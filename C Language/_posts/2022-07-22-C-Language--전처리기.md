---
title: "C Language : #전처리기 매크로"
excerpt: "컴파일 과정에서 전처리기를 동작하여 바이너리 파일을 보다 효율적으로 생성하기 위해 사용됩니다."
categories:
  - C Language
---

<br>

<br>

# ⭐ #전처리기 ⭐

컴파일 과정에서 전처리기를 동작하여 바이너리 파일을 보다 효율적으로 생성하기 위해 사용됩니다.

`#include` ,`#define` ,

`#if` ,`#ifdef` ,`#ifndef` ,

`#else` ,`#elif` ,

`#endif` ,

------

컴파일과정에서 헤더파일이 중복되어 불러오지 않도록 할 수 있고, 운영체제를 구분하여 부분적으로 소스코드를 제거하거나 추가할 수 있습니다.

```c
#ifdef _WIN32
#include <windows.h>
#endif

#ifdef linux
#include <unistd.h>
#endif
```

전처리기 매크로

```dart
#define MALLOC(type) (type*)malloc(sizeof(type))
#define SWAP(a, b) {int tmp=a; a=b; b=tmp;}
```

전처리기 예약어

```dart
__DATE__ // 이 매크로를 만나면 현재의 날짜(월 일 년)로 치환된다.
__TIME__ // 이 매크로를 만나면 현재의 시간(시 분 초)으로 치환된다.
__LINE__ // 이 매크로를 만나면 소스 파일에서의 현재의 라인 번호로 치환된다.
__FILE__ // 이 매크로를 만나면 소스 파일 이름으로 치환된다.
```

<br>

<br>
