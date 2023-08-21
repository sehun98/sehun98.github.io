---
title: "Basic Electronics : 미분기 & 적분기"
excerpt: "연산 증폭기를 이용한 미분기, 적분기에 대해 알아봅니다."
categories:
  - Basic Electronics
---

<br>

<br>

### 미분기

연산증폭기를 이용한 미분기와 적분기의 동작을 설명할 수 있습니다. 

미분기는 파형의 모든 지점에서 선분의 순간적 기울기를 계산하는 회로입니다. 

적분기는 주어진 파형에서 곡선 아래의 면적을 계산합니다.



<img width="500" alt="217" src="https://github.com/sehun98/TIL/assets/100746863/4c861255-9637-44f9-a688-5181d1fa8f7b">

1. Figure. 1과 같이 회로를 구성하고, CH1: 500mV/div, 직류결합(DC 1M), CH2:  50mV/div, 직류결합(DC 1M), 시간축 500μs/div으로 오실로스코프를 조정합니다. 

2. Power Supply로 ±15V전원 및 접지를 공급하고, Function Generator로 1Vpp으로 입력 전압을 조절하여 주파수가 400Hz이고, Symmetry를 50%로 삼각파를 설정합니다. 

3. 프로브를 입력전압과 미분기 출력단에 연결하여, 오실로스코프로 두 파형을 동시에 캡처하고, 접지를 기준으로 (-)피크전압을 측정하여 Table. 1에 기록합니다. 

4. 출력 파형이 (-)값을 가지는 기간(t1)을 측정합니다. 피크전압 𝑉𝑚(0.5V)을 갖는 삼각파를 미분하여 발생하는 출력파형의 전압은 다음 식으로 주어집니다. 

   𝑣𝑜𝑢𝑡(𝑝𝑒𝑎𝑘) = − (2𝑅𝐹𝐶𝑉𝑚) / 𝑡1

5. (-)피크전압의 기대값을 계산하여 위에서 측정한 전압과 비교하고 결과를 Table. 1에 기록합니다. 
6. 입력주파수를 1kHz로 맞추고, 실험순서 3, 4를 반복합니다. 
7. 입력주파수를 30kHz로 변경합니다. 



### 적분기

<img width="500" alt="218" src="https://github.com/sehun98/TIL/assets/100746863/68786d00-5fd3-436e-9c4d-041688a47c12">



1. Figure. 2와 같이 적분기 회로를 구성하고, CH1, CH2 : 500mV/div, 직류결합(DC  1M), 시간축 20μs/div으로 오실로스코프를 조정합니다.

2. 브레드보드에 전원을 가하고 입력전압을 조절하여 크기가 1Vpp, 주파수가 10kHz, Symmetry가 50%인 구형파(Square파)가 되도록 합니다.

3. 출력파형의 (-)피크전압을 접지를 기준으로 측정하여 Table. 2에 기록하고, 입력 전압과 출력전압의 파형을 동시에 캡쳐합니다.

4. 출력파형이 (-)값을 가지는 기간(t1)을 측정합니다. 피크전압 𝑉𝑚을 갖는 구형파를 적분하여 발생하는 출력파형의 전압은 다음과 같습니다. 

   𝑣𝑜𝑢𝑡(𝑝𝑒𝑎𝑘) = − 𝑉𝑚𝑡1 / 2𝑅1𝐶 

5. (-)피크전압의 기대값을 계산하여 위에서 측정한 값과 비교하고 결과를 Table. 2 에 기록합니다. 
6. 입력주파수를 4kHz로 맞춘다. 실험순서 3,4를 반복합니다.
7. 피크간 출력전압을 측정하고 전압이득을 구하여 그 값을 Table. 2 에 기록합니다. 
8. 반전증폭기의 전압이득에 비하여 전압이득은 어떠한가? 
9. 입력주파수를 100Hz로 변경합니다.



<img width="750" alt="220" src="https://github.com/sehun98/TIL/assets/100746863/8826d3f4-36b2-4c83-ac28-892d0587d2d7">





<img width="750" alt="221" src="https://github.com/sehun98/TIL/assets/100746863/6534fe09-6ce3-42c7-b01d-86e179a8bcba">



<img width="750" alt="222" src="https://github.com/sehun98/TIL/assets/100746863/07cf3427-a76d-4e32-be16-b5a77e2bc83c">



<img width="750" alt="223" src="https://github.com/sehun98/TIL/assets/100746863/f0e93bb7-3919-4134-bbe7-e36207465dfa">

<img width="750" alt="224" src="https://github.com/sehun98/TIL/assets/100746863/aa36ac0c-82a2-4534-911b-1de40258a495">

<img width="750" alt="225" src="https://github.com/sehun98/TIL/assets/100746863/f77fae5f-1728-4d83-8014-ef2037192ce7">

<img width="750" alt="226" src="https://github.com/sehun98/TIL/assets/100746863/52c7444c-f396-4c7c-bce1-5ae9d906cb1e">

<img width="750" alt="227" src="https://github.com/sehun98/TIL/assets/100746863/df88a6c0-b828-4a80-9658-7476117de8c9">

<img width="750" alt="228" src="https://github.com/sehun98/TIL/assets/100746863/b8a422f9-9928-46f3-b911-0d609a2a013b">



<img width="750" alt="229" src="https://github.com/sehun98/TIL/assets/100746863/6eafed9f-2d61-41f1-a533-7e39a80b49b3">
<img width="750" alt="230" src="https://github.com/sehun98/TIL/assets/100746863/b3d9b87f-15b1-4ac9-8f85-b9a992aaa38e">



<img width="750" alt="231" src="https://github.com/sehun98/TIL/assets/100746863/011d460a-5777-4662-9f5d-d210168456b3">

<img width="750" alt="232" src="https://github.com/sehun98/TIL/assets/100746863/c1c3ebc6-8f16-4f5c-98ab-778e8d2ca13f">

<img width="750" alt="233" src="https://github.com/sehun98/TIL/assets/100746863/c572f262-ad48-4c10-a4c8-f3b930022ee2">



<img width="750" alt="234" src="https://github.com/sehun98/TIL/assets/100746863/444e0cc8-e733-4971-9a36-b20ee0e37aa9">

<img width="750" alt="235" src="https://github.com/sehun98/TIL/assets/100746863/43aa3204-bb5a-4ff0-aef1-1a0e3fcfdd85">



#### 실험 결과 및 고찰

미분기는 이전에 실험한 반전 증폭기와 비슷한 형태로 반전 입력 임피던스에 캐패시터가 달려 있고 피드백 임피던스는 저항이 달려 있습니다. 출력 전압의 경우 Q = CV에 의해 다음과 같이 출력됩니다.

𝑽𝒐 (𝒕) = − 𝟏 / 𝑹𝑪 * 𝑽𝑰 (𝒕) * 𝒅 / 𝒅t

미분기는 주파수가 높아짐에 따라 이득이 증가하여 일정 주파수를 넘게 되면 반전 증폭기의 역할을 하게 됩니다.

𝒇𝒄 = 𝟏 / 𝟐𝝅𝑹C



적분기는 반전 입력 단자에 저항이 달려있고 피드백 임피던스는 캐패시터로 구성되어 있습니다. 

𝑽𝒐 (𝒕) = − 𝟏 / 𝑹𝑪 ∫ 𝑽𝑰 (𝒕)𝒅𝒕 

적분기는 미분기와 반대로 주파수가 높아짐에 따라 이득이 감소하게 됩니다.



따라서 미분기와 적분기를 사용할 때 필요한 적절한 R, C 값을 선정해야 합니다. 

미분기는 주파수가 낮은 신호에서만 미분기로 동작하고 주파수가 높은 신호에서는 HPF로 동작합니다. 

적분기는 주파수가 낮은 신호에서는 LPF로 동작하고 주파수가 높은 신호에서는 적분기로 동작합니다.

<br>

<br>
