---
title: "C Language : sprintf()"
excerpt: "printf와 sprintf의 차이가 무엇일까?"
categories:
  - C Language
---

<br>

<br>

`printf`는 화면에 직접 출력하는 함수이고, `sprintf`는 형식화된 문자열을 문자열 버퍼에 저장하는 함수입니다. 사용 목적과 환경에 따라 적절한 함수를 선택하여 사용됩니다.

```c
#include <string.h>

int main()
{
	sprintf(arrayName, "%d", a); // arrayName의 버퍼에 a를 저장

	return 0;
}
```

<br>

<br>
