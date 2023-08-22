---
title: "ATmega4809 : 7 Segment"
excerpt: "Interrupt 호출 방법에 대해 학습합니다."
categories:
  - ATmega4809
---
<br>

<br>

```c
/* 
  * #키워드
  * #7SEGMENT #크리트컬 섹션 #Anti Ghost
  *
  * 3장 7SEG와 크리티컬 섹션을 방지하는 방법
  * 
  * 지난 2장에서 버튼의 여러가지 동작 구현 방법을 알아보았다.
  * 이번 3장에서는 7 SEGMENT를 동작시키는 방법에 대해 알아보자.
  * 
  * 우선 7 SEGMENT를 설정하기 위한 클럭과 인터럽트 설정은 다시 설명하지 않겠다.
  * 기억이 나지 않는다면 1장을 다시 보고 오길 바란다.
  * GPIO에서 버튼 구현을 위해 설정을 조금 바꿨으니 GPIO_Init()을 보고 오자.
  * 
  * callback) GPIO_Init()을 보자.
  * 
  * SEGMENT를 동작시키기 위해서는 우선 Initialization 을 진행해야한다.
  * 이때 하드웨어적으로 다알링톤에 의해 세그먼트의 동작을 유추하는 방법을 알아야한다. (Common Emitter Amp 를 생각해보자)
  * 회로도를 보면 다알링톤에 의해 신호가 뒤집어진다는 사실을 생각하며 다음을 이해해보자.
  *
  * PORTF에 output 을 다알링톤과 연결을 시켜 HIGH 신호를 주게 될 경우 LOW 신호가 LED에 들어가게 된다.
  * 반대편에는 PORTC에 HIGH 신호를 주게 될 경우 PORTF의 LOW와 PORTC의 HIGH에 전압차가 발생하여 LED가 켜지게 된다.
  * 이해가 안된다면 될때까지 이해해봐라.
  * 
  * 이러한 세그먼트의 동작을 암기하고 언제 PORTF에 HIGH/LOW 신호를 줘야하는지 PORTC에 HIGH/LOW 신호를 줘야하는지 정확하게 파악해야한다.
  * 세그먼트를 사용할 경우 디버그 할때 파악할 줄 알아야 한다. 
  *
  * 세그먼트가 모두 안켜질 경우 (Anti Ghost 나 PORT 설정을 잘못했을 가능성 존재)
  * 일부만 안켜질 경우 (Anti Ghost 나 PORT 설정을 잘못했을 가능성 존재)
  * 데이터값이 이상하게 나올 경우 (data value 의 타입이 이상해서 or segBuffer에 넣을 때 다른 값을 넣었을 떄 따라서 break point 를 segDigit에 걸어서 올바른 정보가 들어오는지 확인한다)
  * Reading Zero Kill 이 이상하게 나올 경우 (Reading Zero Kill에서 i값을 잘못 설정했거나 else break;를 안걸어줬을 때) 
  * 이상이 없는거 같은데 LED 하나 동작 안할 경우 (납땜문제나 LED가 과전류에 의해 고장났을 경우가 있다. 보통은 코드문제 때문에 발생하는 것이니 당황하지 말고 코드나 다시 고쳐봐라.)
  * 그 밖에 데이터 처리가 잘못 된 경우 (data 연산 과정의 오류)
  * 
  * 위의 오류들은 SEG를 모두 학습하고 난 후 직접 오류를 발생시켜보면서 어느 부분이 잘못되면 오류가 발생하는지 기록해서 암기해두는 것이 좋다.
  *
  * 본론으로 돌아가 Initialization 을 진행해야한다.
  * 
  * callback) SEG_Init()을 보자.
  */ 

#define F_CPU 5000000UL
#include <avr/io.h>
#include <avr/interrupt.h>

void CLK_Init(void);
void GPIO_Init(void);
void TCB0_Init(void);
void SEG_Init(void);
void segSignedDisplay(int16_t);

void segAntiGhostISR(uint16_t);

/*
 * 데이터를 넣어두는 Look Up Table 과 Digit 부분이다. 데이터 값이 정상적으로 저장되어 있는지 확인해줘야 한다.
 */
uint8_t segDigit[4] = {0xff,0xff,0xff,0xff};
uint8_t segLUT[] = {0x3f,0x06,0x5b,0x4f,0x66,
					0x6d,0x7d,0x27,0x7f,0x67,
					0x77,0x7c,0x39,0x5e,0x79,
					0x71,0x40};

int main(void)
{
	CLK_Init();
	GPIO_Init();
	TCB0_Init();
	SEG_Init();
	
	sei();
	
    while (1) 
    {
		/*
		 * segSignedDisplay()함수를 만들지 않고 먼저 써넣은 이유는 세그먼트를 언제 부르는지 파악하면 코드를 작성하기 용이하기 때문에 이 순서로 학습을 했다.
		 * 다른 통신 같은 코드를 작성할 때에는 우선 통신 protocol 을 뚫고 interface 와 application 을 작성한다.
		 * 
		 * 세그먼트를 파악하기 위해 제일 먼저
		 * segSignedDisplay(-103);를 사용한다.
		 * 이때 -103을 사용한 이유는 -의 경우와 가운데 0 에서 코드 오류가 발생할 경우의 수가 많기 때문에 -103을 통해 빠르게 디버깅을 할 수 있게 된다.
		 * 예를들어 -1과 3만 나오게 된다면 reading zero kill 이 잘못 설정되어 0을 없애버린 것이고
		 * -의 값이 안나오거나 전혀다른 숫자가 나올 경우 data type이 잘못 되어있거나 (int16_t를 사용해야 하는데 uint16_t를 사용하는 경우) segBuffer[0] == 0x3f가 잘못 되어있을 경우가 많다.
		 * 따라서 -103을 테스트로 사용하는 것이다.
		 * 
		 * segSignedDisplay 를 설정을 했다면 segSignedDisplay() 를 작성해 보자.
		 * 
		 * callback) segSignedDisplay()을 보자.
		 */
		segSignedDisplay(-103);
    }
}

void CLK_Init(void)
{
	CCP = CCP_IOREG_gc;
	CLKCTRL.MCLKCTRLB = CLKCTRL_PDIV_4X_gc | CLKCTRL_ENABLE_bm;
}

/* 
 * PORTF의 6번 핀에 버튼이 존재하기 떄문에 이를 내부 pull up 으로 사용하기 위해 다음과 같이 설정을 진행하였다.
 * Direction 설정은 이해하기 쉬울것이다.
 *
 * PORTF.PIN6CTRL |= PORT_PULLUPEN_bm;
 * 내부에서 pull up 설정을 해줌으로 노이즈에 대비를 한다.
 *
 * callback) return 맨 처음으로 되돌아간다.
 */
void GPIO_Init(void)
{
	PORTF.DIRSET = PIN5_bm;
	PORTF.DIRCLR = PIN6_bm;
	PORTF.OUTSET = PIN5_bm;
	PORTF.PIN6CTRL |= PORT_PULLUPEN_bm;
}

void TCB0_Init(void)
{
	TCB0.CCMP = 5000;
	TCB0.CTRLA |= TCB_ENABLE_bm;
	TCB0.INTCTRL |= TCB_CAPT_bm;
}

/*
 * 앞서 설명한 것 처럼 어느 핀에 다알링톤 회로가 연결 되었는지 생각을 하면서 코드를 작성해야 할 것이다.
 * PORTF.DIRSET = PIN0_bm | PIN1_bm | PIN2_bm | PIN3_bm;
 * PORTC.DIR = 0xff;
 *
 * 설정이 완료가 되었다면 main()의 while(1)로 들어가 segSignedDisplay(data);를 만들어준다.
 *
 * callback) main()의 while(1)로 들어가 segSignedDisplay(data);
 */
void SEG_Init(void)
{
	PORTF.DIRSET = PIN0_bm | PIN1_bm | PIN2_bm | PIN3_bm;
	PORTC.DIR = 0xff;
}

/*
 * segBuffer[]에 담아 두었다가 한번에 segDigit[]에 넣어서 정보를 전달해줘야한다.
 * 이는 인터럽트에서 발생하는 크리티컬 섹션 때문인데
 * 크리티컬 섹션이란 인터럽트 자원을 main 자원과 공유되었을 때 주로 발생하며
 * CURD 상황에서 발생한다.
 * CURD란 Create Update Read Delete 로 Web 개발자들이 자주 사용하는 용어이다.
 * 
 * 많은 임베디드 개발자들은 크리티컬 섹션을 디버깅 할줄 몰라서 폴링 방식으로 작성을 한다.
 * 이런 개 쓰래기같은 코드는 작성하지 말아야한다.
 * 크리티컬 섹션은 논리적으로 모두 맞는데 발생하는 경우로 아주 골때리는 현상이라고 한다.
 * 이를 디버깅 하기 위해서는 내가 main 에서 사용하는 자원과 interrupt 에서 사용하는 자원을 구분에서 정리를 해보고
 * 크리티컬 섹선이 발생하는 경우가 생길 위험이 있는 자원부터 확인을 해본다.
 * 원인이 된 자원을 찾는게 제일 문제가 크지만
 * 찾았다면 50% 해결한 것과 마찬가지이다.
 * 이 자원에서 main 에서 instruction 이 몇번걸리고 interrupt 에서 몇번 걸리는지 확인을 하여
 * instruction 을 줄이는 방법을 찾아야한다.
 * 몇번의 instruction 이 발생하는지 확인 하려면 lss 리스팅 파일을 확인하는 수 밖에 없다.
 * instruction 을 줄이기 위해 7 segment 에서는 마지막에 segBuffer[]에 담아 두었다가 한번에 segDigit[]에 넣어서 정보를 전달해주는 방식을 채택했다.
 *
 * data 연산과정과 reading zero kill 과 data setting 3단계가 존재한다.
 * data 가 -999, 0, 999 를 기준으로 data 에 어떤 값이 들어가야 하는지 연산을 진행한다.
 * 만약 첫째 자리수가 아닌 다른 자리에서 차례대로 0이 왔을 때를 확인해서 제거해준다.
 * 꼭 else break;를 해줘야한다. 없애고 확인해보자.
 * 
 * 크리티컬 섹션을 없애기 위해 마지막에 데이터를 넣어주는 과정을 한다. 만약 데이터 값이 이상할 경우 여기에 break point를 걸어 segDigit[]에 알맞은 데이터가 들어가는지 확인한다.
 * 
 * 데이터를 넣어주는 과정을 마쳤다. 넣어준 데이터를 Display 하기 위해 Anti Ghost 를 진행하자.
 *
 * callback) ISR(TCB0_INT_vect)
 */
void segSignedDisplay(int16_t data)
{
	uint8_t segBuffer[4];
	
	// segBuffer[0] 및 data 연산
	if(data < -999) { segBuffer[0] = segLUT[16]; data = 999; }
	else if(data >= -999 && data < 0) { segBuffer[0] = segLUT[16]; data = -data; }
	else if(data >= 0 && data <= 999) { segBuffer[0] = 0; }
	else { segBuffer[0] = 0; data = 999; }
		
	segBuffer[1] = segLUT[data/100];
	segBuffer[2] = segLUT[(data%100)/10];
	segBuffer[3] = segLUT[data%10];
	
	// reading zero kill
	for(uint8_t i = 1; i < 3; i++)
	{
		if(segBuffer[i] == 0x3f) segBuffer[i] = 0;
		else break;
	}
	
	// setting data
	for(uint8_t i = 0; i < 4; i++)
		segDigit[i] = segBuffer[i];
}

/*
 * 우리 눈은 60Hz 이상의 주파수를 볼 수 없이 때문에 5ms를 기준으로 AntiGhost를 진행한다.
 * 
 * Anti Ghost를 진행하지 않을 경우 Ghost 현상이 보이게 된다.
 * segAntiGhostISR(Cnt1000Hz)를 만들어주자.
 *
 * callback) segAntiGhostISR(Cnt1000Hz)
 */
ISR(TCB0_INT_vect)
{
	static uint16_t Cnt1000Hz = 0;
	Cnt1000Hz++;
	uint8_t Cnt200Hz = (uint8_t)(Cnt1000Hz % 5);
	uint8_t Cnt1Hz = (uint8_t)(Cnt1000Hz % 1000);
	
	if(Cnt1Hz == 0);
	if(Cnt200Hz == 0) segAntiGhostISR(Cnt1000Hz);	
	
	TCB0.INTFLAGS |= TCB_CAPT_bm;
}

/*
 * 맨 처음에 세그먼트를 켜고 끄는 동작을 암기하라고 했다.
 * 이를 바탕으로 세그먼트의 동작을 제어해주게된다.
 * 
 * uint8_t index = (uint8_t)(Cnt1000Hz & 0x03);
 * & 기호는 이렇게 생각함녀 된다. A에 있는 B 비트를 처다봐라. (A & B)
 * 즉 0bxxxxxx00을 쳐다보게 되고 그 숫자는 00, 01, 10, 11 4개가 되어 segDigit[] 의 자리수임을 확인 할 수 있다.
 * 
 * PORTF.OUTCLR = PIN0_bm | PIN1_bm | PIN2_bm | PIN3_bm;
 * 세그먼트를 모두 꺼준다.
 * PORTC.OUT = segDigit[index];
 * 꺼준 상태에서 데이터를 넣어주고 LEF를 순서대로 00 > 01 > 10 > 11 을 켜주게 되면 Ghost 현상이 사라진다.
 * PORTF.OUTSET = 1 << index;
 *
 * 모든 코드를 작성했다. 이제 세그먼트의 동작을 확인하고 임의로 오류를 발생시켜 디버그를 진행해보자.
 */
void segAntiGhostISR(uint16_t Cnt1000Hz)
{
	uint8_t index = (uint8_t)(Cnt1000Hz & 0x03);
	
	PORTF.OUTCLR = PIN0_bm | PIN1_bm | PIN2_bm | PIN3_bm;
	PORTC.OUT = segDigit[index];
	PORTF.OUTSET = 1 << index;
}
```

<br>

<br>
