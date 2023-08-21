---
title: "ATmega4809 : Clock IC"
excerpt: "Interrupt 호출 방법에 대해 학습합니다."
categories:
  - ATmega4809
---
<br>

<br>

Interrupt를 사용하기 위해서는

Timer/Counter Type B Block Diagram에 대해서 완벽하게 알아볼 필요가 있습니다.



## 용어 정리

TCB : Timer/Counter Type B

CCMP : Counter Compare/Capture

CTRLA : Control A

CAPT : Capture

sei : set interrupt

cli : clear interrupt

<br>

## 예제 코드

```
#define		F_CPU	3333333UL

#include <avr/io.h>
#include <avr/interrupt.h>
#include <inttypes.h>

typedef enum {KEY_IDLE, KEY_PRESSING, KEY_PRESSED, KEY_RELEASE}KeyState_t;

#define USER_LED	PIN5_bm

#define USER_LED_ON		(PORTF.OUTCLR = PIN5_bm)
#define USER_LED_OFF	(PORTF.OUTSET = PIN5_bm)
#define USER_LED_TOGGLE (PORTF.OUTTGL = PIN5_bm)

#define USER_BUTTON (PORTF.IN & PIN6_bm)

void interrupt_init();
void pin_init();
void buttonISR();

/*
 * brief : 100Hz 마다 interrupt가 발생하여 USER_BUTTON 의 상태를 확인하고 오토마타에 의한 알고리즘 구성으로 채터링 현상을 제거하는 알고리즘
 * note : interrupt 사용 시 Race Condition, Critical Section, Atomic Operation 에 대해 고려해야 합니다.
 */
ISR(TCB0_INT_vect)
{
	buttonISR();
	
	TCB0.INTFLAGS |= TCB_CAPT_bm;
}

int main()
{
	/* PF5 output mode, PF6 input mode initialization */
	pin_init();
	
	/* TCB0 100Hz interrupt initialization */
	interrupt_init();
	
	while(1)
	{
		
	}
}

void interrupt_init()
{
	TCB0_CCMP = 33333; // 20,000,000Hz / 6분주비(default) = 3,333,333Hz 에서 100Hz의 주기를 얻기 위해서는 3,333,333Hz * x = 100Hz 로 333333이 추출됩니다.
	TCB0_CTRLA |= TCB_ENABLE_bm;
	TCB0_INTCTRL |= TCB_CAPT_bm;
	
	sei();
}

void pin_init()
{
    PORTF.DIRSET = USER_LED;
    PORTF.OUTSET = USER_LED;
}

void buttonISR()
{
	static KeyState_t KeyState = KEY_IDLE;
	
	switch (KeyState)
	{
		case KEY_IDLE :
			if(!USER_BUTTON) KeyState = KEY_PRESSING;
			break;
		case KEY_PRESSING :
			if(USER_BUTTON) KeyState = KEY_IDLE;
			else
			{
				KeyState = KEY_PRESSED;
				USER_LED_TOGGLE;
			}
			break;
		case KEY_PRESSED :
			if(USER_BUTTON) KeyState = KEY_RELEASE;
			break;
		case KEY_RELEASE :
			KeyState = (USER_BUTTON)? KEY_IDLE : KEY_PRESSED;
			break;
	}
}
```





<br>

<br>
