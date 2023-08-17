---
title: "C Language : Enum"
excerpt: "struct(구조체), array(배열), enum(열거형), pointer(포인터), function Pointer(함수 포인터)"
categories:
  - C Language
---

<br>

<br>

# ⭐ 열거형 enum ⭐

고속 연산이 되어가면서 대용량의 데이터를 처리하기 위해 사용되는 데이터의 구조가 중요하게 되었습니다.

C언어에서 배우는 데이터 구조는 `struct(구조체)`, `array(배열)`, `enum(열거형)`, `pointer(포인터)`, `function Pointer(함수 포인터)`가 있습니다.

<br>

enum은 enumeration 나열이라는 뜻으로 (const int) 정수형 상수 식별자들로

week, 국가, 색상과 같은 결이 같은 데이터들로 구성되는 자료형입니다.

\#define 들이 너무 많지 않을때

경우의 수가 결정되어있을 때 사용한다.

```cpp
enum deptcode {KOREA = 100, USA = 200, JP}; // JP = 201이 된다.

enum deptcode {KOREA, USA, JP};
struct student {
	int id;
	enum deptcode dept;
};
```
<br>
``` cpp
dept = KOREA;
enum DayOfWeek {sun,mon,tue,wed,fri,sat}; // 0, 1, 2, 3, 4, 5

enum DayOfWeek week;

week = Tuesday;
printf("%d\\n",week);
```

<br>

<br>
