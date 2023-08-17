---
title: "C Language : Function Pointer"
excerpt: "struct(구조체), array(배열), enum(열거형), pointer(포인터), function Pointer(함수 포인터)"
categories:
  - C Language
---

<br>

<br>

# ⭐ 함수 포인터 function pointer ⭐

고속 연산이 되어가면서 대용량의 데이터를 처리하기 위해 사용되는 데이터의 구조가 중요하게 되었습니다.

C언어에서 배우는 데이터 구조는 `struct(구조체)`, `array(배열)`, `enum(열거형)`, `pointer(포인터)`, `function Pointer(함수 포인터)`가 있습니다.

------
<br>

```c
#include <stdio.h>
#include <math.h>

double func(double x);
double (*f[4])(double x) = {sin, cos, tan, func};

int main(void)
{
	int i;
	double x = 3.131592/6.0;

	for(i = 0; i<4; i++) printf("%g\\n",f[i](x));
	return 0;
}

double func(double x)
{
	return x * x;
}
```

<br>

<br>
