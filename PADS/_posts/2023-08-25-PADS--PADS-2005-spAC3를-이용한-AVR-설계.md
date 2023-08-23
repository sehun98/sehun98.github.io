---
title: "PADS : PADS 2005 spAC3를 이용한 AVR 설계"
excerpt: "PADS 책을 공부해봅시다."
categories:
  - PADS
---

<br>

<br>

제 2 장 PADS Logic - AVR 회로

2.1 PADS Logic 시작하기

2.2 PADS Logic 화면구조

2.3 PADS Logic 단축키

2.4 Docking 윈도우 제어하기

2.5 화면 확대/축소 하기

## **2.6 AVR 회로도**

<img width="750" alt="184" src="https://github.com/sehun98/TIL/assets/100746863/a9699ef5-c81b-48a8-b1e3-455727c505e4">
<img width="750" alt="185" src="https://github.com/sehun98/TIL/assets/100746863/475ca9d2-1f5c-49f4-94b7-f00e41756d44">

## **2.7 AVR 회로도의 부품표**

<img width="750" alt="186" src="https://github.com/sehun98/TIL/assets/100746863/38e9cb54-ec83-43d8-be48-3e7f6d5d062e">

<img width="750" alt="187" src="https://github.com/sehun98/TIL/assets/100746863/c45908a8-27d9-4018-b8f4-b465a1f363c4">

<img width="750" alt="188" src="https://github.com/sehun98/TIL/assets/100746863/e1778f39-ae69-490f-b6bc-45446ba79357">

<img width="750" alt="189" src="https://github.com/sehun98/TIL/assets/100746863/d21c4c3b-0896-4e88-9572-30e7718cf3bf">

<img width="750" alt="190" src="https://github.com/sehun98/TIL/assets/100746863/b045886f-cdde-45a7-9fe4-fc50c9890d1b">

<img width="750" alt="191" src="https://github.com/sehun98/TIL/assets/100746863/0127fb68-6170-4916-9717-7fdce83a7f7d">

<img width="750" alt="192" src="https://github.com/sehun98/TIL/assets/100746863/607695dd-ee1a-4713-af8c-84226494c065">

제 3 장 회로 부품 만들기

3.1 PADS Library 만들기

3.2 PADS Library 구조

3.3 ATMEGA128 Library 만들기

3.4 7SEG Library 만들기

3.5 SW_PUSHBUTTON Library 만들기

3.6 CON14 Library 만들기

3.7 DC_JACK (TC18-013-01) Library 만들기

3.8 Test_Point Library 만들기

3.9 RES2012 Library 만들기

3.10 CAP2012 부품 외 나머지 부품 등록하기

제 4 장 회로 환경 설정하기

4.1 Option 환경 설정하기

4.2 Color 설정하기

4.3 Sheet 설정하기

제 5 장 회로 부품 배치하기

5.1 Sheet1에 부품 배치하기

5.2 Sheet2에 부품 배치하기

## **5.3 파일 저장하기**

<img width="500" alt="193" src="https://github.com/sehun98/TIL/assets/100746863/30c2b05c-e9c2-44aa-b972-6a200eeffae9">

<img width="500" alt="194" src="https://github.com/sehun98/TIL/assets/100746863/2ac9c5ff-0dd1-4916-98d5-178df622baf5">

제 6 장 신호선 연결하기

6.1 신호선 연결하기

6.2 신호선 수정하기

6.3 신호선 자동으로 연결하기

6.4 Power와 Ground 신호선 연결하기

6.5 Floating 신호선 연결하기

## **6.6 BUS선 만들기**

<img width="60" alt="195" src="https://github.com/sehun98/TIL/assets/100746863/566d3a2f-0ee3-4fc7-a4b7-772dd1289e76">

<img width="750" alt="196" src="https://github.com/sehun98/TIL/assets/100746863/2a7b54d3-2bb4-4a23-8d92-8dac073ddea0">

Bit Format : 순차적으로 표현되는 하나의 어드레스선을 묶어 표현하는 버스선을 말한다.

예) AB[0:5]는 버스에 연결되는 신호선에 AB0~AB5이름이 부여된다.

Mixed Net : 네트이름이 다른 한 개 이상의 어드레스선들을 하나로 묶어 표현하는 버스선을 말한다. 즉 한 개 이상의 Bit Format 버스를 하나로 묶어서 표현한다.



<img width="750" alt="197" src="https://github.com/sehun98/TIL/assets/100746863/0b8e9b55-40a4-4801-a3d5-6a8fa77d4e36">



제 7 장 회로도 수정하기

7.1 부품의 Visibility 수정하기

7.2 동일 부품의 부품값 수정하기

7.3 멀티선택 부품의 부품값 수정하기

7.4 74HC244 부품의 PCB Decal 설정하기

7.5 MAX232 부품의 PCB Decal 설정하기

7.6 파일 저장하기

제 8 장 Netlist 파일 만들기

8.1 Netlist 파일 만들기

제 9 장 Report 만들기

9.1 BOM 데이터 만들기

9.2 Basic Script로 BOM 만들기

9.3 PDF 파일 만들기

제 10 장 PADS Layout - AVR PCB

10.1 PADS Layout 시작하기

10.2 PADS Layout 화면구조

10.3 PADS Layout 단축키

10.4 Docking 윈도우 제어하기

10.5 화면 확대/축소하기

10.6 PCB의 부품리스트

10.7 AVR PCB파일

제 11 장 PCB 부품 만들기

11.1 PADS 부품 만들기

11.2 ATMEGA128 부품 만들기

11.3 7SEG 부품 만들기

11.4 SW_PUSHBUTTON 부품 만들기

11.5 CON14 부품 만들기

11.6 DC_JACK (TC18-013-01) 부품 만들기

11.7 나머지 부품 만들기

제 12 장 Layout 작업 환경 설정하기

12.1 Option 환경 설정하기

12.2 Layer 설정하기

12.3 Design Rule 정의하기

12.4 Start Up 파일 만들기

제 13 장 PCB Boardoutline 만들기

13.1 Start Up 파일 열기

13.2 PCB Boardoutline 만들기

13.3 치수 입력하기

13.4 치수선 디스플레이 off 하기

13.5 파일 저장하기

제 14 장 Netlist 파일 불러오기

14.1 Netlist 파일 불러오기

제 15 장 PCB 부품 배치하기

15.1 부품 이동 방법

15.2 properties로 부품 이동하기

15.3 부품 배치 환경

15.4 부품 배치와 이동 명령

15.5 Find 기능으로 부품 배치하기

15.6 남은 부품 배치하기

15.7 Ref-Des 이동하기

15.8 파일 저장하기

제 16 장 배선하기

16.1 환경 설정하기

16.2 배선 연습하기

16.3 배선 수정하기

16.4 배선하기

16.5 파일 저장하기

제 17 장 Design Rule 체크하기

17.1 Design rule 체크하기

제 18 장 Copper 작성하기

18.1 Copper Pour 작성하기

18.2 Free Via 만들기

## **18.3 Keepout 만들기**

<img width="60" alt="198" src="https://github.com/sehun98/TIL/assets/100746863/bcf42e55-911e-455b-9e3d-6586c8681f7b">
<img width="750" alt="199" src="https://github.com/sehun98/TIL/assets/100746863/9e35703e-403c-4bf8-825a-469537fb4d34">

18.4 Copper Pour 영역 채우기

18.5 파일 저장하기

제 19 장 CAM 파일 만들기

19.1 CAM 폴더 만들기

19.2 CAM Document 만들기

19.3 CAM Documents 파일 (Gerber) 만들기

19.4 파일 저장하기



<br>

<br>
