---
title: "ATmega4809 : GPIO Button"
excerpt: "General Purpose Input Output 제어 방법에 대해 학습합니다."
categories:
  - ATmega4809
---
<br>

<br>

GPIO를 사용하기 위해서는

PORT Block Diagram에 대해서 완벽하게 알아볼 필요가 있습니다.



따라서 GPIO를 설정하기 위해서는 다음과 같은 순서를 지켜야합니다.

1. PORTx의 방향을 설정합니다.
   출력 포트 설정 : PORTx.DIRSET = PINx_bm;
   입력 포트 설정 : PORTx.DIRCLR = PINx_bm;
2.  회로도를 확인하여 PULL-UP/DOWN을 확인하여 초기화 상태를 인지합니다.
3. PORTx를 사용합니다.
   출력 포트 사용 : PORTx.OUTSET = PINx_bm;
   입력 포트 사용 : ( PORTx.IN & PINx_bm )

## 예제 코드

스위치(PF6)를 누르면 LED(PF5)가 켜지는 간단한 코드 

```c
#include <avr/io.h>

#define 	USER_LED 	PIN5_bm
#define 	USER_BUTTON 	PIN6_bm

#define 	USER_LED_ON 	(PORTF.OUTCLR = USER_LED)
#define 	USER_LED_OFF 	(PORTF.OUTSET = USER_LED)

typedef enum {false, true} bool;

void pin_init();

int main()
{
	/* PF5 output mode, PF6 input mode initialization */
	pin_init();
	
	while(1)
	{
		!( PORTF.IN & USER_BUTTON ) ? USER_LED_ON : USER_LED_OFF;
	}
}

void pin_init()
{
	PORTF.DIR &= USER_LED; 		// 0b00000000 & 0b00100000
	PORTF.DIR |= ~USER_BUTTON; 	// 0b00000000 | 0b10111111
	PORTF.OUTSET = USER_LED; 	// PULL-UP 저항이 달려있기 때문에 High(3.3V)일 때 꺼진 상태
}

void pin_init2()
{
    PORTF.DIRSET = USER_LED;
    PORTF.DIRCLR = USER_BUTTON;
    PORTF.OUTSET = USER_LED;
}
```



<br>

<br>