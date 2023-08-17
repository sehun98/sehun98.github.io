---
title: "C Language : auto, static, extern, const, final(java)"
excerpt: "데이터 타입과 메모리 영역의 깊은 이해를 해봅니다."
categories:
  - C Language
---

<br>

<br>

# ⭐ auto, static, extern, const, final(java) ⭐

앞서 데이터 타입과 메모리 영역에 대해서 알아보았습니다. 이때 설명 하지 않은 부분에 대해서 설명 하겠습니다.

`int a = 0;` 은 사실 `auto int a = 0;` 에서 auto가 생략된 코드입니다.

기본적으로 데이터 타입은 stack 영역에 할당 되도록 구성되어 있습니다.

따라서 static(정적 변수) 메모리 영역에 데이터를 할당하고 싶다면 `static int a = 0;` 과 같이 작성해 주어야 합니다.

그러면 static영역에 할당을 해주어야 하는 이유는 무엇일까요?

auto의 지역변수 : 함수 내에서만 메모리 할당 후 해제

auto의 전역변수 : 함수 외부에서 메모리 할당되어 프로그램이 끝날 때 해제

static의 지역변수 :  static 특성 상 한번의 선언과 초기화를 진행하기 때문에 아래 코드와 같은 효과가 나타납니다.

static의 전역변수 :  다른 파일에서는 접근이 불가능 하지만 같은 소스 파일 내의 함수는 접근이 가능

------
`result : 1 2 3 4 5`

```
#include <stdio.h>

int staticLocalTest();

int main()
{
	int i = 0;
	while (i < 5)
	{
		printf("%d\\n", staticLocalTest());
		i++;
	}
	return 0;
}

int staticLocalTest()
{
	static int sInt32_value = 0;
	return ++sInt32_value;
}
```
<br>

`result : 1 1 1 1 1`

```
#include <stdio.h>

int staticLocalTest();

int main()
{
	int i = 0;
	while (i < 5)
	{
		printf("%d\\n", staticLocalTest());
		i++;
	}
	return 0;
}

int staticLocalTest()
{
	int sInt32_value = 0;
	return ++sInt32_value;
}
```

auto : stack 메모리 자동 할당

static : static 메모리 할당

const : 상수

final : runtime const

<br>

extern은 다중 모듈 프로그램에서 전역변수에 선언된 변수를 가져오기 위해 사용됩니다.

즉, 다른 소스 파일의 전역변수를 가져오는 방법이다.



![12](https://github.com/sehun98/TIL/assets/100746863/bfed4570-688c-4224-bfeb-c4d44bdeeebf)

<br>

<br>
