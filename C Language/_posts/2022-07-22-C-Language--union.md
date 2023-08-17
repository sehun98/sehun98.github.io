---
title: "C Language : union"
excerpt: "struct(구조체), array(배열), enum(열거형), pointer(포인터), function Pointer(함수 포인터)"
categories:
  - C Language
---

<br>

<br>

# ⭐ union ⭐

같은 데이터 타입을 다르게 표현하고자 할 때 사용됩니다.

rgb를 예를 들 수 있습니다.

`Hex Code` : #A52A2A

`Decimal Code` : (165,42,42,0) (r,g,b,a)

```cpp
typedef union
{
    unsigned int val;

    struct
    {
        unsigned char r;
        unsigned char g;
        unsigned char b;
        unsigned char a;
    } rgba;
} color_t;

int main(void)
{
  color_t yellow;

  yellow.rgba.r= 255;   // 0xff
	yellow.rgba.g= 255;   // 0xff  
	yellow.rgba.b= 0;     // 0x00  
	yellow.rgba.a= 255;   // 0xff  
	printf("yellow: 0x%08x(%3d, %3d, %3d, %3d)\\n",yellow.val, yellow.rgba.r, yellow.rgba.g, yellow.rgba.b, yellow.rgba.a);
}
```

<br>

<br>
