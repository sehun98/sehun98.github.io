---
title: "C Language : Bool"
excerpt: "C언어에는 Bool 타입이 존재하지 않습니다."
categories:
  - C Language
---

<br>

<br>

# ⭐ Bool  타입 만들기 ⭐

C언어에는 Bool 타입이 존재하지 않기 때문에 가독성을 위해 Bool을 사용하고 싶다면 다음과 같이 선언하면 된다.

```cpp
typedef enum { False = 0, True = 1} Bool;
```

------

```jsx
#include <stdio.h>
typedef enum { false, true } bool;

int main()
{
	bool symbolicAddress = true;

	if (!symbolicAddress) {
		printf("true");
	}
	else printf("false");

	return 0;
}
```

<br>

<br>
