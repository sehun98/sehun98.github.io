---
title: "Basic Electronics : 기본 논리 게이트 실험"
excerpt: "기계적 스위치부터 트랜지스터로 구성한 기본 논리 게이트에 대해서 알아봅니다."
categories:
  - Basic Electronics
---

<br>

<br>

## 기본 논리 게이트 실험

 AND, OR, NOT, XOR Gate의 진리표 (True Table)를 이해합니다.

Switch를 이용하여 AND, OR, NOT Gate를 구현합니다.

Diode와 Transistor를 이용하여 AND, OR, NOT Gate를 구현합니다.

## 기계식 스위치

### AND GATE

 <img width="50%" alt="30" src="https://user-images.githubusercontent.com/100746863/191964634-a9ec7fa3-5c2a-49c4-a20e-a6215f14c8c2.PNG">

AND GATE 진리표

| SW1  | SW2  | LED  |
| ---- | ---- | ---- |
| 0    | 0    | 0    |
| 0    | 1    | 0    |
| 1    | 0    | 0    |
| 1    | 1    | 1    |

<img width="100%" alt="33" src="https://user-images.githubusercontent.com/100746863/191965430-598dfb39-eb8f-4f7c-abbd-61d55e834547.PNG">



### OR GATE

<img width="50%" alt="31" src="https://user-images.githubusercontent.com/100746863/191964637-c40301f8-613c-4796-9edd-34675da60d97.PNG">

OR GATE 진리표

| SW1  | SW2  | LED  |
| ---- | ---- | ---- |
| 0    | 0    | 0    |
| 0    | 1    | 1    |
| 1    | 0    | 1    |
| 1    | 1    | 1    |

<img width="100%" alt="34" src="https://user-images.githubusercontent.com/100746863/191965445-73a07ef5-b553-4b49-95e3-bdefebaf8926.PNG">


### NOT GATE

<img width="50%" alt="32" src="https://user-images.githubusercontent.com/100746863/191964640-82abeba2-8c3c-4957-ae03-37ecadea600d.PNG">

NOT GATE 진리표

| SW  | LED  |
| ---- | ---- |
| 0    | 1    |
| 1    | 0    |

<img width="100%" alt="35" src="https://user-images.githubusercontent.com/100746863/191965447-997cdc0f-c7da-448a-81be-7ca29bd2aee1.PNG">

<br>

**실험 결과**

기계식 스위치 만으로도 AND, OR, NOT 게이트를 만들 수 있다는 사실을 알 수 있습니다. 따라서 컴퓨터의 기본 유닛을 구성하는 XOR을 만들 수 있다는 사실이며 과거 ENIAC의 경우 진공관 2만 개, 캐패시터 1만 개, 기계식 스위치 6천 개, 저항 7만 개를 사용하여 만들어졌습니다.

<img width="50%" alt="36" src="https://user-images.githubusercontent.com/100746863/191965449-8c5cbfea-b723-4742-b396-d103b871a3d4.PNG">

XOR 게이트의 논리회로 구성(참고문헌 : ‘디지털 논리회로 이해’, 오창환 저, 한국학술정보㈜)

<br>

## 다이오드를 이용한 AND, OR 논리 구현과 TR을 이용한 NOT 논리 구현

<img width="50%" alt="37" src="https://user-images.githubusercontent.com/100746863/191966938-ddb70f59-357c-41a3-a739-ca243102c810.PNG">

<img width="100%" alt="40" src="https://user-images.githubusercontent.com/100746863/191966949-dd85a66c-75a9-474a-aee3-a3664bacd5fb.PNG">

| SW1  | SW2  | LED  |
| ---- | ---- | ---- |
| 0    | 0    | 0    |
| 0    | 1    | 0    |
| 1    | 0    | 0    |
| 1    | 1    | 1    |

<img width="50%" alt="38" src="https://user-images.githubusercontent.com/100746863/191966942-732ebea4-d42d-4377-b77c-dd6780d05cc5.PNG">

<img width="100%" alt="41" src="https://user-images.githubusercontent.com/100746863/191966955-97a30bf6-3dea-4907-9dff-308ac5eeced6.PNG">

| SW1  | SW2  | LED  |
| ---- | ---- | ---- |
| 0    | 0    | 0    |
| 0    | 1    | 1    |
| 1    | 0    | 1    |
| 1    | 1    | 1    |

<img width="50%" alt="39" src="https://user-images.githubusercontent.com/100746863/191966946-e2c925bc-9892-4010-934d-09ea97e2215c.PNG">



## 로직 게이트 IC를 통한 AND, OR, NOT, XOR의 동작 확인

<img width="50%" alt="42" src="https://user-images.githubusercontent.com/100746863/191966961-6cd25cd2-a197-4898-b650-bfae8439c785.PNG">
<img width="50%" alt="43" src="https://user-images.githubusercontent.com/100746863/191966965-264c6f3c-b26e-45f8-9260-43f00d6fd2e3.PNG">
<img width="50%" alt="44" src="https://user-images.githubusercontent.com/100746863/191966966-a9f3349e-6fc4-4303-8f7f-5df341111596.PNG">
<img width="50%" alt="45" src="https://user-images.githubusercontent.com/100746863/191966967-142a8fa6-c1c5-45ea-9c35-288ed9adfa39.PNG">
<img width="100%" alt="46" src="https://user-images.githubusercontent.com/100746863/191966970-cad1ba80-3eaa-4f02-9b8b-fc95ced8fa34.PNG">

AND(7408)

| **Input 1** | **Input 2** | **LED** |
| ----------- | ----------- | ------- |
| 0           | 0           | **0**   |
| 0           | 1           | **0**   |
| 1           | 0           | **0**   |
| 1           | 1           | **1**   |

OR(7432)

| **Input 1** | **Input 2** | **LED** |
| ----------- | ----------- | ------- |
| 0           | 0           | **0**   |
| 0           | 1           | **1**   |
| 1           | 0           | **1**   |
| 1           | 1           | **1**   |

NOT(7404)

| **Input 1** | **LED** |
| ----------- | ------- |
| 1           | **0**   |
| 0           | **1**   |

XOR(7486)

| **Input 1** | **Input 2** | **LED** |
| ----------- | ----------- | ------- |
| 0           | 0           | **0**   |
| 0           | 1           | **1**   |
| 1           | 0           | **1**   |
| 1           | 1           | **0**   |

## 3 Input AND, OR의 동작 확인

<img width="100%" alt="47" src="https://user-images.githubusercontent.com/100746863/191966972-088a79e3-68b1-483a-8447-5bc354e9eb00.PNG">

3 Input AND

| **Input 1** | **Input 2** | **Input 3** | **Output** |
| ----------- | ----------- | ----------- | ---------- |
| 0           | 0           | 0           | 0          |
| 0           | 0           | 1           | 0          |
| 0           | 1           | 0           | 0          |
| 0           | 1           | 1           | 0          |
| 1           | 0           | 0           | 0          |
| 1           | 0           | 1           | 0          |
| 1           | 1           | 0           | 0          |
| 1           | 1           | 1           | 1          |

<img width="100%" alt="48" src="https://user-images.githubusercontent.com/100746863/191966974-fbacf106-f628-4061-80f3-f01e7f08879c.PNG">

3 Input OR

| **Input 1** | **Input 2** | **Input 3** | **Output** |
| ----------- | ----------- | ----------- | ---------- |
| 0           | 0           | 0           | 0          |
| 0           | 0           | 1           | 1          |
| 0           | 1           | 0           | 1          |
| 0           | 1           | 1           | 1          |
| 1           | 0           | 0           | 1          |
| 1           | 0           | 1           | 1          |
| 1           | 1           | 0           | 1          |
| 1           | 1           | 1           | 1          |



<img width="75%" alt="49" src="https://user-images.githubusercontent.com/100746863/191966975-947835e7-5c39-449b-b458-e01ca777dff7.PNG">

## 실험 중 발생한 오류

### Floating 현상

피아노 스위치를 사용할 때 플로팅 현상에 의해 LED가 오작동 하는 상황이 발생했습니다.

스위치를 눌러도 항상 켜져있는 것을 알 수 있습니다.

<img width="75%" alt="50" src="https://user-images.githubusercontent.com/100746863/191966977-a95e8403-5940-469a-b9b9-890698c7ae02.PNG">

### 해결 방안

피아노 스위치를 사용할 때 하기와 같은 회로 구성이 되어 Pull-Down 저항을 달아주거나 다른 스위치를 사용해야 합니다.

#### 플로팅 발생 회로

<img width="100%" alt="51" src="https://user-images.githubusercontent.com/100746863/191966983-b92b5dce-3ab2-4dfb-8363-366413fd64b0.PNG">
#### 플로팅 현상 Pull-Down으로 수정한 회로

<img width="100%" alt="52" src="https://user-images.githubusercontent.com/100746863/191966987-e29a0284-55c8-4d5a-8b96-135fd992dfd2.PNG">

<br>

<br>
