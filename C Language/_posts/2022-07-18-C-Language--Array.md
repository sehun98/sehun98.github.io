---
title: "C Language : Array"
excerpt: "struct(구조체), array(배열), enum(열거형), pointer(포인터), function Pointer(함수 포인터)"
categories:
  - C Language
---

<br>

<br>

# ⭐ Call by Address 관점에서 배열 Array  학습⭐

고속 연산이 되어가면서 대용량의 데이터를 처리하기 위해 사용되는 데이터의 구조가 중요하게 되었습니다.

C언어에서 배우는 데이터 구조는 `struct(구조체)`, `array(배열)`, `enum(열거형)`, `pointer(포인터)`, `function Pointer(함수 포인터)`가 있습니다.

동일 데이터를 하나의 이름으로 추상화 하는 array 입니다.

배열의 `첫 번째 Element`는 배열의 주소값(포인터)에 해당됩니다. 따라서 배열은 `복사가 이행 되지 않습니다.`

Call by Address를 통한 주소값 전송으로 함수 내부에서 컨트롤 할 수 있게 진행 합니다.

배열을 항상 초기화 해줘야 합니다.

```jsx
int a[10] = {0};
```

------

☑️ 배열의 정의 (배열의 크기에 맞게 메모리 할당이 이루어집니다.)

```cpp
int arryIntValue[10];

char arrtString[] = "Build String"; // "Build String\\0" sizeof = 13, strlen = 12
```

☑️ 배열의 복사

memcpy()

```cpp
#include <stdio.h>
#include <string.h>

#define ARR_SIZE 6

void printfArray(int *arr, int n) {
	int i;
	for(i=0; i<n; i++)
	{
		printf("%d", arr[i]);
	}
	printf("\\n");
}

int main() {
	const int src[ARR_SIZE] = {0,1,2,3,4,5};
	int dst[ARR_SIZE];
	memcpy(dst, src, sizeof(src));
	printfArray(dst, ARR_SIZE);
	return 0;
}
```

my_memcpy()

```cpp
#include <stdio.h>
#include <string.h>

#define ARR_SIZE 6

void my_memcpy(int *dst, const int *src, int n) {
	int i;
	for (i = 0; i < n; i++) {
		dst[i] = src[i];
	}
}

void printArray(int *arr, int n) {
	int i;
	for (i = 0; i < n; i++) {
		printf("%d ", arr[i]);
	}
	printf("\\n");
}

int main() {
	const int src[ARR_SIZE] = {0, 1, 2, 3, 4, 5};
	int dst[ARR_SIZE];
	my_memcpy(dst, src, ARR_SIZE);
	printArray(dst, ARR_SIZE);
	return 0;
}
```

<br>

# ⭐ 데이터 타입 관점에서 배열 Array  학습⭐

메모리 구조로 데이터를 바라 보았을 때

`char` , `short` , `int` , `long` , `float` , `double` 의 데이터 타입들은 대량의 데이터를 연산하기에 부적합합니다.

char를 토대로 예를 들어보겠습니다.

<code>

```jsx
char c1 = 1;
char c2 = 1;
 . . .

char c100 = 1;
```

<메모리 구조>

| Symbolic Address | Value |
| ---------------- | ----- |
| c100             | 1     |
|                  | . . . |
| c2               | 1     |
| c1               | 1     |

<br>

데이터 사이의 연관성이 없기 때문에 데이터를 사용하기 위해서는 연관성을 주어야 합니다.

따라서 배열을 통해 다음과 같이 연관성을 부여합니다.

<code>

```jsx
char c[100] = {1,1, . . . , 1};
```

<메모리 구조>

| Symbolic Address | Value |
| ---------------- | ----- |
| c[99]            | 1     |
|                  | . . . |
| c[1]             | 1     |
| c[0]             | 1     |

<br>

<br>
