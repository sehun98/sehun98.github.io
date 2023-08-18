---
title: "Basic Electronics : 기본 논리 게이트 실험 2"
excerpt: "기계적 스위치부터 트랜지스터로 구성한 각종 논리 게이트에 대해서 알아봅니다."
categories:
  - Basic Electronics
---

<br>

<br>

## 기본 논리 게이트 실험 2

일반 논리 게이트인 NAND, NOR, 버퍼 게이트의 논리기호와 기본 동작을 이해합니다.

실험을 통해 NAND, NOR, 버퍼 게이트의 동작 특성을 확인합니다.

NAND 및 NOR 게이트로 NOT 게이트를 구성할 수 있습니다.

### NAND GATE

<img width="750" alt="53" src="https://github.com/sehun98/TIL/assets/100746863/916335c8-f9dd-46b1-945a-097f92648d4d">

NAND GATE 진리표

| SW1  | SW2  | LED  |
| ---- | ---- | ---- |
| 0    | 0    | 1    |
| 0    | 1    | 1    |
| 1    | 0    | 1    |
| 1    | 1    | 0    |

<img width="750" alt="54" src="https://github.com/sehun98/TIL/assets/100746863/73dc7957-c4c1-437d-9574-52a608dbe62a">

<img width="750" alt="55" src="https://github.com/sehun98/TIL/assets/100746863/14fe4c6d-e1d3-45cc-a62b-efad6d1b7ee6">

### NAND GATE를 이용한 NOT 게이트

<img width="500" alt="56" src="https://github.com/sehun98/TIL/assets/100746863/6659868d-f063-43a3-a827-551dcfe8c102">

NAND GATE 를 이용한 NOT 게이트 진리표

| A    | X    |
| ---- | ---- |
| 0    | 1    |
| 1    | 0    |

<img width="750" alt="57" src="https://github.com/sehun98/TIL/assets/100746863/67266bf2-545f-4a00-bd79-70733a8daa00">

<img width="750" alt="58" src="https://github.com/sehun98/TIL/assets/100746863/f8646fbe-aea7-4d43-b36b-354f357823ad">

### 2입력 NAND GATE를 이용한 3입력 NAND GATE

<img width="750" alt="59" src="https://github.com/sehun98/TIL/assets/100746863/4cd3ff58-1703-425a-8d7e-4dfda815ef9e">

| A    | B    | C    | X    |
| ---- | ---- | ---- | ---- |
| 0    | 0    | 0    | 1    |
| 0    | 0    | 1    | 1    |
| 0    | 1    | 0    | 1    |
| 0    | 1    | 1    | 1    |
| 1    | 0    | 0    | 1    |
| 1    | 0    | 1    | 1    |
| 1    | 1    | 0    | 1    |
| 1    | 1    | 1    | 0    |

<img width="750" alt="60" src="https://github.com/sehun98/TIL/assets/100746863/62944bef-7bb6-41a8-b9e7-f3f75b26a3b1">

<img width="750" alt="61" src="https://github.com/sehun98/TIL/assets/100746863/fdf73996-9e33-4132-9f43-fecf463629e2">

<img width="750" alt="62" src="https://github.com/sehun98/TIL/assets/100746863/f39f980f-580c-4e8b-a386-909e67fd415a">



#### 3 input NAND 회로에서 NOT 게이트가 필요한 이유?

다음과 같이 회로를 구성해 3 input NAND 회로를 구성 할 수 있지만 AND + NAND 두 게이트를 사용해야 되기 때문에 또 다른 소자를 사용해야 된다는 단점이 있습니다. 

<img width="400" alt="63" src="https://github.com/sehun98/TIL/assets/100746863/b939c606-6b99-42e4-b917-d90ecad33818">





따라서 같은 NAND로 구성된 회로를 구성하기 위해 NOR의 두 입력 단자를 묶어 NOT 게이트를 만들어 사용합니다. 

<img width="400" alt="64" src="https://github.com/sehun98/TIL/assets/100746863/ad01cebe-ec6c-46ba-8d49-cb1d1374373a">



### NOR GATE

<img width="750" alt="65" src="https://github.com/sehun98/TIL/assets/100746863/3f4b34b3-db78-4f6a-b9f9-8d490b67b027">

| A    | B    | X    |
| ---- | ---- | ---- |
| 0    | 0    | 1    |
| 0    | 1    | 0    |
| 1    | 0    | 0    |
| 1    | 1    | 0    |

<img width="750" alt="66" src="https://github.com/sehun98/TIL/assets/100746863/68e46b5f-15f0-488b-8003-3b4d2617e6dd">

<img width="750" alt="67" src="https://github.com/sehun98/TIL/assets/100746863/4194b3b5-b8c8-4731-a411-e5f1acda0ec9">

상단 실험의 NAND 게이트 실험에서와 같이 NOT 게이트의 기능으로 반전되는 동작을 알 수 있습니다.



### NOR GATE를 이용한 NOT 게이트

<img width="500" alt="68" src="https://github.com/sehun98/TIL/assets/100746863/eeba158a-087b-492d-b724-3d1b60f2ab5b">

| A    | X    |
| ---- | ---- |
| 0    | 1    |
| 1    | 0    |

<img width="750" alt="69" src="https://github.com/sehun98/TIL/assets/100746863/94ad36f2-063f-448b-9eff-24e7807e4631">
<img width="750" alt="70" src="https://github.com/sehun98/TIL/assets/100746863/655732d4-a317-4b1e-bf07-5f7c9c01f522">
NOR 게이트의 입력 두 단자를 묶어 출력을 하면 OR의 기능상 하나 입력만으로도 1이면 1이 출력되기 때문에 없는 것처럼 보입니다. 하지만 OR 게이트와 NOT게이트 두 게이트를 지나기 때문에 Propagation  Delay가 발생한 것을 볼 수 있습니다.



### 2입력 NOR GATE를 이용한 3입력 NOR GATE



<img width="750" alt="71" src="https://github.com/sehun98/TIL/assets/100746863/a87888a5-3f1e-4611-8450-88ddf2f0f95e">

| A    | B    | C    | X    |
| ---- | ---- | ---- | ---- |
| 0    | 0    | 0    | 1    |
| 0    | 0    | 1    | 0    |
| 0    | 1    | 0    | 0    |
| 0    | 1    | 1    | 0    |
| 1    | 0    | 0    | 0    |
| 1    | 0    | 1    | 0    |
| 1    | 1    | 0    | 0    |
| 1    | 1    | 1    | 0    |

<img width="750" alt="72" src="https://github.com/sehun98/TIL/assets/100746863/5bdd781b-34cf-4b94-a45b-edbfee500f13">
<img width="750" alt="73" src="https://github.com/sehun98/TIL/assets/100746863/77c68a55-a159-4669-a1c4-78d8e7f62953">

브레드보드 실험에서는 관찰할 수 없는 Propagation Delay 에 의한 Static-0 Hazard 현상을 OrCAD 실험을 통해 관찰할 수 있습니다. 

## 해저드란? 

입력으로부터 출력까지 다른 경로가 다른 전파 지연을 가져 일어나는 원하지 않는 스위치 과도 현상.



<img width="750" alt="74" src="https://github.com/sehun98/TIL/assets/100746863/b2dc00e7-bf9e-49b3-89b0-5a2793e7d1fc">
<img width="750" alt="75" src="https://github.com/sehun98/TIL/assets/100746863/def198c0-211f-4444-b467-679031e8c5c7">

### 3-상태 버퍼 게이트

<img width="750" alt="76" src="https://github.com/sehun98/TIL/assets/100746863/f8b9f59f-0461-4b39-ad12-94d08a233462">

| \E   | A    | X    |
| ---- | ---- | ---- |
| 0    | 0    | 0    |
| 0    | 1    | 1    |
| 1    | 0    | Hi-Z |
| 1    | 1    | Hi-Z |

<img width="750" alt="77" src="https://github.com/sehun98/TIL/assets/100746863/74121b9d-1d1b-4737-9a16-962621ef8dae">

<img width="750" alt="78" src="https://github.com/sehun98/TIL/assets/100746863/93a9b93a-8419-46a6-a2c2-8e5864e1e613">

## 3-State Buffer를 언제 사용하는가? 

게이트의 출력끼리 묶는 행위를 하고 싶을 경우 오류가 발생하기 때문에 3-State Buffer를 통해 해결할 수 있습니다. 

브레드 보드 실험에서 확인한 Enable 신호를 1 비트로 입력했을 경우 LED가 켜지지 않는 것을 볼 수 있 습니다. 

하지만 OrCAD를 통해 Hi-Z (High Impedance) 상태임을 확인할 수 있습니다.

<img width="450" alt="79" src="https://github.com/sehun98/TIL/assets/100746863/f79d6739-e73c-48ca-aa1e-94ff9afdd32f">

<br>

<br>
