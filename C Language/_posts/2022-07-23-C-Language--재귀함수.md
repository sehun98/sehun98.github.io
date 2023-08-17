---
title: "C Language : 재귀함수"
excerpt: "자신의 함수 내에서 자신을 다시 호출하여 작업을 수행하는 방식"
categories:
  - C Language
---

<br>

<br>

# ⭐ 재귀함수 ⭐

자신의 함수 내에서 **`자신을 다시 호출`**하여 작업을 수행하는 방식으로

반복문으로 복잡하게 짜는 코드를 변수의 사용을 줄여 비교적 쉽게 짤 수 있다는 장점이 있지만

매번 새로운 변수 할당을 하기 때문에 반복문보다 메모리 사용량이 많다. 메모리가 모두 차게 되면 Stack over flow가 일어나게 된다.

종결 조건을 확실하게 하지 않으면 무한 반복이 일어나게 된다.

```c
#include <stdio.h>

int factorial(int n);

int main(void)
{
	int n=10; //scanf

	printf("%d",factorial(n));
	return 0;
}

/*****************************
 *    @brief      : n! = 1 * 2  . . . (n-1) * n
 *    @param      : n number
 *    @return     : int factorial
*****************************/

int factorial(int n)
{
	if(n==1) return 1;
	return n * factorial(n-1);
}
```

<br>

<br>
