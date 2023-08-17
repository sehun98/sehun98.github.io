---
title: "C Language : string함수"
excerpt: "strcpy, strncpy, strlen, strcmp, strcat"
categories:
  - C Language
---

<br>

<br>

# ⭐ string.h ⭐

strcpy() : string을 전부 복사 하는 기능을 하는 함수

strncpy() : string을 일부 복사 하는 기능을 하는 함수

strlen() : string의 길이를 세어주는 함수

strcmp() : string 두 개를 사전 상의 위치 비교

strcat() : string 뒤에 string 추가

------

# strcpy() : string을 `전부 복사`하는 기능을 하는 함수

헤더파일 : #include <string.h>

함수원형 : char* strcpy(char* destination, const char* origin);

```cpp
char origin[] = "String Copy"; // "String Copy\\0" 이므로 size = 12;
char destination[100];

strcpy(destination, origin);
```

# strncpy() : string을 `일부 복사`하는 기능을 하는 함수

헤더파일 : #include <string.h>

함수원형 : char* strncpy(char* destination, const char* origin, size_t n);

주의사항 : n ≤ sizeof(origin) && n ≤ sizeof(destination)

```cpp
char origin[] = "String Copy"; // "String Copy\\0" 이므로 size = 12;
char destination[100];

strncpy(destination, origin, sizeof(origin));
```

# strlen() : string의 `길이`를 세어주는 함수

헤더파일 : #include  <string.h>

함수 원형 : int strlen(char *string);

```cpp
char origin[] = "String Copy"; // "String Copy\\0"이므로 len = 11;

strlen(origin);
```

# strcmp() : string 두 개를 사전 상의 위치 `비교`

헤더파일 : #include <string.h>

함수 원형 : int strcmp(char *string1,char *string2);

```cpp
char string1[] = "a";
char string2[] = "b";

strcmp(string1,string2);
```

# strcat() : string 뒤에 string 추가

헤더파일 : #include <string.h>

함수 원형 : char *strcat(char *string1, char * string2);

```cpp
char string1[] = "a";
char string2[] = "b";

strcat(string1, string2);
```

<br>

<br>
