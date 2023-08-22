---
title: "PADS : FPGA Parts"
excerpt: "FPGA를 만드는 방법을 알아봅니다."
categories:
  - PADS
---

<br>

<br>

### **세부 내용**

FPGA의 경우 회로 설계시 게이트 별로 나눠줘야 한다.

xc7s50-csga324 `pinout`을 검색해 Pinout Files에서 Pin map을 다운받는다.

<img width="750" alt="70" src="https://github.com/sehun98/TIL/assets/100746863/5037eb18-be1d-41c0-a5b7-cd01be401627">

<img width="750" alt="71" src="https://github.com/sehun98/TIL/assets/100746863/b47a7792-2146-4f15-9617-345aef97d8e6">

<img width="750" alt="72" src="https://github.com/sehun98/TIL/assets/100746863/9c075b85-1808-4cf3-9c35-ab078e73914f">

<img width="750" alt="73" src="https://github.com/sehun98/TIL/assets/100746863/e7884f84-4ffe-4b97-8bf1-ed52261e839b">

텍스트 파일을 csv파일로 정리하기

Save As 저장하기

### 

<img width="750" alt="74" src="https://github.com/sehun98/TIL/assets/100746863/85e2403c-9b31-4192-8301-a4cb62bc16a9">

BANK 별로 나누고 전원별로 나누어 줘서 CONFIGURATION에 사용되는 핀들을 좀 더 쉽게 정리 할 수 있으며 전원 관련 핀들도 파악하기 쉬워진다.

<img width="750" alt="75" src="https://github.com/sehun98/TIL/assets/100746863/46c6f2bc-283e-4571-96b7-d90acabaa559">

### FPGA 만들기

PADS Logic > Tools > Part Editor

<img width="300" alt="76" src="https://github.com/sehun98/TIL/assets/100746863/82c9db76-a656-4e22-bfa8-cd54e50126e5">

Edit Electrical > Gate > Add 게이트 추가하기

<img width="80" alt="77" src="https://github.com/sehun98/TIL/assets/100746863/4bc29c49-ec2d-4909-b891-26789c800fc2">

Wizard를 통한 게이트 생성

<img width="750" alt="78" src="https://github.com/sehun98/TIL/assets/100746863/f605f800-3e13-43fa-9d53-ad3c21f8c218">

Edit Electrical > Pins, Attributes 설정하기

<img width="80" alt="79" src="https://github.com/sehun98/TIL/assets/100746863/2c29dbfa-8d8f-4ae0-861b-5fe9c9c51d9c">

PADS Logic > Tools > Parts Editor > Wizard

게이트 하나 만들기

File > Return to Part 후 다시 또 다른 게이트 만들기

<img width="750" alt="80" src="https://github.com/sehun98/TIL/assets/100746863/bc9d21da-1116-451c-af29-df7514839a61">

<img width="500" alt="81" src="https://github.com/sehun98/TIL/assets/100746863/1d46a266-dbec-47ec-8fff-82f9bf88f7f1">
<img width="400" alt="82" src="https://github.com/sehun98/TIL/assets/100746863/f546ba2d-9114-4f57-a7bf-36a6bf56cd36">

FPGA Pins, Attributes 넣어주기

<img width="750" alt="83" src="https://github.com/sehun98/TIL/assets/100746863/aef0e2aa-8ee5-4ee7-b283-3f1c3e5d4241">

<img width="750" alt="84" src="https://github.com/sehun98/TIL/assets/100746863/99a4c395-813f-4749-bcd5-2a1be326a226">

<img width="750" alt="85" src="https://github.com/sehun98/TIL/assets/100746863/293203be-5796-4989-bd69-bb548fa4ec86">

<img width="500" alt="86" src="https://github.com/sehun98/TIL/assets/100746863/648f7213-5d49-41f9-affd-b72cb34794a3">





<br>

<br>
