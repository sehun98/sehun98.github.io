---
title: "PuTTY : fast learn"
excerpt: "AWS 기반으로 PuTTY 원격 호스트 접속하는 방법에 대해 기술하였습니다."
categories:
  - PuTTY
---

<br>

<br>

PuTTY를 사용해 원격 호스트 접속, 시리얼 포트 접속 등을 할 수 있습니다.



SSH는 Secure Shell의 줄임말로, **원격 호스트에 접속하기 위해 사용되는 보안 프로토콜**입니다. (*Shell(쉘): 명령어와 프로그램을 사용할 때 쓰는 인터페이스를 말합니다.

<br>

## pem파일 PPK 전환

### PuTTYgen 실행하기

<img width="184" alt="3" src="https://github.com/sehun98/TIL/assets/100746863/6e17d0fa-3294-44c1-b303-b4998dce123d">

### Conversions > Import key

<img width="446" alt="4" src="https://github.com/sehun98/TIL/assets/100746863/08f34ef6-c725-45e7-9d2d-b5c83c882346">

### pem 파일 import

<img width="585" alt="5" src="https://github.com/sehun98/TIL/assets/100746863/6e253683-e482-4b78-ad49-1dc84a47af8a">

### ppk 생성하기

<img width="450" alt="6" src="https://github.com/sehun98/TIL/assets/100746863/b3d0f498-5af0-497a-bd57-db14474822cd">
<img width="584" alt="7" src="https://github.com/sehun98/TIL/assets/100746863/9233e5e4-5783-4bcf-9a39-6645c5570575">

<br>

## 키(ppk)를 이용한 PuTTY실행

<img width="181" alt="8" src="https://github.com/sehun98/TIL/assets/100746863/64745e1b-ea7d-4a5f-b99b-fe43711461f0">

### `호스트` , `포트` 입력하기

<img width="336" alt="9" src="https://github.com/sehun98/TIL/assets/100746863/5b34c466-d1a6-4569-a155-55e729e80038">

### SSH > Auth ppk 파일 추가하기

<img width="338" alt="10" src="https://github.com/sehun98/TIL/assets/100746863/de7f0c48-6dbe-461f-8718-da278fa61168">

### 빠른 접속을 위한 Sessions 저장하기

<img width="336" alt="11" src="https://github.com/sehun98/TIL/assets/100746863/8f032e02-4e51-49ed-ae67-19a602009697">

### PuTTY접속이 안될 경우 방화벽에 의한 접속 불가를 확인하기

<img width="492" alt="12" src="https://github.com/sehun98/TIL/assets/100746863/982077c3-2abb-49bd-8e4b-e880ec49dfb4">
<img width="274" alt="13" src="https://github.com/sehun98/TIL/assets/100746863/73b33d60-fdeb-464e-9624-b994752fd869">



<br>

<br>
