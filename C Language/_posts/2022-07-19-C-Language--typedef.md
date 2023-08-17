---
title: "C Language : typedef"
excerpt: "데이터를 내맘대로"
categories:
  - C Language
---

<br>

<br>

# ⭐ code refectoring typedef ⭐

다음과 같이 매번 데이터 타입을 선언해야 하는 것을 줄여 줄 수 있습니다.

```c
#include <stdio.h>

struct _student{
	int age;
	char name[100];
};

int main(){
	struct _student student;
	
	student.age = 1;
	
	return 0;
}
```

다음과 같이 새로운 타입을 선언 할 수 있습니다.

```c
typedef int vector[10];

vector a;
typedef struct { double x, y;} Point;

Point p,q;
```

<br>

<br>
