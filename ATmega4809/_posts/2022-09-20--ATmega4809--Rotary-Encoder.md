---
title: "ATmega4809 : Rotary Encoder"
excerpt: "Interrupt 호출 방법에 대해 학습합니다."
categories:
  - ATmega4809
---
<br>

<br>

```
#define F_CPU 5000000UL
#include <avr/io.h>
#include <avr/interrupt.h>

#define		RotSW_Key		PIN1_bm
#define		RotSW_S1		PIN2_bm
#define		RotSW_S2		PIN3_bm

#define		ROT_BUTTON		(PORTE.IN & RotSW_Key)

void CLK_Init(void);
void GPIO_Init(void);
void TCB0_Init(void);

void SEG_Init(void);
void segSignedDisplay(int16_t);

void segAntiGhostISR(uint16_t);

void ROT_Init(void);

uint8_t GetRotSwitch(void);
void ScanRotSwitchISR(void);
void ScanRotSwISR(void);

uint8_t segDigit[4] = {0xff,0xff,0xff,0xff};
uint8_t segLUT[] = {0x3f,0x06,0x5b,0x4f,0x66,
					0x6d,0x7d,0x27,0x7f,0x67,
					0x77,0x7c,0x39,0x5e,0x79,
					0x71,0x40};

typedef enum { ROT_IDLE, ROT_PRESSING, ROT_PRESSED, ROT_RELEASE } RotSwState_t;
typedef enum { S00, S01, S10, S11 } RotState_t;

uint16_t buttonCount = 0;

int main(void)
{
	CLK_Init();
	GPIO_Init();
	TCB0_Init();
	
	SEG_Init();
	ROT_Init();
	
	sei();
	
    while (1) 
    {
		segSignedDisplay(buttonCount);
    }
}

void CLK_Init(void)
{
	CCP = CCP_IOREG_gc;
	CLKCTRL.MCLKCTRLB = CLKCTRL_PDIV_4X_gc | CLKCTRL_ENABLE_bm;
}

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

void SEG_Init(void)
{
	PORTF.DIRSET = PIN0_bm | PIN1_bm | PIN2_bm | PIN3_bm;
	PORTC.DIR = 0xff;
}

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

ISR(TCB0_INT_vect)
{
	static uint16_t Cnt1000Hz = 0;
	Cnt1000Hz++;
	uint8_t Cnt200Hz = (uint8_t)(Cnt1000Hz % 5);
	uint8_t Cnt1Hz = (uint8_t)(Cnt1000Hz % 1000);
	
	if(Cnt1Hz == 0);
	if(Cnt200Hz == 0) segAntiGhostISR(Cnt1000Hz);	
	if(Cnt200Hz == 2) ScanRotSwitchISR();
	if(Cnt200Hz == 3) ScanRotSwISR();
	
	TCB0.INTFLAGS |= TCB_CAPT_bm;
}

void segAntiGhostISR(uint16_t Cnt1000Hz)
{
	uint8_t index = (uint8_t)(Cnt1000Hz & 0x03);
	
	PORTF.OUTCLR = PIN0_bm | PIN1_bm | PIN2_bm | PIN3_bm;
	PORTC.OUT = segDigit[index];
	PORTF.OUTSET = 1 << index;
}


void ROT_Init(void)
{
	PORTE.DIRCLR = RotSW_S1 | RotSW_S2 | RotSW_Key;
}

uint8_t GetRotSwitch( void )
{
	return (~PORTE.IN & ( RotSW_S1 | RotSW_S2 )) >> 2;
}

void ScanRotSwitchISR( void )
{
	static RotState_t RotState = S00;
	static int8_t	RotCount = 0;
	
	switch ( RotState )
	{
		case S00 :
		if ( RotCount ) {
			if ( RotCount == 4 )	{ buttonCount--; }
			if ( RotCount == -4 )	{ buttonCount++; }
			RotCount = 0;
		}
		if ( GetRotSwitch() == 0b10 ) { RotState = S10;  RotCount++; }
		if ( GetRotSwitch() == 0b01 ) { RotState = S01;  RotCount--; }
		break;
		case S01 :
		if ( GetRotSwitch() == 0b00 ) { RotState = S00;  RotCount++; }
		if ( GetRotSwitch() == 0b11 ) { RotState = S11;  RotCount--; }
		break;
		case S10 :
		if ( GetRotSwitch() == 0b11 ) { RotState = S11;  RotCount++; }
		if ( GetRotSwitch() == 0b00 ) { RotState = S00;  RotCount--; }
		break;
		case S11 :
		if ( GetRotSwitch() == 0b01 ) { RotState = S01;  RotCount++; }
		if ( GetRotSwitch() == 0b10 ) { RotState = S10;  RotCount--; }
		break;
		default:
		RotState = S00;
		break;
	}
}

void ScanRotSwISR( void )
{
	static RotSwState_t RotSwState = ROT_IDLE;
	
	switch ( RotSwState )
	{
		case ROT_IDLE :
		if ( !ROT_BUTTON )  RotSwState = ROT_PRESSING;
		break;
		case ROT_PRESSING :
		if ( ROT_BUTTON ) RotSwState = ROT_IDLE;
		else
		{
			RotSwState = ROT_PRESSED;
		}
		break;
		case ROT_PRESSED :
		if ( ROT_BUTTON ) RotSwState = ROT_RELEASE;
		break;
		case ROT_RELEASE :
		RotSwState = ( ROT_BUTTON )? ROT_IDLE : ROT_PRESSED;
		break;
	}
}
```





<br>

<br>
