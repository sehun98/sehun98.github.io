---
title: "Basic Electronics : C-E와 C-C"
excerpt: "공통 이미터와 공통 컬렉터 증폭기"
categories:
  - Basic Electronics
---

<br>

<br>

### 공통이미터 증폭기

공통 이미터 증폭기에 대해 이해 할 수 있습니다.

베이스에 입력신호를 가하고 출력을 컬렉터에서 얻는 공통 이미터 증폭기의 특성을 이해 합니다.

공통 이미터 증폭기는 입력과 출력 신호의 위상 차이가 180도 있다는 사실을 이해합니다.

---

<img width="750" alt="171" src="https://github.com/sehun98/TIL/assets/100746863/26774b30-1358-4db9-bf48-c75724287d10">



1. Figure. 1과 같이 회로를 구성합니다.

2. 멀티미터로 Table. 1에 있는 파라미터의 측정하고, 이론 값을 계산하여 Table. 1 에 기록합니다. 이때 Function generator는 연결하지 않은 상태여야 합니다. ( 𝑉𝐵𝐸 =0.7V 가정)

3. Function generator를 (0.2Vpp, 5kHz)로 맞춘 뒤 Oscilloscope를 이용하여 입력 전압과 출력 전압을 동시에 관찰합니다. 

   A. 입력과 출력 진폭 차이가 있는가? 

   B. 입력과 출력 위상 차이가 있는가?

4. 직류 이미터 전류와, 교류 이미터 저항을 계산하여 Table. 2에 기록합니다. 

5. Oscilloscope를 이용하여 이미터 단의 전압과 RE2 양단의 전압을 관찰합니다.

6. 전압이득 기대값을 계산하고 Table. 3에 기록합니다. Oscilloscope로 Vin, Vout 측 정 후 전압 이득을 계산하여 기록합니다.

7. 부하저항 제거 후 출력전압을 관찰합니다. 

   A. 출력전압은 어떻게 변하는가? 이러한 변화의 영향 요인은? 

   B. 출력전압 측정하고 Table. 3에 기록합니다. 

8. 부하저항 연결 후 바이패스 캐패시터를 제거하고 출력전압을 관찰한다. 

   A. 전압이득의 변화는 어떠한가? 그 이유는 무엇인가? 

   B. Table. 3의 파라미터에 대한 값을 측정하고 계산하여 기록한다.

9. 바이패스 캐패시터와 부하 저항이 이득에 어떠한 영향을 주는지 이해한다.

<img width="300" alt="180" src="https://github.com/sehun98/TIL/assets/100746863/8d8b621b-141c-464b-82f5-dca98992893f">



Table - 1 직류값

<img width="500" alt="172" src="https://github.com/sehun98/TIL/assets/100746863/067b60f4-8e89-4970-af01-de43b7831a5a">



Table - 2 교류 이미터 저항



<img width="300" alt="173" src="https://github.com/sehun98/TIL/assets/100746863/058e4b68-f22f-44f8-a156-54806f5f950a">



Table - 3 교류 이미터 저항

<img width="500" alt="174" src="https://github.com/sehun98/TIL/assets/100746863/b6e9423c-a691-4210-a52c-5154f892c057">

<img width="750" alt="175" src="https://github.com/sehun98/TIL/assets/100746863/72391f21-d415-43b2-9f13-516b65aa5bce">
<img width="750" alt="176" src="https://github.com/sehun98/TIL/assets/100746863/0a9a0f9d-5ef3-4bdf-87a2-dee0b8b6e3c3">



정상 회로 출력 파형

<img width="750" alt="177" src="https://github.com/sehun98/TIL/assets/100746863/2cc034ae-a027-48a5-bbae-17959c974806">



무부하 회로 출력 파형

출력 파형에 Offset이 존재하는 것을 알 수 있습니다.

<img width="750" alt="178" src="https://github.com/sehun98/TIL/assets/100746863/63393ab0-b794-4917-9d7a-c8fc2fd3c14f">

바이패스 제거 회로 출력 파형

<img width="750" alt="179" src="https://github.com/sehun98/TIL/assets/100746863/2bcef3f2-29d9-48df-a303-996b3dfb8be1">



OrCAD 시뮬레이션



정상 회로 출력 파형
<img width="750" alt="181" src="https://github.com/sehun98/TIL/assets/100746863/a8f79941-0c91-4c0a-9c7f-2e90e9ec6464">



<img width="750" alt="182" src="https://github.com/sehun98/TIL/assets/100746863/724568eb-5fa7-4f41-a87e-d3a31b538a8b">

무부하 회로 출력 파형

<img width="750" alt="183" src="https://github.com/sehun98/TIL/assets/100746863/e820bffa-b85d-4ad2-b59c-2d41ae8121d3">

<img width="750" alt="184" src="https://github.com/sehun98/TIL/assets/100746863/c66bfe89-5a58-4732-9b6e-235966eb99db">

바이패스 제거 회로 출력 파형

<img width="750" alt="185" src="https://github.com/sehun98/TIL/assets/100746863/30224815-886c-49cf-bfda-8c6ebca6b724">
<img width="750" alt="186" src="https://github.com/sehun98/TIL/assets/100746863/93a3c032-24cf-4b2e-bf35-fc4eb4866655">



### 공통컬렉터(이미터 폴로어) 증폭기

소신호 공통컬렉터 증폭기의 특성 및 동작을 살펴보고 무엇이 이득에 영향을 주는지 알아 있습니다.

출력전압은 입력전압보다 크지 않고 입출력 전압간에 위상차이는 없습니다.

일반적으로 다른 트랜지스터 증폭기에 비해 입력 임피던스가 높다는 장점이 있습니다.

---

<img width="750" alt="187" src="https://github.com/sehun98/TIL/assets/100746863/1d4de0fd-429d-4fba-991a-346e4b5030ad">

<img width="300" alt="196" src="https://github.com/sehun98/TIL/assets/100746863/3830d485-5a38-4b27-9f2f-40f1f5c464b8">



1. Figure. 2와 같이 회로를 구성합니다.

2. 멀티미터로 Table. 4에 있는 파라미터의 측정하고, 이론 값을 계산하여 Table. 4에 기록합니다. ( 𝑉𝐵𝐸 =0.7V 가정)

3. Function generator를 0.2Vpp, 5kHz로 맞춘 뒤 Oscilloscope를 이용하여 입력 전압 Ch2 Ch1 과 출력 전압을 동시에 관찰합니다.

   A. 입력과 출력 진폭 차이가 있는가? 

   B. 입력과 출력 위상 차이가 있는가? 

4. 직류 이미터 전류와, 교류 이미터 저항을 계산하여 Table. 5에 기록합니다.

5. 를 이용하여 부하저항 양단의 전압을 측정하고 기대값을 계산합니다. 출력전압과 입력전압을 스코프를 이용하여 살펴보고, 이득을 구한 뒤 Table. 6에 기록합니다.

6. Table. 6의 다른 저항값으로 부하저항을 바꾸어 달고 실험순서 5를 반복합니다. 

   A. 출력전압의 크기는 어떻게 변하는가? 그 이유는?



Table. - 4

<img width="750" alt="188" src="https://github.com/sehun98/TIL/assets/100746863/97c94fe9-fc58-44b2-9622-9b740ee19537">

Table. - 5

<img width="400" alt="189" src="https://github.com/sehun98/TIL/assets/100746863/0a19ac4e-b606-48b1-b360-ada7cddd41d0">

Table. - 6

<img width="750" alt="190" src="https://github.com/sehun98/TIL/assets/100746863/8d7fa03d-aa50-431f-8ffa-89c86f777fa2">

<img width="750" alt="191" src="https://github.com/sehun98/TIL/assets/100746863/eab7521c-d1b9-44de-a3c3-7d3c553dc011">

<img width="750" alt="192" src="https://github.com/sehun98/TIL/assets/100746863/03f8dc2e-8208-4b9f-a6f3-3fcb28525deb">



부하 저항 1.2kΩ

<img width="750" alt="193" src="https://github.com/sehun98/TIL/assets/100746863/13978904-4451-4783-9e18-9c062a0c48eb">

부하 저항 100Ω

<img width="750" alt="194" src="https://github.com/sehun98/TIL/assets/100746863/64bd17f7-53d7-4af3-ac5d-a5b5ae1c6d8d">

부하 저항 56Ω

<img width="750" alt="195" src="https://github.com/sehun98/TIL/assets/100746863/d4eb4fcf-ef31-487a-be72-2cfdcc363184">

OrCAD 시뮬레이터

<img width="500" alt="197" src="https://github.com/sehun98/TIL/assets/100746863/bdb19f86-2f92-4c2e-b8a9-6220cb4357d4">

부하 저항 1.2kΩ

<img width="750" alt="198" src="https://github.com/sehun98/TIL/assets/100746863/af34531a-ec32-48fb-a49a-46fa59e01a69">

부하 저항 100Ω

<img width="750" alt="199" src="https://github.com/sehun98/TIL/assets/100746863/8b793b73-0ed8-48dc-be18-0225eac732d1">

부하 저항 56Ω

<img width="750" alt="200" src="https://github.com/sehun98/TIL/assets/100746863/fbbeff55-0beb-4733-ba69-5a93a7bcb050">



#### 실험 결과 및 고찰 

앞에서는 트랜지스터를 이용한 전자식 스위치를 알아보았다면 이번 실험은 Common Emitter Amplifier와 Common Collector Amplifier의 트랜지스터 증폭기에 대해서 학습을 하였습니다. 

실험 1에서는 C-E Amp에서 정상회로, 부하 제거, 바이패스 제거의 상황에서 전압이득의 변화를 보는 실험입니다. 

정상 회로에서 RL이 존재하기 때문에 RC와 RL의 병렬 합성으로 다음과 같은 전압 이득이 됩니다. 

𝐴𝑣 = (𝑅𝐶||𝑅𝐿 ) / (𝑅𝐸1 + 𝑟𝑒 ′) 

하지만 부하 제거에서 RL이 없기 때문에 병렬 합성을 할 필요가 없어 더 큰 전압 이득 을 같습니다. 

𝐴𝑣 = 𝑅𝐶 / (𝑅𝐸1 + 𝑟𝑒 ′) 

그렇다면 바이패스의 용도는 무엇일까요?? 바이패스는 트랜지스터에 인가되는 교류 신호를 캐패시터를 통해 바이패스 하는 역할을 합니다. 

따라서 RE2가 없는 것과 같은 회로가 되는데 바이패스가 사라지면 RE2를 통해서 전류가 흐르기 때문에 다음과 같은 전압 이득이 발생합니다. 

𝐴𝑣 = ( 𝑅𝐶||𝑅𝐿 ) / (𝑅𝐸1 + 𝑅𝐸2 + 𝑟𝑒 ′ ) 

따라서 간단한 캐패시터에 불과하지만 역할이 중요한 것을 볼 수 있습니다

실험 2에서는 C-C Amp에서 부하 저항이 달라졌을 때 버퍼의 역할이 일정한가에 대해 알아보는 실험입니다. 

부하 저항 1.2kΩ에서 Av = 1에 가깝게 출력 전압이 일정하지만 부하저항이 낮아 질 수록 Av = 1보다는 낮아지는 것을 볼 수 있습니다. 

하지만 그럼에도 너무 큰 차이가 발생 하지는 않습니다. 

Class A Amplifier라고도 불리는 Common Emitter Amplifier는 주로 효율이 좋지 않지 만 증폭을 하는데 사용됩니다. 

Common Collector Amplifier의 경우 input impedance가 높고 output impedance가 낮아 전류 증폭기/버퍼로 사용됩니다. 

OP-AMP에 대해서 간단하게 알아보겠습니다.



<img width="750" alt="201" src="https://github.com/sehun98/TIL/assets/100746863/0132d608-6d26-42b7-bc40-a2595b698b6f">

<img width="750" alt="202" src="https://github.com/sehun98/TIL/assets/100746863/65206629-0a4f-47df-ac34-7d64077a6dd2">
<img width="750" alt="203" src="https://github.com/sehun98/TIL/assets/100746863/83e3f823-8527-46bb-bc51-9a1455bd0228">

<br>

<br>
