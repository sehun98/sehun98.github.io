---
title: "C Language : char, short, int, long & float, double"
excerpt: "모든 언어의 시작 데이터 타입"
categories:
  - C Language
---

<br>

<br>

## ⭐ 데이터 타입 ⭐

모든 언어를 시작 할 때에는 데이터 타입이 어떠한 것이 있는지 파악을 해야합니다.

예를 들어 자바의 경우 boolean, string이라는 데이터 타입이 있는 반면, C언어에서는 boolean, string을 사용하지 않고 `0이 아닌 경우 모두 true로 간주합니다.`

특히 C언어에서의 데이터 타입은 비트 단위의 조작을 진행하기 때문에 데이터 타입별 크기도 잘 알아두어야 합니다.

------

### char
<br>

### short

<br>

### int

<br>

### long

<br>

### float

<br>

### double

<br>


## 운영 체제에 따른 데이터 크기

`주의 사항`

**운영체제**의 bit수에 따라 (CPU가 한번에 처리할 수 있는 bit수에 따라) 기준점인 int의 비트 수가 변경이 됩니다.

int의 비트 수가 16bit가 될 수도, 32bit가 될 수도 있기 때문에 컴파일러에서 sizeof(int)를 통한 데이터 타입의 크기를 확인해야 합니다.

C언어 데이터 타입

|        | char    | short      | int  | long |
| ------ | ------- | ---------- | ---- | ---- |
| byte   | 1       | 2          | 4    | 4    |
| bit    | 8       | 16         | 32   | 32   |
| sizeof | 2^8=256 | 2^16=65536 | 2^32 | 2^32 |

|                 | float | double |
| --------------- | ----- | ------ |
| 소수점 유효숫자 | 6자리 | 15자리 |

IEEE 754

![10](https://github.com/sehun98/TIL/assets/100746863/d5638619-c62c-4606-9539-1735c5cc854d)

<br>

<br>
