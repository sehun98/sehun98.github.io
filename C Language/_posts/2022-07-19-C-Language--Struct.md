---
title: "C Language : Struct"
excerpt: "struct(구조체), array(배열), enum(열거형), pointer(포인터), function Pointer(함수 포인터)"
categories:
  - C Language
---

<br>

<br>

# ⭐ 구조체 struct ⭐

고속 연산이 되어가면서 대용량의 데이터를 처리하기 위해 사용되는 데이터의 구조가 중요하게 되었습니다.

C언어에서 배우는 데이터 구조는 `struct(구조체)`, `array(배열)`, `enum(열거형)`, `pointer(포인터)`, `function Pointer(함수 포인터)`가 있습니다.

이번 페이지에서는 `struct(구조체)`에 대해 알아보겠습니다.

동일 데이터를 하나의 이름으로 추상화 하는 array와 다르게 잡종 데이터를 하나의 이름으로 추상화 하는 struct입니다.

<img src="/assets/images/post/C Language/9.png" width="75%" height="75%" alt="9">

그림을 보면서 직관적으로 생각하시면 될 것 같습니다.

하나의 데이터만 입출력 하기보다는 여러가지의 데이터를 입출력하기 위해 상자에 묶는다라는 개념을 생각하시면 됩니다.

구조체 맴버 접근

함수에서 구조체를 선언 할 경우 구조체명을 통해 직접 접근이 가능하지만 구조체의 주소를 넘겨주는 Call by Address의 경우 (*구조체명)을 통해 멤버에 접근을 해야합니다.

[member.name](http://member.name);

(*member).name;

member→name;

------

☑️ 구조체 전역에서 `타입`을 정의 (아직 선언되지 않은 상태)

```cpp
typedef struct _node {
	int id;
	char name[10];
	int* _node;
};
```

☑️ 위 조건에 의한 구조체 선언

```cpp
int main()
{
	struct _node node;	

	return 0;
}
```

☑️ 지역변수로 구조체 정의와 동시에 선언

```cpp
int main()
{
	struct _node {
		int id;
		char name[10];
		int* _node;
	}node;

	node.id = 1;

	return 0;
}
```

☑️ 구조체 복사(배열은 포인터를 나타내기 때문에 불가능한 기능)

```cpp
#include <stdio.h>

struct _struCopy {
    int x;
    int y;
};

int main()
{
    struct _struCopy struCopy = { 1, 2 };
    struct _struCopy struCopy2;

    struCopy2 = struCopy;

    /*
        struCopy2.x = struCopy.x;
        struCopy2.y = struCopy.y;
    */

    printf("%d, %d\\n", struCopy2.x, struCopy2.y);
    
    return 0;
}
```

<br>

<br>
