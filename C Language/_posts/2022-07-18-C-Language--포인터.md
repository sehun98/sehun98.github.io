---
title: "C Language : 포인터"
excerpt: "struct(구조체), array(배열), enum(열거형), pointer(포인터), function Pointer(함수 포인터)"
categories:
  - C Language
---

<br>

<br>

# ⭐ 포인터 pointer ⭐

고속 연산이 되어가면서 대용량의 데이터를 처리하기 위해 사용되는 데이터의 구조가 중요하게 되었습니다.

C언어에서 배우는 데이터 구조는 `struct(구조체)`, `array(배열)`, `enum(열거형)`, `pointer(포인터)`, `function Pointer(함수 포인터)`가 있습니다.

<br>

포인터란 무엇이고 포인트를 사용하는 이유는 무엇일까요?

우선 저희는 데이터 타입에 대해서 학습을 진행했습니다.

`char` , `short`, `int` , `long` , `float` , `double`

이때 char를 기준으로 데이터 크기는 `-128~127` 입니다.

stack 영역에서 데이터를 확인해 보겠습니다.

```c
char a[100] = {0};
```

| pointer | Symbolic Address | Value |
| ------- | ---------------- | ----- |
|         | a[99]            | 0     |
|         | . . .            |       |
|         | a[1]             | 0     |
| a       | a[0]             | 0     |

<br>

포인터란 말 그대로 데이터를 가르키는 것입니다.

포인터는 가르키고 있는 주소를 값으로 넣어 8bit로 모두 동일한 크기를 가지지만,

타입 지정을 해줘야 하는 이유는 가르키고 있는 대상의 자료형 크기만큼 증가/감소를 진행해야하기 때문입니다.

```cpp
int *pointer;
pointer + 1 = 1; // 포인터를 이동할 때 그 거리를 알기 위함
```

<br>

포인터는 배열과 매우 유사한 성격을 가지고 있습니다.

배열에서의 배열명은 첫 번째 앨리먼트의 주소값을 나타냅니다. 이 말은 즉, 배열에서의 배열명은 포인터라는 뜻 입니다.

하지만 포인터와 배열은 엄연히 다릅니다.

포인터는 +, -를 통해 데이터 접근을 하지만 배열은 인덱스를 통해 데이터를 접근하여 효율이 떨어지는 상황이 있을 수 있습니다.

배열은 인덱스 번호만 있으면 접근이 가능해서 효율이 좋은 상황이 있을 수 있다.

배열은 치환과 비교가 안되고 구조체는 치환은 가능하나 비교는 불가능 합니다.

------

## 포인터를 정확하게 학습하기 위해서는 Linked List를 그려보고 구현하는 연습을 진행합니다.

![13](https://github.com/sehun98/TIL/assets/100746863/7e5552b8-cfa1-4f01-9cd8-08373d3121c8)


```cpp
#include <stdio.h>

int main(void)
{
	int data = 1;
	int** phead;
	int* head;

	head = &data;
	phead = &head;

	printf("%d\\n", *phead);
	printf("%d\\n", head);
	printf("%d\\n", &data);

	printf("%d\\n", phead);
	printf("%d\\n", &head);

	printf("%d\\n", **phead);
	printf("%d\\n", data);

	return 0;
}
```

<br>

<br>
