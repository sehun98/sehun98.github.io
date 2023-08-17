---
title: "C Language : Call by Value & Call by Address"
excerpt: "C언어를 학습 했는데 Call by Value 와 Call by Address에 대해서 모른다는 것은 핵심을 모른다는 것이나 다름 없다고 생각합니다."
categories:
  - C Language
---

<br>

<br>

# ⭐ Call by Value & Call by Address ⭐

C언어를 학습 했는데 Call by Value 와 Call by Address에 대해서 모른다는 것은 핵심을 모른다는 것이나 다름 없다고 생각합니다.

------

Call by Value를 메모리 측면에서 접근해서 설명하자면,

Actual Parameter에 있는 인자(변수의 값)이 Formal Parameter 메모리에 `복사` 되는 것이여서 함수 내부에서 직접적인 접근이 이루어지는 것이 아닙니다.

(새로운 메모리 할당)

반면, Call by Address(Call by reference)는 Actual Parameter에 있는 인자의 값이 아닌 인자의 `주소값`이 Formal Parameter 메모리에 전달되게 됩니다.

따라서 함수 내부에서는 주소값을 이용해 `직접 인자에 접근` 할 수 있게 됩니다.

이러한 방법은 C언어에서는

직관적으로 Actual Parameter에서 Formal Parameter로 배열의 복사가 이행되지 않기 때문에 배열명인 배열의 첫번째 엘리멘트가 들어있는 곳의 주소를 Formal Parameter에 전달 해주게 됩니다.

```c
#include <stdio.h>

void callByValue(int xInt32Value);
void callByAddress(int xArrInt32Value[]);

int main(void)
{
	int int32Value= 0;
  int arryInt32Value[5] = {0};

	printf("%d %d\\n",int32Value, &int32Value);
	callByValue(int32Value);

	printf("%d %d\\n",arryInt32Value[0],&arryInt32Value[0]);
	callByAddress(&arryInt32Value[0]);

	return 0;	
}

/**********************************
 * brief        : call by value excample
 * prame        : int32Value value
 * return       : no
**********************************/

void callByValue(int xInt32Value)
{
	printf("%d %d\\n\\n",xInt32Value,&xInt32Value); // 주소값이 변하는 것을 볼 수 있다.
}

/**********************************
 * brief        : call by address excample
 * prame        : &arryInt32Value[0] array address
 * return       : no
**********************************/
void callByAddress(int xArryInt32Value[])
{
	printf("%d %d\\n\\n",xArryInt32Value[0],&xArryInt32Value[0]); // 주소값이 변하지 않은 것을 볼 수 있다.
}
```

<br>

<br>
