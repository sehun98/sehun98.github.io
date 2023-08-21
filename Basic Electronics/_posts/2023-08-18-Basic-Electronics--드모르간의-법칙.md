---
title: "Basic Electronics : 드모르간의 법칙"
excerpt: "DeMorgan's themorem을 이용하여 응용 문제를 해결하는 방법을 알아보자."
categories:
  - Basic Electronics
---

<br>

<br>

NAND, NOR Gate의 진리표를 이해한다.

NAND, NOR Gate의 특징인 DeMorgan’s theorem을 이해하고 구현하다.

DeMorgan’s theorem을 이용하여 응용 문제를 해결하고 구현한다.

---

### NAND 논리

<img width="450" alt="80" src="https://github.com/sehun98/TIL/assets/100746863/d9c05926-e8e3-4410-a8a9-272bd19e0715">

| A          | B          | Y    |
| ---------- | ---------- | ---- |
| Low (GND)  | Low (GND)  | 1    |
| Low (GND)  | High (VCC) | 1    |
| High (VCC) | Low (GND)  | 1    |
| High (VCC) | High (VCC) | 0    |

<img width="750" alt="81" src="https://github.com/sehun98/TIL/assets/100746863/828a1788-6b8a-40d0-af09-501949185530">

### NAND Gate Using DeMorgan's theorem

<img width="450" alt="86" src="https://github.com/sehun98/TIL/assets/100746863/6c60af7f-121a-4eda-8329-df6bc48ec17c">

<img width="750" alt="89" src="https://github.com/sehun98/TIL/assets/100746863/a0199bb3-c146-4651-abef-2f7aafa1bec9">

| A          | B          | Y    |
| ---------- | ---------- | ---- |
| Low (GND)  | Low (GND)  | 1    |
| Low (GND)  | High (VCC) | 1    |
| High (VCC) | Low (GND)  | 1    |
| High (VCC) | High (VCC) | 0    |

#### Figure 1과 Figure 2의 동작이 동일한가? 그 이유에 대해 방정식으로 설명하시오. 

Figure 1의 진리식과 Figure 2의 진리식은 하기의 식과 같습니다. 따라서 DeMorgan's theorem 에 의해 Figure 2의 진리식은 Figure 1과 같아지게 됩니다. 즉, DeMorgan's theorem 첫번째 A · Ｂ의 보수 취한 것이 A 의 보수와 B 의 보수와 합한 것과 같습니다

<img width="750" alt="82" src="https://github.com/sehun98/TIL/assets/100746863/a0cbf2c6-f0a8-4c87-aeaa-a6200144df95">

OrCAD 시뮬레이션에서도 마찬가지로 같은 결과가 나오는 것을 볼 수 있습니다

<img width="750" alt="83" src="https://github.com/sehun98/TIL/assets/100746863/939c8b45-b724-41aa-ba21-643301f67080">

#### OrCAD 출력에서 나오는 ?? 현상은 무엇일까?

Time 을 늘려서 다음 신호에서도 동일한 현상이 나타나는지 확인해본 결과 의문의 신호가 사라지는 것을 볼 수 있었습니다. 따라서 의문의 신호는 <b>Sampling Time 이 적절하지 않아서 발생한 현상</b>인 것임을 알 수 있었습니다

---



### NOR Gate

<img width="450" alt="87" src="https://github.com/sehun98/TIL/assets/100746863/572b901f-5073-4bba-b467-2de623a641e1">

<img width="750" alt="84" src="https://github.com/sehun98/TIL/assets/100746863/1dc14c42-42d2-4387-b5d1-51110f2d14be">

| A          | B          | Y    |
| ---------- | ---------- | ---- |
| Low (GND)  | Low (GND)  | 1    |
| Low (GND)  | High (VCC) | 0    |
| High (VCC) | Low (GND)  | 0    |
| High (VCC) | High (VCC) | 0    |



---

 ### NOR Gate using DeMorgan's theorem

<img width="450" alt="88" src="https://github.com/sehun98/TIL/assets/100746863/4604c972-caf6-4b8e-b848-9f5c3e18ede9">

<img width="450" alt="90" src="https://github.com/sehun98/TIL/assets/100746863/ca602705-31c5-4e5c-8c5b-38bef1671e8a">

| A          | B          | Y    |
| ---------- | ---------- | ---- |
| Low (GND)  | Low (GND)  | 1    |
| Low (GND)  | High (VCC) | 0    |
| High (VCC) | Low (GND)  | 0    |
| High (VCC) | High (VCC) | 0    |

#### Figure 3과 Figure 4의 동작이 동일한가? 그 이유에 대해 방정식으로 설명하시오. 

Figure 3의 진리식과 Figure 4의 진리식은 다음과 같습니다. 따라서 DeMorgan's theorem 에 의해 Figure  4의 진리식은 Figure 3과 같아지게 됩니다. 즉, DeMorgan's theorem 두번째 A + Ｂ의 보수 취한 것이 A 의 보수와 B 의 보수와 곱한 것과 같습니다.

<img width="750" alt="85" src="https://github.com/sehun98/TIL/assets/100746863/631b73e4-3634-42c8-b206-fb2376f92d7b">

OrCAD 시뮬레이션에서도 마찬가지로 같은 결과가 나오는 것을 볼 수 있습니다

<img width="750" alt="91" src="https://github.com/sehun98/TIL/assets/100746863/bf489f9d-2132-4d14-932e-077c3558c599">



### Sum-of-products implement

<img width="450" alt="92" src="https://github.com/sehun98/TIL/assets/100746863/4e21ab66-56e4-40f6-8cd0-e844768b7f0f">

<img width="750" alt="96" src="https://github.com/sehun98/TIL/assets/100746863/5499931a-f7cb-4e73-8a26-a7dbbca57b5f">

| A          | B          | C          | Y    |
| ---------- | ---------- | ---------- | ---- |
| Low (GND)  | Low (GND)  | Low (GND)  | 0    |
| Low (GND)  | Low (GND)  | High (VCC) | 0    |
| Low (GND)  | High (VCC) | Low (GND)  | 1    |
| Low (GND)  | High (VCC) | High (VCC) | 0    |
| High (VCC) | Low (GND)  | Low (GND)  | 1    |
| High (VCC) | Low (GND)  | High (VCC) | 1    |
| High (VCC) | High (VCC) | Low (GND)  | 1    |
| High (VCC) | High (VCC) | High (VCC) | 1    |

### NAND Gates implement

<img width="450" alt="93" src="https://github.com/sehun98/TIL/assets/100746863/4d9b54b2-1b6b-4ede-8e94-ea805ab42387">

<img width="750" alt="97" src="https://github.com/sehun98/TIL/assets/100746863/225a121f-cedc-44c2-a0d5-9bd8b27eef31">

<img width="750" alt="98" src="https://github.com/sehun98/TIL/assets/100746863/c0f8f501-9844-41c8-b431-bc417040195c">

| A          | B          | C          | Y    |
| ---------- | ---------- | ---------- | ---- |
| Low (GND)  | Low (GND)  | Low (GND)  | 0    |
| Low (GND)  | Low (GND)  | High (VCC) | 0    |
| Low (GND)  | High (VCC) | Low (GND)  | 1    |
| Low (GND)  | High (VCC) | High (VCC) | 0    |
| High (VCC) | Low (GND)  | Low (GND)  | 1    |
| High (VCC) | Low (GND)  | High (VCC) | 1    |
| High (VCC) | High (VCC) | Low (GND)  | 1    |
| High (VCC) | High (VCC) | High (VCC) | 1    |

#### Figure 5와 Figure 6의 동작이 동일한가? 그 이유에 대해 방정식으로 설명하시오. 

Figure 5의 진리식과 Figure 5의 진리식은 다음과 같습니다. 따라서 DeMorgan's theorem 에 의해 Figure  5의 진리식은 Figure 6과 같아지게 됩니다.

<img width="750" alt="99" src="https://github.com/sehun98/TIL/assets/100746863/7fc72284-9729-495f-abfd-593d2bdd5a56">

OrCAD 시뮬레이션에서도 마찬가지로 같은 결과가 나오는 것을 볼 수 있습니다.

<img width="750" alt="100" src="https://github.com/sehun98/TIL/assets/100746863/4f87158f-7835-4eda-b79e-c0ebdad451e9">

<img width="750" alt="101" src="https://github.com/sehun98/TIL/assets/100746863/b06b3874-eaed-4b6f-ae5c-509dea74ce1c">

### Product-of-sums implement

<img width="450" alt="94" src="https://github.com/sehun98/TIL/assets/100746863/0e425559-dd61-4d5b-be8e-cb74e98f518f">

| A          | B          | C          | Y    |
| ---------- | ---------- | ---------- | ---- |
| Low (GND)  | Low (GND)  | Low (GND)  | 0    |
| Low (GND)  | Low (GND)  | High (VCC) | 0    |
| Low (GND)  | High (VCC) | Low (GND)  | 1    |
| Low (GND)  | High (VCC) | High (VCC) | 1    |
| High (VCC) | Low (GND)  | Low (GND)  | 1    |
| High (VCC) | Low (GND)  | High (VCC) | 0    |
| High (VCC) | High (VCC) | Low (GND)  | 1    |
| High (VCC) | High (VCC) | High (VCC) | 1    |



<img width="750" alt="102" src="https://github.com/sehun98/TIL/assets/100746863/5f6ad970-88e3-438c-9646-3c1852ddff89">

<img width="750" alt="103" src="https://github.com/sehun98/TIL/assets/100746863/8f8cda27-571e-4367-8305-75d15d85882d">

### NOR Gates implement

<img width="450" alt="95" src="https://github.com/sehun98/TIL/assets/100746863/f17160e7-13f5-4f6b-9a8d-3684a71e2a23">

| A          | B          | C          | Y    |
| ---------- | ---------- | ---------- | ---- |
| Low (GND)  | Low (GND)  | Low (GND)  | 0    |
| Low (GND)  | Low (GND)  | High (VCC) | 0    |
| Low (GND)  | High (VCC) | Low (GND)  | 1    |
| Low (GND)  | High (VCC) | High (VCC) | 1    |
| High (VCC) | Low (GND)  | Low (GND)  | 1    |
| High (VCC) | Low (GND)  | High (VCC) | 0    |
| High (VCC) | High (VCC) | Low (GND)  | 1    |
| High (VCC) | High (VCC) | High (VCC) | 1    |






<img width="750" alt="104" src="https://github.com/sehun98/TIL/assets/100746863/7e57a600-694a-4430-8211-9be43258d7fa">

#### Figure 7과 Figure 8의 동작이 동일한가? 그 이유에 대해 방정식으로 설명하시오. 

Figure 7의 진리식과 Figure 8의 진리식은 다음과 같습니다. 따라서 DeMorgan's theorem 에 의해 Figure  5의 진리식은 Figure 7과 같아지게 됩니다.

<img width="300" alt="105" src="https://github.com/sehun98/TIL/assets/100746863/d141377e-8b91-4dce-afa8-74c6bb7c38bc">

<img width="450" alt="106" src="https://github.com/sehun98/TIL/assets/100746863/9ac7278d-6be6-4893-9e81-abeac4339497">

OrCAD 시뮬레이션에서도 마찬가지로 같은 결과가 나오는 것을 볼 수 있습니다.

<img width="750" alt="107" src="https://github.com/sehun98/TIL/assets/100746863/b0350095-4d38-44c2-9a22-2d4b2c371f23">

### 실험에 대한 분석 및 고찰

DeMorgan’s theorem는 수리 논리학이나 집합론, 컴퓨터과학 등에서 집합의 관계를 정리한 것으로 전자 공학 분야에서 논리연산에 주로 사용이 된다고 합니다. 이 DeMorgan’s theorem을 이용해 FPGA라는 복잡 한 논리 구조를 통해 Field Programmable Gate Array를 논리 소자와 프로그래밍이 가능한 반도체 소자로 만듭니다. 주로 FPGA는 노이즈에 강한 특성을 가져 DSP, 우주 및 방산, 차량등에 많이 사용되고 의공학 적으로는 의료 영상 및 컴퓨터 비전, 암호학에서 주로 사용하고 있습니다. VHDL이라는 하드웨어 기술 언 어를 사용하는데 이를 통해 netlist가 생성이 되고 주요 성능 지표로는 마이크로프로세서의 시간 복잡도, 공간 복잡도가 아닌 논리 블록의 수로 평가가 되는 것으로 알고 있습니다. 이는 마이크로프로세서와 다르 게 한번에 병렬적인 실행 체계가 있기 때문입니다. 따라서 압도적인 계산 속도를 가질 수 있습니다.



#### FPGA 설계를 위한 Quartus 2 Verilog를 통해 검증을 진행해 보았습니다.

결론적으로 다른 진리식 ( Verilog Code )로 설계를 진행하였을 때 Simulation 결과와 NetList 가 똑같게 반도체가 설계되어 추출되는 것을 알 수 있습니다.

<img width="750" alt="108" src="https://github.com/sehun98/TIL/assets/100746863/b7f87c02-a6fe-4e89-ba7c-08c901863c2d">

<br>

<br>
