---
title: "C Language : sizeof"
excerpt: "자료형이나 변수에 할당되는 메모리의 크기를 바이트 단위로 알려줍니다."
categories:
  - C Language
---

<br>

<br>

# sizeof()

자료형이나 변수에 할당되는 메모리의 크기를 바이트 단위로 알려줍니다.

```c
sizeof(int) // 자료형 int의 크기
sizeof(struct student) // 자료형 struct student의 크기
sizeof(s) // 변수 s의 크기

int a[][5] = {'12345'};
sizeof(a) / sizeof(a[0]) // 2차원 배열의 행의 개수
sizeof(a) / (5*sizeof(int)) // 2차원 배열의 행의 개수

struct student s[] = { . . .};
sizeof(s) / sizeof(struct student) // 구조체 배열 s의 원소 개수
```

<br>

<br>
