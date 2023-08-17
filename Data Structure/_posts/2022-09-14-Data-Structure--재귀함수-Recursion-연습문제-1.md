---
title: "Data Structure : Recursion 재귀함수"
excerpt: "간결하고 명확한 코드를 위한 재귀함수"
categories:
  - Data Structure
---

<br>

<br>

## Recursion

팩토리얼을 구하기 위한 함수

n! = n * (n-1) * (n-2) * . . . * 2 * 1

입력 데이터, 출력 데이터, 종료 조건을 고려해서 설계해야 합니다.

```c
#include <stdio.h>

int factorial(int num);

int main()
{
	int num = 0;

	scanf_s("%d", &num);
	if(num) printf("%d", factorial(num));
	return 1;
}

/*
 * brief : n! = n * (n-1) * (n-2) * . . . * 2 * 1
 * input : 팩토리얼 값 num
 * output : 팩토리얼 결과 result
 * End condition : num == 0
 */
int factorial(int num)
{
	if (num == 0) return 1;
	else return num * factorial(num - 1);
}
```

<br>

<br>
