---
title: "Basic Electronics : 플립플롭"
excerpt: "Flip-flop & Counter에 학습해봅니다."
categories:
  - Basic Electronics
---

<br>

<br>

JK 플립플롭을 이용하여 D 플립플롭과 T 플립플롭을 구현하고 동작을 확인합니다.

플립플롭을 이용하여 간단한 카운터 회로를 구현합니다.

---

### JK Flip-Flop Application

<img width="300" alt="117" src="https://github.com/sehun98/TIL/assets/100746863/fc1c3ec2-8520-4dbf-9aea-a1d85680c682">

채터링 노이즈에 오동작하는 경우가 많았습니다.

<img width="750" alt="131" src="https://github.com/sehun98/TIL/assets/100746863/2f961270-37fa-4e22-bd64-46d5da583b66">

OrCAD 시뮬레이션 결과 

초기 상태를 0으로 설정해주어야 합니다.

<img width="750" alt="118" src="https://github.com/sehun98/TIL/assets/100746863/ccf5b07d-7738-4147-abd6-527c0767bbe1">

### JK FF를 이용한 T FF

<img width="750" alt="119" src="https://github.com/sehun98/TIL/assets/100746863/1fd30c87-3596-4aac-b5b9-d619234bd1d5">

<img width="750" alt="120" src="https://github.com/sehun98/TIL/assets/100746863/7eadf3c5-28e0-4d41-9d93-1119547f7b7e">



<img width="750" alt="121" src="https://github.com/sehun98/TIL/assets/100746863/c4cc6aae-eefb-4e3d-85a2-d23cb7b0fbab">



| CLOCK | Q3   | Q2   | Q1   | Q0   | Decimal |
| ----- | ---- | ---- | ---- | ---- | ------- |
| 1st   | 1    | 1    | 1    | 1    | 15      |
| 2nd   | 1    | 1    | 1    | 0    | 14      |
| 3rd   | 1    | 1    | 0    | 1    | 13      |
| 4th   | 1    | 1    | 0    | 0    | 12      |
| 5th   | 1    | 0    | 1    | 1    | 11      |
| 6th   | 1    | 0    | 1    | 0    | 10      |
| 7th   | 1    | 0    | 0    | 1    | 9       |
| 8th   | 1    | 0    | 0    | 0    | 8       |
| 9th   | 0    | 1    | 1    | 1    | 7       |
| 10th  | 0    | 1    | 1    | 0    | 6       |
| 11th  | 0    | 1    | 0    | 1    | 5       |
| 12th  | 0    | 1    | 0    | 0    | 4       |
| 13th  | 0    | 0    | 1    | 1    | 3       |
| 14th  | 0    | 0    | 1    | 0    | 2       |
| 15th  | 0    | 0    | 0    | 1    | 1       |
| 16th  | 0    | 0    | 0    | 0    | 0       |

#### 16번째 클럭을 입력하면 어떻게 되는가? 

| Q3   | Q2   | Q1   | Q0   |
| ---- | ---- | ---- | ---- |
| 0    | 0    | 0    | 0    |

#### <img width="750" alt="122" src="https://github.com/sehun98/TIL/assets/100746863/b8433568-4539-413a-9a12-6445e2f63a81">

<img width="750" alt="123" src="https://github.com/sehun98/TIL/assets/100746863/d806960f-c1bb-4a73-a047-28317c3a3629">

###  Ring Counter

<img width="750" alt="124" src="https://github.com/sehun98/TIL/assets/100746863/5973279b-edb4-4af8-b836-e8e37c7dd4b3">

<img width="750" alt="125" src="https://github.com/sehun98/TIL/assets/100746863/e598a895-80af-4382-ab0a-2a048f3913df">

<img width="750" alt="126" src="https://github.com/sehun98/TIL/assets/100746863/7f7549f1-366c-4fbb-a52e-25638d72a716">





### Q. PR 과 CLR 핀의 역할은 무엇인가? 

PR (Preset)과 CLR (CLEAR)는 Set과 Reset과 무엇이 다를까? 

Set과 Reset은 클럭의 라이징 엣지 혹은 폴링 엣지에 따라 즉, 동기적으로 신호 상태를 변화 시키는 반면 Preset과 Clear는 비동기적으로 원하는 시간대에서 출력을 초기화 혹은 세팅 할 수 있습니다. 간단하게 우선순위가 가장 높다고 생각하면 될 것 같습니다. 



#### 실험에 대한 결과 분석과 고찰 

74LS76 소자를 사용함에 있어 이론에 일치하지 않고 동작하는 문제가 발생했습니다. 

이 문제가 발생 한 이유는 플립플롭은 순차 논리회로 기억소자인데 채터링 노이즈에 의한 상태 변화가 생기기 때문에 원하는 동작을 하지 않는 것을 볼 수 있습니다.

따라서 채터링 노이즈를 방지하기 위한 대책이 필요합니다. 

채터링 노이즈의 의미와 보편적인 방지책 기계적 스위치는 접점면 사이에 0과 1이 반복되는 채터링 노이즈가 발생합니다. 

마이크로프로세서,  CPU등 고속의 연산 장치들은 그러한 변화도 신호로 읽어버리기 때문에 채터링 노이즈를 제거할 필요 가 있습니다. 

채터링 노이즈를 제거하는 방법은 여러가지가 존재합니다. 

첫번째, 하드웨어적 노이즈 제거 & 두번째, 소프트웨어적 노이즈 제거 우선 하드웨어적 노이즈 제거 방법으로는 간단하게 바이패스 캐패시터를 통해 고주파 노이즈를 제거해 줄 수 있습니다. 

즉, Low Pass Filter를 통해 저주파인 디지털 신호만 신호 처리 하는 방식입니다. 

소프트웨어적 노이즈 제거 방법으로는 마이크로프로세서에서 채터링 노이즈 구간을 측정하여 2~3ms 일 경우 5ms 주기로 State를 확인하여 스위치를 동작했는지 동작하지 않았는지 확인하는 코드를 작성 할 수 있습니다. 

혹은 Low pass filter를 소프트웨어적으로 설계할 수도 있습니다. 하지만 이번 실험의 경우 마이크로프로세서를 사용하지 않기 때문에 채터링 노이즈를 제거하기 위해 하드웨어적 노이즈 제거를 진행할 필요가 있습니다. 이때 너무 캐패시터값이 큰 소자를 사용할 경우 출력 파형이 Delay 될 수 있으니 유의해서 사용합니다. 



#### 래치와 플립플롭의 차이 

래치와 플립플롭의 차이에 대해서 말해보자면 래치의 경우 High / Low Level Detect 방식으로 instruction을 수행합니다. 반면 플립플롭의 경우 클럭 동기방식으로 Low Level 에서 High Level로 올 라가는 라이징 엣지, High Level에서 Low Level로 떨어지는 폴링 엣지 순간에 instruction을 수행하게 됩니다. 

이때 클럭이란 반도체 소자에서 속도를 맞추기 위한 주기적 동작이라고 생각하시면 될 것 같습니다. 

예를 들어 1초에 10번 라이징 엣지, 폴링 엣지가 진행 되는 것을 10Hz의 클럭을 가진 소자라고 생각 하시면 됩니다. 

jk, d 플립플롭의 원리(논리 게이트 단위로 클럭의 엣지에 따른 동작 설명) 우선 플립플롭을 왜 써야했는지에 대해서 이해를 하고 JK 플립플롭과 D 플립플롭이 어떤이유로 생기 게 되었는지 말씀드리겠습니다. 

플립 플롭을 사용하게 된 이유는 조합논리회로와 순서논리회로가 존재하는데 수행한 결과를 저장하는 순서논리회로가 필요하게 되었습니다. 

이때 Not gate 두개로 이전의 상태를 기억하고자 했습니다.

하지만 이 회로는 출력이 항상 1 또는 0과 같기 때문에 상태를 변화하지 않으며 영구적으로 설정되는 문제점을 가지고 있습니다. 따라서 SR 플립플롭을 사용하게 되었습니다. 

SR 혹은 RS 플립플롭은 Reset과 Set으로 상태를 변화 시키는 기억소자로 클럭의 라이징엣지 혹은 폴 링 엣지 타이밍때 Set : 0 / Reset : 1 일 경우 Q(t+1) : 1 이 되고 Set : 1 / Reset : 0 일 경우 Q(t+1) :  0 이 됩니다. 

이때 Set : 1 / Reset : 1인 경우를 사용하지 않기 때문에 이를 사용하기 위해서 JK 플립플롭이 생기게 됩니다.

<img width="400" alt="127" src="https://github.com/sehun98/TIL/assets/100746863/350eb40c-64e9-490e-ba22-5437a4f616cc">

JK 플립플롭은 RS 플립플롭에서 Reset과 Set 모두 1인 상태를 사용하기 위해 출력을 다시 궤환하는 회로를 추가하여 Toggle 기능을 사용할 수 있게 하였습니다

<img width="400" alt="128" src="https://github.com/sehun98/TIL/assets/100746863/342be4ad-f0c1-4bb2-aaaa-6e7c3b58f004">

T 플립플롭은 Toggle 플립플롭으로 Reset과 Set을 묶어서 Toggle의 기능만 사용할 수 있게 만들어진 소자입니다.

<img width="400" alt="129" src="https://github.com/sehun98/TIL/assets/100746863/90f86cef-d025-4342-8356-331c662f96d8">

D 플립플롭은 Data 플립플롭으로 Reset과 Set이 공통인 신호가 나오지 않게 만든 소자입니다.

<img width="400" alt="130" src="https://github.com/sehun98/TIL/assets/100746863/d70a9db1-a686-4b46-a408-3b53e0040691">

<br>

<br>
