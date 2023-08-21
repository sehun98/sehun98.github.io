---
title: "Basic Electronics : 디지털공학 요약"
excerpt: "조합 논리 회로와 순서 논리 회로에 대해 요약합니다."
categories:
  - Basic Electronics
---

<br>

<br>

데이터 Resister (플립플롭)에 저장되었다가 MUX를 거쳐 ALU로 전달되고, DeMUX를 거쳐 출력됩니다.

이때 데이터가 Resister로 전달 될 때 적절한 위치에 저장하기 위해 디코더를 거칩니다.

<img width="750" alt="236" src="https://github.com/sehun98/TIL/assets/100746863/de3ae683-4421-4d03-a8a2-d9699642cbaf">



1. 코드와 비트
   BCD 코드
   3초과 코드
   그레이 코드
   ASCII 코드
   패리티 코드
   병렬 패리티 비트

2. 조합 논리 회로
   불의 대수
   드모르간의 법칙
   카르노맵
   퀸-맥클러스키
   AND, OR, Buffer, NOT, XOR

   3-State

   transmission Gate
   MUX, DeMUX

   디코더, 인코더

   반가산기, 가산기
   
3. High Speed Digital
   Propagation Delay
   Static/Dynamic hazard

   hazard free function

   

4. 순차 논리 회로
   래치와 플립플롭

   SR Flip-Flop
   JK Flip-Flop
   T Flip-Flop
   D Flip-Flop

   Tri-state Buffer



### BCD 코드 (Binary Coded Dicimal Code)

BCD 코드는 1010부터 1111까지는 6개는 사용하지 않습니다.

| Decimal | BCD Code |
| ------- | -------- |
| 0       | 0000     |
| 1       | 0001     |
| 2       | 0010     |
| 3       | 0011     |
| 4       | 0100     |
| 5       | 0101     |
| 6       | 0110     |
| 7       | 0111     |
| 8       | 1000     |
| 9       | 1001     |



### 3초과 코드 (excess 3 code)

BCD 코드에 +3 더하여 나타낸 코드로 자기 보수의 성질을 가지며 현재값에서 1의 보수를 취하면 10진수에서 9의 보수에 해당되는 값이 됩니다.

| Decimal | BCD Code | ecess 3 code |
| ------- | -------- | ------------ |
| 0       | 0000     | 0011         |
| 1       | 0001     | 0100         |
| 2       | 0010     | 0101         |
| 3       | 0011     | 0110         |
| 4       | 0100     | 0111         |
| 5       | 0101     | 1000         |
| 6       | 0110     | 1001         |
| 7       | 0111     | 1010         |
| 8       | 1000     | 1011         |
| 9       | 1001     | 1100         |



### 그레이 코드

최상위 비트(MSB)는 그대로 쓰고 앞 비트와 다음 비트를 비교하여 같으면 0. 다르면 1을 내려씁니다.

| Decimal | BCD Code | ecess 3 code | Gray Code |
| ------- | -------- | ------------ | --------- |
| 0       | 0000     | 0011         | 0000      |
| 1       | 0001     | 0100         | 0001      |
| 2       | 0010     | 0101         | 0011      |
| 3       | 0011     | 0110         | 0010      |
| 4       | 0100     | 0111         | 0110      |
| 5       | 0101     | 1000         | 0111      |
| 6       | 0110     | 1001         | 0101      |
| 7       | 0111     | 1010         | 0100      |
| 8       | 1000     | 1011         | 1100      |
| 9       | 1001     | 1100         | 1101      |

<img width="400" alt="237" src="https://github.com/sehun98/TIL/assets/100746863/2d258900-3b3f-4407-b941-0e5b83e661c5">



### ASCII 코드 (American Standard Code for Information Interchange)

| 10진수 | 16진수 | 문자 |
| ------ | ------ | ---- |
| 0      | 0x00   | NULL |
| 1      | 0x01   | SOH  |
| 2      | 0x02   | STX  |
| 3      | 0x03   | ETX  |



### 패리티 비트

데이터 전송 과정에 오류가 있는지 검사하기 위한 추가 비트

그러나 단지 오류 검사 기능만 존재하기 때문에 어느 부분의 오류인지 파악하기 위해 병렬 패리티를 사용합니다.



### 병렬 패리티 (Parallel Parity)

<img width="500" alt="238" src="https://github.com/sehun98/TIL/assets/100746863/98522f29-0f89-4cfe-bfe3-7e2a9ef1e8ee">



### 해밍 코드

패리티 코드를 응용해서 오류를 정정할 수 있는 코드



### 순차 논리 회로

출력이 현재 입력과 이전의 논리 회로 상태의 조합에 의해 결정되는 논리 회로

레지스터, 래치, 플립플롭

<img width="300" alt="239" src="https://github.com/sehun98/TIL/assets/100746863/cf5ca3d1-9f7d-4971-b473-dc6d788f6846">



### 조합 논리 회로

게이트의 조합으로 출력이 나오는 회로

게이트, 가산기, 멀티 플렉서, ALU

<img width="300" alt="240" src="https://github.com/sehun98/TIL/assets/100746863/a804a3ae-b921-44ee-af00-dbf89a19a2b8">



### 불의 대수

<img width="500" alt="241" src="https://github.com/sehun98/TIL/assets/100746863/ff5cba82-a469-4dee-bc81-d09996324448">



### 드모르간의 법칙

<img width="200" alt="242" src="https://github.com/sehun98/TIL/assets/100746863/4d3bd9d1-964f-4d60-aea9-fa8cae53b43e">









### 카르노맵

<img width="300" alt="243" src="https://github.com/sehun98/TIL/assets/100746863/9ee4a195-3384-4c9e-9f8a-385505772397">



### 최소항의 논리 합

<img width="300" alt="244" src="https://github.com/sehun98/TIL/assets/100746863/42f50385-b703-460d-85dc-3c8cc53d166a">

<img width="300" alt="245" src="https://github.com/sehun98/TIL/assets/100746863/ed52860a-9825-47a9-a976-9b146377b6c7">



### 최대항의 논리 곱



### 입력이 5개 이상일 경우 퀸-맥클러스키 사용



### Logic 데이터 시트 읽는법

<img width="500" alt="246" src="https://github.com/sehun98/TIL/assets/100746863/0713441b-b3d1-4be1-ad50-d420b4361184">



### 해저드

입력으로 부터 출력까지 다른 경로가 다른 전파 지연을 가져 일어나는 원하지 않는 스위치 과도 현상

정적 1-해저드 (Static 1-hazard)

<img width="200" alt="247" src="https://github.com/sehun98/TIL/assets/100746863/2feb9456-ecdd-4633-94cb-dc3354c31894">

정적 0-해저드 (Static 0-hazard)

<img width="200" alt="248" src="https://github.com/sehun98/TIL/assets/100746863/28c86bce-a6c2-4245-8891-864660618103">

동적 해저드 (Dynamic hazard)

<img width="200" alt="249" src="https://github.com/sehun98/TIL/assets/100746863/c8cd4328-468f-4367-8313-61cd5b741164">

### Propagation Delay에 의한 스위치 과도 현상

<img width="750" alt="250" src="https://github.com/sehun98/TIL/assets/100746863/fb50b45e-0380-49bd-85b2-bcc4b1e85703">





<br>

<br>
