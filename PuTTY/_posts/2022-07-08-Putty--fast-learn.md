---
title: "PuTTY : fast learn"
excerpt: "AWS 기반으로 PuTTY 원격 호스트 접속하는 방법에 대해 기술하였습니다."
categories:
  - PuTTY
---

<br>

<br>

SSH는 Secure Shell의 줄임말로, **원격 호스트에 접속하기 위해 사용되는 보안 프로토콜**입니다. (*Shell(쉘): 명령어와 프로그램을 사용할 때 쓰는 인터페이스를 말합니다.

<br>

## pem파일 PPK 전환

### PuTTYgen 실행하기

<img src="/assets/images/post/PuTTY/3.png" width="50%" height="50%" alt="3">

### Conversions > Import key

<img src="/assets/images/post/PuTTY/4.png" width="100%" height="100%" alt="4">

### pem 파일 import

<img src="/assets/images/post/PuTTY/5.png" width="100%" height="100%" alt="5">

### ppk 생성하기

<img src="/assets/images/post/PuTTY/6.png" width="100%" height="100%" alt="6">

<img src="/assets/images/post/PuTTY/7.png" width="100%" height="100%" alt="7">

<br>

## 키(ppk)를 이용한 PuTTY실행

<img src="/assets/images/post/PuTTY/8.png" width="50%" height="50%" alt="8">

### `호스트` , `포트` 입력하기

<img src="/assets/images/post/PuTTY/9.png" width="100%" height="100%" alt="9">

### SSH > Auth ppk 파일 추가하기

<img src="/assets/images/post/PuTTY/10.png" width="100%" height="100%" alt="10">

### 빠른 접속을 위한 Sessions 저장하기

<img src="/assets/images/post/PuTTY/11.png" width="100%" height="100%" alt="11">

### PuTTY접속이 안될 경우 방화벽에 의한 접속 불가를 확인하기

<img src="/assets/images/post/PuTTY/12.png" width="100%" height="100%" alt="12">

<img src="/assets/images/post/PuTTY/13.png" width="50%" height="50%" alt="13">



<br>

<br>
