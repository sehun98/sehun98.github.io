---
title: "C Language : 지역변수(auto) & 전역변수"
excerpt: "전역 변수는 다른 함수에 의한 Data 왜곡이 생길 가능성이 존재하고 종료 될 때까지 메모리를 차지하므로 Memory Leak에 걸릴 수 있습니다."
categories:
  - C Language
---

<br>

<br>

# ⭐ 지역변수(auto) & 전역변수 ⭐

`auto`, `static`, `extern`, `const`, `final(java)` 에서 지역변수, 전역변수에 대해 말을 했었습니다.

지역 변수는 Stack Area에 런타임 시에 메모리가 할당되며 중괄호 내에 선언된 변수로 해당 함수에서 벗어나게 되면 메모리 할당이 해제됩니다.

반면, 전역 변수는 Data Area에 컴파일 시에 메모리가 할당되며 다른 함수들에 의해 접근이 가능해 종료 될 때까지 존재하게 됩니다.

따라서 전역 변수는 다른 함수에 의한 Data 왜곡이 생길 가능성이 존재하고 종료 될 때까지 메모리를 차지하므로 `Memory Leak`에 걸릴 수 있습니다.

------

| Code Area  | 코드                             |
| ---------- | -------------------------------- |
| Data Area  | 전역변수, Static 변수, 문자열    |
| Stack Area | 지역변수, formal Parameter, auto |
| Heap Area  | malloc(), free()                 |

`global value` & `local value`

```
#include <stdio.h>
int g_Value;

int main()
{
	char local_Value;
	return 0;
}
```

<br>

<br>
