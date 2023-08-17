---
title: "C Language : 오버플로우와 언더플로우"
excerpt: "싸이의 강남스타일의 유튜브 조회수"
categories:
  - C Language
---

<br>

<br>

## ⭐ 오버플로우와 언더플로우 ⭐

오버플로우는 변수에 대입된 수가 너무 커서 변수가 저장할 수 없는 상황을 의미합니다.

언더플로우는 오버플로우와 반대의 상황이다. 부동 소수점 수가 너무 작아서 표현하기가 힘든 상황이 언더플로우입니다.

대표적인 예제로 싸이의 강남스타일의 유튜브 조회수가 있습니다. (32비트에서 64비트 변경했다고 합니다.)

<br>

![11](https://github.com/sehun98/TIL/assets/100746863/a02acf14-077a-43d7-9fb4-bc2be9d56c51)



```c
#include<stdio.h>

int main()
{
	unsigned char overflow = 256;
	
	printf("output : %d\n", overflow); // output : 0
	return 0;
}
```

<br>

<br>
