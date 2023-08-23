---
title: "PADS : FPGA Decal"
excerpt: "FPGA를 만드는 방법을 알아봅니다."
categories:
  - PADS
---

<br>

<br>

1. PADS Layout > Tools > PCB Decal Editor > Wizard
2. Bow 사이즈에 따라 트레이스 사이즈와 전원부 via 사이즈가 달라지므로 계산을 잘해야한다.
3. 선 정리 및 slikscreen Top 설정
4. Setup > Display colors 에서 Pin number 지우기
5. Save As 저장하기



### **세부 내용**

[중요]

Bow 사이즈에 따라 `트레이스 사이즈`와 `전원부 via 사이즈`가 달라지므로 계산을 잘해야한다.

datasheet 참고

<img width="750" alt="122" src="https://github.com/sehun98/TIL/assets/100746863/eba92e6f-3805-4b43-b841-0e14a4606315">

PADS Layout > Tools > PCB Decal Editor > Wizard

<img width="750" alt="123" src="https://github.com/sehun98/TIL/assets/100746863/d6ef02f8-1ea6-4738-934e-f9970915b2de">

<img width="600" alt="124" src="https://github.com/sehun98/TIL/assets/100746863/d3ba8d9a-018d-4df0-b305-ee3d17e4c4ae">

PIN NUMBER 지우기

<img width="750" alt="125" src="https://github.com/sehun98/TIL/assets/100746863/dbf14cbd-0013-4fb2-94a6-728bf7714ff8">

<img width="600" alt="126" src="https://github.com/sehun98/TIL/assets/100746863/2f6f9375-710a-498a-b73d-874d69fcefb1">

2D Line 에서 hc 명령어로 원을 그려준다.

q 명령어로 길이를 측정할 수 있다.

<img width="600" alt="127" src="https://github.com/sehun98/TIL/assets/100746863/5028ca5d-f0fe-4241-8742-0096025f45db">

<img width="400" alt="128" src="https://github.com/sehun98/TIL/assets/100746863/875c68df-626b-4c7f-b913-3467de826e6d">

## **Part 와 Decal 이어주기**

### **요약**

1. PADS Logic > Part Information for Part > PCB Decals 에서 Assign 해주기

### **세부내용**

<img width="750" alt="129" src="https://github.com/sehun98/TIL/assets/100746863/4ae0f6e8-7f78-4ceb-a42e-d470905d480d">

<img width="750" alt="130" src="https://github.com/sehun98/TIL/assets/100746863/df5866be-4e18-4d31-b04d-ca00d6d26be0">



<br>

<br>
