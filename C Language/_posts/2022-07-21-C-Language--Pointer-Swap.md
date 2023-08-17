---
title: "C Language : Pointer Swap"
excerpt: "strcpy, strncpy, strlen, strcmp, strcat"
categories:
  - C Language
---

<br>

<br>

# ⭐Pointer Swap⭐

```c
/*****************************************************
* brief : swap function
* param : 구조체 배열의 주소
* return : void
*****************************************************/
void swap(struct _point* point1, struct _point* point2) {
	struct _point temp;
	temp = *point1;
	*point1 = *point2;
	*point2 = temp;
}
```

<br>

<br>
