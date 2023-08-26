---
title: "FPGA Project : FPGA 부품 만들기"
excerpt: "PCB 설계를 위한 FPGA 부품 라이브러리 만들기"
categories:
  - FPGA Project
---

<br>

<br>

XC7S50_2CSGA324C -> XC7Z010_2CSGA400I 부품 변경



### FPGA 부품 만들기

#### pinout 검색

<img width="750" alt="1" src="https://github.com/sehun98/TIL/assets/100746863/499132d6-e237-4dd0-b2ae-54c75cec6660">

데이터 시트에서 ctrl + f로 pinout을 바로 찾아봅니다.

<img width="300" alt="2" src="https://github.com/sehun98/TIL/assets/100746863/5f93929a-bee5-48c3-90df-f121cbc81073">

pinout files

<img width="750" alt="3" src="https://github.com/sehun98/TIL/assets/100746863/a87ef06d-f856-4487-81eb-4b34ee0e3fce">

pinout 파일을 다운로드 받습니다.

<img width="750" alt="4" src="https://github.com/sehun98/TIL/assets/100746863/953dd12e-bbd9-4937-bbda-10dc3e84c830">

가공되지 않은 파일을 가공할 준비를 합니다.

<img width="750" alt="5" src="https://github.com/sehun98/TIL/assets/100746863/2fce9268-e7bc-42eb-a07e-2bdf81f7aea6">

Bank, pin, pin Name 순으로 정리를 합니다.

<img width="300" alt="6" src="https://github.com/sehun98/TIL/assets/100746863/29a41f94-c5f6-497f-b92c-12445cc9fe91">

Bank 별로 분배합니다.

<img width="750" alt="7" src="https://github.com/sehun98/TIL/assets/100746863/45e4111c-8b7d-46eb-9d30-252942ded7a4">

Bank 별 분배 및 전원 별 분배로 적절한 핀 배치를 합니다.

<img width="750" alt="8" src="https://github.com/sehun98/TIL/assets/100746863/0024880f-de8c-4bd1-a620-cb09e678e812">

#### Logic 만들기

Layout에 들어가 Gate를 만들어줍니다.

<img width="750" alt="9" src="https://github.com/sehun98/TIL/assets/100746863/fef072b2-364f-48d4-8f23-7e4f5983b478">



<img width="750" alt="10" src="https://github.com/sehun98/TIL/assets/100746863/ed873181-abce-45c3-9ece-9e516e609756">

Gate를 추가합니다.

<img width="750" alt="11" src="https://github.com/sehun98/TIL/assets/100746863/475f5b81-eaa5-4b2e-b10d-10db41a541f3">



<img width="750" alt="12" src="https://github.com/sehun98/TIL/assets/100746863/d5c8aa2b-ada9-4c77-9c12-f13b3706d4c8">

엑셀 파일로 부터 붙혀넣기 합니다.

<img width="750" alt="13" src="https://github.com/sehun98/TIL/assets/100746863/54106f69-aa06-421d-a206-f0d07f21db1f">

Save As 저장합니다.

<img width="750" alt="14" src="https://github.com/sehun98/TIL/assets/100746863/02346c57-eaf1-441e-af91-88a1113dff32">

#### Layout 만들기 및 연결을 진행합니다.

<img width="750" alt="15" src="https://github.com/sehun98/TIL/assets/100746863/92ec8fca-f88d-44cb-9586-e2ec614a2877">
<img width="750" alt="16" src="https://github.com/sehun98/TIL/assets/100746863/2a74293d-5f3b-44e2-ae3a-25a9d6803445">









<br>
<br>

