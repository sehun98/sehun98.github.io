---
title: "Basic Electronics : OPAMP"
excerpt: "Operational amplifier"
categories:
  - Basic Electronics
---

<br>

<br>

### 연산증폭기를 이용한 반전증폭기와 비반전증폭기

---

741 연산증폭기를 이용한 반전증폭기와 비반전증폭기의 회로의 동작을 알아봅니다.

반전증폭기의 폐회로 전압이득은 1보다 작거나 같거나 크게 만들 수 있습니다. 출력신호는 입력신호 와 반전되어 있습니다.

비반전증폭기의 전압이득은 항상 1보다 크며, 입력신호와 출력신호는 동위상입니다.





<img width="500" alt="204" src="https://github.com/sehun98/TIL/assets/100746863/2d68f02f-10cb-4e5e-ace7-95b777ef2811">



1. Figure. 1과 같이 회로를 구성하고 오실로스코프를 채널1, 채널2 : 모두 0.5V/division, 시간: 1ms/division으로 맞춥니다.

2. 주파수 500Hz, 첨두치 전압 Vpp=1V가 되도록 입력전압을 가합니다. 1-2.1. 입력, 출력 신호의 차이점은? 

3. 출력전압을 측정하고 그림을 기록합니다. 전압이득을 구하여 기대값과 비교 하고 결과를 Table. 1에 기록합니다.

4. Table. 1과 같이 피드백 저항을 변화시키며 실험순서 3과 같이 결과를 기록합니다. 

   반전증폭기의 전압이득에 대한 공식에서 계산한 값과 일치하는가? 

   ※ Vin과 Vout의 측정치의 비율을 통해 이득 측정값을 계산합니다.

5. Figure. 2와 같이 회로를 구성하고 주파수 400Hz, 첨두치 전압 Vpp = 1V가 되도록 입력전압을 조절한다. 

   입력, 출력 신호의 차이점은? 

6. 출력전압을 측정하고 기록한다. 전압이득을 구하여 기대값과 비교하고 결과를 Table. 2에 기록한다.

7. Table. 2의 피드백 저항을 변화시키며 실험순서 6과 같이 결과를 기록한다. 

   측정결과가 비반전증폭기의 전압이득과 관련한 공식에서 계산한 값 과 일치하는가?

   ※ Vin과 Vout의 측정치의 비율을 통해 이득 측정값을 계산합니다.

Table - 1 반전 증폭기

<img width="750" alt="205" src="https://github.com/sehun98/TIL/assets/100746863/e3bbf02a-c6bd-4caf-8bbe-8259fba45067">



Table - 2 비반전 증폭기

<img width="750" alt="206" src="https://github.com/sehun98/TIL/assets/100746863/cd43e4b6-a92d-4079-810a-a834d35db964">

<img width="750" alt="207" src="https://github.com/sehun98/TIL/assets/100746863/76f4d9ed-a5fd-4c15-b321-1cacedb4f2b8">

<img width="750" alt="208" src="https://github.com/sehun98/TIL/assets/100746863/c7d8b737-9a48-4cd0-822c-2cb597791d49">



<img width="500" alt="209" src="https://github.com/sehun98/TIL/assets/100746863/df9c7db5-f935-43b8-a8aa-eb57bf39b3ed">

<img width="750" alt="210" src="https://github.com/sehun98/TIL/assets/100746863/1ff0853e-3ed5-4add-9b7f-105813a267a8">

<img width="400" alt="211" src="https://github.com/sehun98/TIL/assets/100746863/f4990533-23b0-4c90-b547-b7e4edc8bdc9">

<img width="750" alt="212" src="https://github.com/sehun98/TIL/assets/100746863/85d2da84-8264-4c97-9913-e049ace53427">



### 연산증폭기를 이용한 비교기

741 연산증폭기를 이용한 비반전비교기와 반전비교기의 동작을 알아봅니다.

비교기는 입력전압이 미리 정해진 기준값보다 더 큰지 혹은 더 작은지를 결정합니다. 

비교기는 개회로 모드로 동작하므로 출력전앖은 + 또는 –의 전원전압에 근접합니다.

---

<img width="500" alt="213" src="https://github.com/sehun98/TIL/assets/100746863/df193a1a-2504-4b5f-b7df-692eb5abefc8">





1. Figure. 3과 같이 회로를 구성하고 오실로스코프를 채널1 : 1V/division, 채널2 :  10V/division, 시간: 1ms/division으로 맞춥니다.

2. 주파수 300Hz, 첨두치 전압 3Vpp의 입력전압을 가합니다. 

   A. 입력신호가 +일 때 출력전압의 극성은? 반대의 경우는? 

3. Figure. 4와 같이 회로를 구성하고 입력 출력 특성을 살펴본다.

   A. 위의 동작과의 차이는?

   

<img width="750" alt="214" src="https://github.com/sehun98/TIL/assets/100746863/678f2468-7935-48a4-aba5-f3cc854e5e29">

<img width="750" alt="215" src="https://github.com/sehun98/TIL/assets/100746863/e4eee044-f9aa-4e30-bf85-ff949d4e11ef">

<img width="750" alt="216" src="https://github.com/sehun98/TIL/assets/100746863/8b2f83b7-3e6a-47ad-b3b4-adaac40a64ca">



#### 실험 결과 및 고찰

실험 결과와 AV 유도 공식에 의해 Rf 피드백 저항의 변화와 전압이득의 연관 관계를 알아보았습니다.



이러한 OPAMP와 TR의 전압 이득과는 어떠한 차이가 있을까?

트랜지스터는 노이즈도 함께 증폭 시킨다는 점이 있는 반면 OPAMP는 두 입력 측에 공통으로 들어오는 점이 있는 반면 OPAMP는 두 입력 측에 공통으로 들어오는 전원 노이즈 같은 공통 노이즈는 Differential AMP에 의해 제거가 됩니다.

이러한 OPAMP는 비교기, 증폭기, 가산기, 감산기, 미분기, 적분기 외에도 슈미트 트리거, instrument OPAMP, ADC, DAC, Log & Anti Log, Pick Ditector, Voltage Current Convertor, Current to Voltage, Isolation OPAMP, Active LPF/HPF/BPF/BSF 등에 활용될 수 있습니다.



마지막으로 OPAMP의 5가지 특성을 암기합니다.

1. input impedance가 매우 높습니다.
2. output impedance가 매우 낮습니다.
3. AOL가 매우 높습니다.
4. BW가 매우 넓습니다.
5. CMRR이 매우 높습니다.



<br>

<br>
