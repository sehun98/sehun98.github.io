---
title: "C Language : printf()와 scanf()의 이스케이프 시퀀스"
excerpt: ""
categories:
  - C Language
---

<br>

<br>

# ⭐ Call by Value &  Call by Address 선행학습 ⭐

call by value 와 call by address를 학습하기 이전에 printf() 함수와 scanf() 함수를 익숙하게 사용할 줄 알아야 합니다.

그 이유는 다음에 알려주는 것으로 하고, 간단한 형식 지정자와 제어 문자에 대해 알아봅니다.

------

printf는 `hidden const char *format_string`을 넘겨 받아 화면에 출력해주는 기능을 합니다.

hidden const char *format_string이라는 것이 어렵게 느껴질 수 있습니다.

순서대로 이야기를 하자면, `hidden → 숨겨진` `const → 상수` `char  → 문자열` `*format_string → 포인터`라는 뜻으로

문자열(string)이 메모리에 선언되어있고 그 주소 값을 hidden 상태로 printf에 넘겨주는 것입니다.

<br>

`형식 지정자`


| 형식 지정자 | 의미                   | 형식 지정자 | 의미                   | 형식 지정자 | 의미            |
| ----------- | ---------------------- | ----------- | ---------------------- | ----------- | --------------- |
| %d          | 10진 정수              | %f          | float                  | %c          | char            |
| %u          | 양의 10진 정수         | %e          | 0.00e+00               | %s          | string          |
| %o          | 양의 8진 정수          | %a          | 실수를 16진법으로 표현 | %p          | pointer address |
| %x          | 양의 16진 정수(소문자) | %lf         | double                 |             |                 |
| %X          | 양의 16진 정수(대문자) |             |                        |             |                 |
| %lu         | unsigned long          |             |                        |             |                 |
| %ld         | signed long            |             |                        |             |                 |
| %llu        | unsigned long long     |             |                        |             |                 |
| %lld        | signed long long       |             |                        |             |                 |

<br>

`제어 문자` `이스케이프 시퀀스`

| 제어 문자 이름 | 제어 문자 표기 |
| -------------- | -------------- |
| 널문자         | \0             |
| 백스페이스     | \b             |
| 수평 탭        | \t             |
| 줄바꿈         | \n             |
| 수직탭         | \v             |
| 캐리지 리턴    | \r             |
| 역슬래시       | \\             |

<br>

<br>
