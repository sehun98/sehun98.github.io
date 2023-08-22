---
title: "ECG : Software architecture"
excerpt: "Pan Tompkins Algorithm이 무엇인지 확인하고 소프트웨어 구현을 합니다."
categories:
  - ECG
---
<br>

<br>

QRS complex는 QRS 복합체는 심전도에서 관찰되는 파형 중 하나로 앞선 인체생리학에서 자세하게 다루고 있습니다.

심부전, 심근경색, 심장비대 등과 같은 심장 문제를 감지하고 진단에 사용되고 산소포화도 SPO2를 같이 사용하면 각종 질병들을 감지할 수 있습니다.

현재 심전도를 사용하여 심장질환 예측 및 당뇨병과 같은 다른 질병을 측정하는 연구가 진행되고 있습니다. 이러한 연구는 의료 분야에서 진단 및 예방의 정확성을 향상시키는 데 기여할 수 있습니다.



### Pan Tompkins Algorithm

Pan Tompkins 알고리즘은 QRS complex를 감지하는 데 사용되는 심전도 신호 처리 기술 중 하나입니다. 

Pan-Tompkins 알고리즘은 자동화된 심전도 분석에서 매우 효과적으로 사용되며, QRS 복합체의 정확한 감지와 분석을 통해 심박수 측정, 부정맥 탐지, 심장 이상 등을 판별하는 데 도움을 줍니다. 



<img width="750" alt="13" src="https://github.com/sehun98/TIL/assets/100746863/1377a3a3-49e0-4b42-8cd5-e40e96f56791">

```c
/*
 * #키워드
 * #ADC #Low Pass Filter #Differential #Square #Moving Average Filter
 * 
 * Pan Tompkins Algorithm
 * 
 * R-R interval을 측정하기 위해 Raw Signal을 가공해야 합니다.
 * 일반적으로 Pan-Tompkins 알고리즘은 자동화된 심전도 분석에서 매우 효과적으로 사용되며, QRS 복합체의 정확한 감지와 분석을 통해 심박수 측정, 부정맥 탐지, 심장 이상 등을 판별하는 데 도움을 줍니다. 
 *
 * 심전도는 분당 80~120bpm으로 비교적 낮은 속도입니다.
 * 샘플링 레이트는 Nyquist Frequency에 의해 2배 이상인 1041Hz으로 결정하였습니다.
 * 이로서 raw signal의 왜곡은 없으나 많은 노이즈가 문제가 되는 상황입니다.
 * 알고리즘을 구성함에 있어 데이터 타입이 가장 큰 역할을 합니다.
 * 잘못된 데이터 타입에 데이터를 넣으면 전혀 다른 데이터가 되어버립니다. 너무 작은 데이터 타입을 사용하면 오버플로우가 발생하고 너무 큰 데이터 타입을 사용하면 불필요한 저장공간을 사용하게 됩니다.
 * 또한 unsigned와 signed를 잘 활용해야 합니다.
 *
 * 기본적인 Pan Tompkins Algorithm의 순서는 다음과 같습니다.
 * Raw ECG Signal -> Low Pass Filter
 * Low Pass Filter -> Differential
 * Differential -> Square
 * Square -> Moving Average Filter
 * Moving Average Filter -> R-R interval
 *
 *
 */

#define F_CPU 16000000UL

#include <avr/io.h>
#include <avr/interrupt.h>
#include <stdio.h>
#include <stdbool.h>
#include <inttypes.h>
#include <util/delay.h>

#include "uart.h"

#define MOVING_AVERAGE_SIZE 			8
#define MOVING_AVERAGE_MASK 			(MOVING_AVERAGE_SIZE - 1)

#define ADC_VREF_TYPE 					0x40
#define THRESHOLD 						2000000

volatile bool ECG_Flag = false;

/*
 * ecg와 moving average 구조체를 사용하여 종합 관리를 진행합니다.
 */
typedef struct ecg_t
{
	uint16_t 	raw_data;
	uint16_t 	lowPassFiltered_data;
	int16_t 	differented_data;
	uint32_t 	squared_data;
	uint32_t 	moving_average_filtered_data;
	uint16_t 	bpm;
};

typedef struct moving_average_t 
{
	uint16_t 	index;
	uint32_t 	sum;
	uint32_t 	buffer[MOVING_AVERAGE_SIZE];
};

/*
 * ecg와 moving average 구조체의 데이터 공간 할당을 진행합니다.
 */
struct ecg_t ecg = { 0, 0, 0, 0, 0, 0 };
struct moving_average_t moving_average = { 0, 0, {0} };

void 		Timer_Init(void);
void 		ADC_Init(void);
uint16_t 	read_adc(unsigned char adc_input);

uint16_t 	lowPass_filter(uint16_t raw_data);
int16_t 	differentiator(uint16_t lowPassFiltered_data);
uint32_t 	moving_average_filter(uint32_t squared_data);
uint16_t 	peak_detection(uint32_t filtered_data);

int main(void)
{
	stdout = &mydata;
	
	Timer_Init();
	ADC_Init();
	UART_Init(0,115200);
	
	sei();

	while (1)
	{
		if(ECG_Flag)
		{
			ecg.raw_data = read_adc(0);
			ecg.lowPassFiltered_data = lowPass_filter(ecg.raw_data);
			ecg.differented_data = differentiator(ecg.lowPassFiltered_data);
			ecg.squared_data = (uint32_t) ecg.differented_data * (uint32_t) ecg.differented_data;
			ecg.moving_average_filtered_data = moving_average_filter(ecg.squared_data);
			ecg.bpm = peak_detection(ecg.moving_average_filtered_data);
			UART_Printf(0, "%d %d\n\r", ecg.lowPassFiltered_data, ecg.bpm);
			ECG_Flag = false;
		}
	}
}

/* 
 * ECG 데이터는 일반적으로 고주파 성분이 매우 낮기 때문에 샘플링 레이트가 매우 높을 필요는 없을 수 있습니다. 
 * 샘플링 레이트는 504Hz로도 충분합니다. 하지만 샘플링 레리트를 건들이지 않고 사용하는 방법을 찾아보는 연습을 할 것 입니다.
 * 그 방법으로는 다음과 같습니다.
 * 1. 데이터 압축: ECG 데이터는 주로 저주파 성분을 포함하므로, 데이터를 효과적으로 압축하여 UART 통신의 데이터 전송률을 낮출 수 있습니다. 
 * 2. 다운 샘플링: ECG 신호의 고주파 성분은 매우 낮기 때문에, 샘플링 레이트를 낮추는 것이 가능합니다. 
 * 3. 데이터 프레임화: ECG 데이터를 작은 블록으로 나누어 전송하는 것을 고려해 볼 수 있습니다. 
 * 4. FIFO 버퍼 사용: UART 통신을 위한 FIFO (First-In-First-Out) 버퍼를 사용하여 데이터를 임시로 저장하고, 효율적으로 전송할 수 있습니다.
 * 5. 데이터 효율화: ECG 데이터 중 불필요한 부분을 필터링하거나 축소하여 전송하는 방법도 고려해 볼 수 있습니다. 
 * 6. 고급 통신 프로토콜 사용: UART 대신 더 빠른 전송 속도를 지원하는 고급 통신 프로토콜(예: USB, Bluetooth 등)을 사용하는 것도 고려할 수 있습니다.
 */

//16000000Hz/1024/31 = 504Hz, (256-225) = 31
//16000000Hz/1024/15 = 1041Hz, (256-241) = 15
ISR(TIMER0_OVF_vect)
{
	ECG_Flag = true;
	TCNT0 = 241;
}

/*
 * 16000000Hz/1024 스케일을 기본값으로 설정합니다.
 */
void Timer_Init(void)
{
	TIMSK = 0x01;    // TOIE0 = 1;
	TCCR0 = 0x07;    // 일반모드, 프리스케일 = CK/1024
	TCNT0 = 241;    // 타이머/카운터0 레지스터 초기값
}

void ADC_Init(void)
{
	ADMUX = ADC_VREF_TYPE & 0xff;
	ADCSRA = 0x84;
}

uint16_t read_adc(unsigned char adc_input)
{
	ADMUX = adc_input | (ADC_VREF_TYPE & 0xff);
	_delay_us(10);
	ADCSRA |= 0x40;
	while ((ADCSRA & 0x10) == 0);
	ADCSRA |= 0x10;
	return ADCW;
}

/*
 * 과거 데이터에 90%의 비중을 주고 현재 데이터에 10%의 비중을 준 Low Pass filter입니다.
 */
uint16_t lowPass_filter(uint16_t raw_data)
{
	static float filtered_data = 0.0f; // 이전에 필터링된 데이터를 저장하기 위한 변수
	float alpha = 0.1f; // 필터링 상수 (조절 가능)
	
	filtered_data = (1.0 - alpha) * (float) filtered_data + alpha * (float) raw_data; // 필터링 적용
	
	return (uint16_t) filtered_data;
}

/*
 * delta = 1 / 1024 = 0.0009765625
 */
int16_t differentiator(uint16_t lowPass_filtered_data)
{
	static uint16_t prev_data = 0;
	float delta = 1.0 / 1024.0;

	float slope = ((float)lowPass_filtered_data - (float)prev_data) / delta;
	prev_data = lowPass_filtered_data;

	return (int16_t) slope;
}

/*
 * 저장을 해둔 sum에 이전의 데이터값을 빼주고
 * sum에 새로운 데이터를 더해줍니다.
 * 새로운 데이터를 더해줬으므로 buffer에 저장합니다.
 * index를 증가하여 컨트롤할 데이터를 변경해줍니다.
 * 조건문을 통해 index의 위치를 확인하는 것은 많은 instruct가 발생하므로 비트를 통한 관리를 진행합니다.
 * 마지막으로 average를 하기 위한 SIZE를 sum에서 나눠주기만 하면 됩니다.
 */
uint32_t moving_average_filter(uint32_t squared_data)
{
	moving_average.sum -= moving_average.buffer[moving_average.index];
	moving_average.sum += squared_data;
	moving_average.buffer[moving_average.index] = squared_data;
	moving_average.index++;
	
	//if(moving_average.index >= MOVING_AVERAGE_SIZE) moving_average.index =0;
	moving_average.index = moving_average.index & MOVING_AVERAGE_MASK;

	return moving_average.sum / MOVING_AVERAGE_SIZE;
}

/*
 * R-R interval 함수
 * THRESHOLD가 static으로 정해져 있으므로 움직임에 의한 half cell potential에 대응하지 못합니다.
 * 따라서 Thereshold 또한 이동 평균을 통한 동적으로 변경을 하거나
 * 칼만 필터 등의 여러가지 방법을 고안해야 합니다.
 */
uint16_t peak_detection(uint32_t moving_average_filtered_data)
{
	static uint16_t sampling_rate = 1041;
	static uint16_t heart_rate = 0;
	static uint16_t rr_interval = 0;
	static uint16_t delay = 0;
    
	if(moving_average_filtered_data > THRESHOLD && delay > 208) // 1041Hz 0.960ms 208개
	{ // 200ms 환산할것!!!! thereshold 설정할 것!!!
		heart_rate = 60 * sampling_rate / rr_interval; // 60 * 180 / 160 = 67.5 bpm
		delay = 0;
		rr_interval = 0;
	}
	else
	{
		delay++;
		rr_interval++;
	}
	return heart_rate;
}
```







#### Low Pass Filtered

<img width="750" alt="9" src="https://github.com/sehun98/TIL/assets/100746863/33a68ac4-f6d3-48ad-9d76-bd90a0889537">





#### Pan Tompkins Algorithm

<img width="750" alt="10" src="https://github.com/sehun98/TIL/assets/100746863/4e137b3a-4c39-4d18-b9e2-039b47725d8d">



### LabView

https://github.com/sehun98/TIL/assets/100746863/9cb88d07-1455-4288-817e-806c017344cb



<img width="750" alt="11" src="https://github.com/sehun98/TIL/assets/100746863/04bc083c-50f6-4b35-8041-4efd1f6f7cab">

<img width="750" alt="12" src="https://github.com/sehun98/TIL/assets/100746863/aee98a5c-1426-4af4-b905-c13705d38190">

<br>

<br>
