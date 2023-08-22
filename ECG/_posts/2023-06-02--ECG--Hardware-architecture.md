---
title: "ECG : hardware architecture"
excerpt: "QRS complex detection device  using Pan Tompkins Algorithm"
categories:
  - ECG
---
<br>

<br>

### ECG Development Board

<img width="750" alt="6" src="https://github.com/sehun98/TIL/assets/100746863/9d03c52f-1e1d-4fd0-9603-ea890a5237de">

### About Project

소프트웨어 필터 적용

Right Leg Driver 오른다리 구동회로 Instrument Circuit

0.05Hz ~ 100Hz Band Pass Filter

2.5V Offset Circuit

AV = 2 Amplifier circuit

5V to 3V3 Level Shifter



### Objective

Pan Tompkins Algorithm를 사용해 QRS complex 감지하는 기기 제작



### Specification

The Atmel AVR 8-bit Microcontrollers ATmega128

Instrument Circuit

Analog Filter

Amplifier circuit

Offset circuit

TFT_SZH-EK096 (TFT LCD)

SN74LVC245A (5V to 3V3 Level Shifter)



### Schematics

<img width="750" alt="1" src="https://github.com/sehun98/TIL/assets/100746863/c3de4b1f-9eaf-490f-9b27-28165e7b898f">
<img width="750" alt="2" src="https://github.com/sehun98/TIL/assets/100746863/b2d02c71-876f-4dfd-81a3-cd2a8b01466c">
<img width="750" alt="3" src="https://github.com/sehun98/TIL/assets/100746863/39cf1bd0-1c01-4179-8a76-b8677e67a8d1">
<img width="750" alt="4" src="https://github.com/sehun98/TIL/assets/100746863/62802a16-75e9-4ab9-bd23-1ab3af4c2148">



### 부품배치도

<img width="750" alt="5" src="https://github.com/sehun98/TIL/assets/100746863/44ea6056-b8b5-4887-8325-a02eed3d4757">

### PCB Assembly

<img width="750" alt="6" src="https://github.com/sehun98/TIL/assets/100746863/9d03c52f-1e1d-4fd0-9603-ea890a5237de">

### Top Layer

<img width="750" alt="7" src="https://github.com/sehun98/TIL/assets/100746863/9b75d7c6-595c-4ff7-be4f-7e1fd9fe006d">

### Bottom Layer

<img width="750" alt="8" src="https://github.com/sehun98/TIL/assets/100746863/d00193b8-57b9-40b9-b906-f3b32138209a">

PADS를 통해 개발보드 PCB를 제작하였습니다.

<br>

<br>
