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

//16000000Hz/1024/31 = 504Hz, (256-225) = 31
//16000000Hz/1024/15 = 1041Hz, (256-241) = 15
ISR(TIMER0_OVF_vect)
{
	ECG_Flag = true;
	TCNT0 = 241;
}

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

uint16_t lowPass_filter(uint16_t raw_data)
{
	static float filtered_data = 0.0f; // 이전에 필터링된 데이터를 저장하기 위한 변수
	float alpha = 0.1f; // 필터링 상수 (조절 가능)
	
	filtered_data = (1.0 - alpha) * (float) filtered_data + alpha * (float) raw_data; // 필터링 적용
	
	return (uint16_t) filtered_data;
}

int16_t differentiator(uint16_t lowPass_filtered_data)
{
	static uint16_t prev_data = 0;
	float delta = 0.0009765625f;

	float slope = ((float)lowPass_filtered_data - (float)prev_data) / delta;
	prev_data = lowPass_filtered_data;

	return (int16_t) slope;
}

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

<img width="750" alt="11" src="https://github.com/sehun98/TIL/assets/100746863/04bc083c-50f6-4b35-8041-4efd1f6f7cab">

<img width="750" alt="12" src="https://github.com/sehun98/TIL/assets/100746863/aee98a5c-1426-4af4-b905-c13705d38190">



<br>

<br>
