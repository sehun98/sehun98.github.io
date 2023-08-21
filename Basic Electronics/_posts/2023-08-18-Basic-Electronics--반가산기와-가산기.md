---
title: "Basic Electronics : 반가산기와 가산기"
excerpt: "반가산기와 전가산기를 이해한다."
categories:
  - Basic Electronics
---

<br>

<br>

반가산기와 전가산기를 구현합니다.

전가산기를 이용한 2bit 비교기를 구현합니다.

---

반 가산기 : 한 비트의 2진수를 더하는 가산기

전가산기 : 한 비트의 2진수를 더하는 가산기이며, 캐리 입력을 받을 수 있음

 ### Adder(Half Adder) True Table

<img width="300" alt="109" src="https://github.com/sehun98/TIL/assets/100746863/6c7aecd2-df55-4238-8ab2-9113a177990c">

| X    | Y    | Sum  | Carry |
| ---- | ---- | ---- | ----- |
| 0    | 0    | 0    | 0     |
| 0    | 1    | 1    | 0     |
| 1    | 0    | 1    | 0     |
| 1    | 1    | 0    | 1     |

<img width="750" alt="110" src="https://github.com/sehun98/TIL/assets/100746863/ea9fc2e7-8509-4108-b0d3-cd76f34170c4">

실험 1의 반가산기 회로 결과와 동일하게 2 input 의 상태에 의해 Sum, Carry 의 결과가 나온 것을 알 수 있습니다.

<img width="750" alt="111" src="https://github.com/sehun98/TIL/assets/100746863/968847fc-d7b1-46c9-a911-7296a7d43559">

### 전가산기 구현

<img width="300" alt="112" src="https://github.com/sehun98/TIL/assets/100746863/8f955109-648c-440e-8adf-4d39fb0a708b">

| Ci   | X    | Y    | Sum  | Carry |
| ---- | ---- | ---- | ---- | ----- |
| 0    | 0    | 0    | 0    | 0     |
| 0    | 0    | 1    | 1    | 0     |
| 0    | 1    | 0    | 1    | 0     |
| 0    | 1    | 1    | 0    | 1     |
| 1    | 0    | 0    | 1    | 0     |
| 1    | 0    | 1    | 0    | 1     |
| 1    | 1    | 0    | 0    | 1     |
| 1    | 1    | 1    | 1    | 1     |

<img width="750" alt="113" src="https://github.com/sehun98/TIL/assets/100746863/23fa83c0-21fc-48cf-9d39-87daf7760ec3">



실험 2의 가산기 회로 결과와 동일하게 3 input 의 상태에 의해 Sum, Carry 의 결과가 나온 것을 알 수 있습니다.

<img width="750" alt="114" src="https://github.com/sehun98/TIL/assets/100746863/65fe0812-bc78-47d8-b0ac-5139e896d15f">

#### 실험 결과 분석 및 고찰 

반가산기와 가산기를 왜 배우는가에 대해서 고찰해 보도록 하겠습니다. CPU, 마이크로프로세서에 내장되는 Arithmetic and Logic Unit 일명 ALU 는 산술 연산과 논리 연산으로 구성됩니다. 내부 part 는 이번 실험에서 배운 바와 같이 가산기(Adder)가 포함됩니다.

내부 장치

| 가산기 (Adder)        | 산술 연산을 수행하는 회로, 두 개이상의 수의 합을 계산하는 논리 회로 |
| --------------------- | ------------------------------------------------------------ |
| 보수기 (Complementer) | 뺄셈을 사용할 때 사용하는 보수를 만들어주는 논리 회로        |
| 시프터 (Shifter)      | 2진수의 각 자리를 왼쪽 또는 오른쪽으로 이동해주는 회로       |
| 오버플로우 (Overflow) | 산술기의 결과가 해당 레지스터의 용량을 초과했을 때를 검출해주는 회로 |

레지스터 (Register)

| 누산기 (Accumulator)                          | 산술과 논리연산의 중간 값을 임시적으로 보관하기 위한 레지스터 |
| --------------------------------------------- | ------------------------------------------------------------ |
| 저장 레지스터 (Storage Register)              | 주기억 장치로 보내는 데이터를 임시적으로 저장하는 레지스터   |
| 데이터 레지스터 (Data Register)               | 연산을 위한 데이터를 임시적으로 기억하는 레지스터            |
| 상태 레지스터 (Status Register)               | 산술과 논리 연산의 결과로 나오는 캐리, 부호, 오버플로우 등의 상태를 기억하는 레지스터 |
| 인덱스 레지스터 (Index Register)              | 명령 주소를 수정하거나 색인 주소를 지정할 때 사용하는 레지스터 |
| 부동소수점 레지스터 (Floating Point Register) | 부동소수점 연산에 사용되는 레지스터                          |



반가산기과 전가산기와의 차이점 

반가산기는 간단하게 보면 input 2개, output 2개 (Carry, Sum)으로 구성되고 가산기는 input 3개, output  2개 (Carry, Sum)으로 구성됩니다. 반가산기에서는 자리 올림 수행을 하지 못하지만 가산기를 3 input 으로 이전 값의 자리 올림을 수행하기 위해 OR gate 를 이용합니다. 따라서 반가산기의 경우 LSB (Least Significant bit) 1비트의 데이터에서만 논리 연산을 수행하고 가산기의 경우 이전 값의 자리 올림에 대한 논리 연산이 가능하기 때문에 모든 비트에서 수행합니다. 임베디드 시스템에서 사용하는 AVR 8비트, cortext 32비트 등의 연산을 수행하기 위해서는 전가산기의 논리 연산이 필요합니다

<img width="750" alt="115" src="https://github.com/sehun98/TIL/assets/100746863/253cb922-3807-49d0-b9cc-90ccd9b31388">



File > New > Verilog HDL File 

File > New > University Program VWF 

Edit > Insert > Insert Node … 

Tools > Net Viewer > Technology Map Viewer

<img width="750" alt="116" src="https://github.com/sehun98/TIL/assets/100746863/7902b150-212f-4433-b92c-08489bc3ec59">





<br>

<br>
