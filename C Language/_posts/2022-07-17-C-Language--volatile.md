---
title: "C Language : Volatile"
excerpt: "volatile은 변수에 대해서 프로그램 최적화 적용을 하지 않음을 의미합니다."
categories:
  - C Language
---

<br>

<br>

# ⭐ Volatile ⭐

## 쓰레드를 공부하기 전에 한번 읽어보고 공부하기를 권장합니다.

프로그램이 컴파일 시에 최적화로 인해 명시되지 않고 변수 값이 변경될 수 있는 경우 사용됩니다. (쓰레드에 의한 변수값이 변경될 수 있을 경우 사용)

따라서 volatile은 변수에 대해서 프로그램 최적화 적용을 하지 않음을 의미합니다.

(optimizing 하지마라!)

------

실제로 다음 코드에서 while을 최적화 시키는 것을 알 수 있습니다.

```cpp
int main()
{
	int i = 0;

	while(i<10);
	i++;

	printf("%d",i);	

	return 0;
}
```

최적화된 코드

```cpp
int main()
{
	int i = 10;
	printf("%d", i);
	
	return 0;
}
```

따라서 메모리에 접근할 수 있게 동작 하게 하려면 volatile을 사용해야 합니다.

<br>

<br>
