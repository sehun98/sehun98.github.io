---
title: "ATmega4809 : Install"
excerpt: "Atmel Studio 7.0 다운로드"
categories:
  - ATmega4809
---
<br>

<br>

## ATmega Install

Atmega4809를 사용하기 위해 무료 IDE를 설치해줍니다.

<a href="https://www.microchip.com/en-us/tools-resources/develop/microchip-studio#Downloads">Atmel Studio 7.0 다운로드 홈페이지</a>

<img width="100%" alt="2" src="https://user-images.githubusercontent.com/100746863/190173401-c03f11bb-518e-40b3-ad9a-8a373bbe7ad0.PNG">
<img width="50%" alt="3" src="https://user-images.githubusercontent.com/100746863/190173409-6dd5d0ff-b4e4-43b5-87e9-ec7234c45198.PNG">

아키텍처를 선택하지 않은 경우 추가 / 복구 하여렴 installer를 다시 실행하고 'Repair' 를 선택하여 다시 진행합니다.

<img width="50%" alt="4" src="https://user-images.githubusercontent.com/100746863/190173411-125f2a46-5355-40cf-83f4-fab412272140.PNG">
<img width="50%" alt="5" src="https://user-images.githubusercontent.com/100746863/190173412-9ccb764e-d310-4d19-be51-d30976b7e6bd.PNG">
<img width="50%" alt="6" src="https://user-images.githubusercontent.com/100746863/190173415-f52eb8dd-7cad-4cae-87e3-697ff1288d7f.PNG">
<img width="50%" alt="7" src="https://user-images.githubusercontent.com/100746863/190173418-744777d5-29b4-4bc3-ba69-6cbe3d136ef6.PNG">

<br>

## 보드 테스트

간단한 프로그램을 실행해 보드 테스트를 진행합니다.

<img width="100%" alt="8" src="https://user-images.githubusercontent.com/100746863/190174692-51c35344-fe04-4b3b-8b52-ebcfa48ad23e.PNG">
<img width="75%" alt="9" src="https://user-images.githubusercontent.com/100746863/190174702-5be2c005-3ba7-41c0-9d12-e40cbd7e9fe2.PNG">
<img width="100%" alt="10" src="https://user-images.githubusercontent.com/100746863/190174706-5042f3ba-5ce2-4409-adce-6affbeb48ff1.PNG">
<img width="100%" alt="11" src="https://user-images.githubusercontent.com/100746863/190174708-bc537c6f-c1fc-499c-8d19-52206de6c287.PNG">

```c
#include <avr/io.h>
#include <util/delay.h>

#define F_CPU 3333333UL
#define USER_LED PIN5_bm;

int main(void)
{
	PORTF.DIR = USER_LED; // 0x20
    while (1) 
    {
		PORTF.OUT &= ~USER_LED; // ~ 0010 0000 => 1101 1111
		_delay_ms(1000);
		PORTF.OUT |= USER_LED; //  1101 1111 => 1111 1111
		_delay_ms(1000);
    }
}
```

## 링크 연결

보드와 컴퓨터를 연결해줍니다.

<img width="50%" alt="12" src="https://user-images.githubusercontent.com/100746863/190176976-526a3023-7b83-49d0-b511-81d0c2a7ab0c.PNG">
<img width="100%" alt="13" src="https://user-images.githubusercontent.com/100746863/190176980-8d28ea65-890b-491a-85a3-3496458309bd.PNG">

<br>

<br>
