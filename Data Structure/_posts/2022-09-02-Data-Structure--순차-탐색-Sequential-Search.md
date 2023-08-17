---
title: "Data Structure : 순차 탐색 Sequential Search"
excerpt: "O(n) 가장 기초가 되는 데이터 탐색 방법입니다."
categories:
  - Data Structure
---

<br>

<br>

## Sequential Search

순차적으로 데이터를 비교하면서 원하는 데이터의 위치를 찾아내는 알고리즘 입니다.

<br>

```c
#include <stdio.h>

int SequentialSearch(int* arr, int arrLength, int searchData);

int main()
{
    int arr[] = { 22 ,9 ,2 ,10 ,11, 32 };
    int searchData = 0;

    scanf_s("%d", &searchData);

    printf("%d", SequentialSearch(arr, sizeof(arr) / sizeof(int), searchData));

    return 1;
}

int SequentialSearch(int* arr, int arrLength, int searchData)
{
    for (int i = 0; i < arrLength; i++)
    {
        if (searchData == arr[i])
        return i;
    }
    return -1;
}
```

<br>

## 알고리즘 분석

우선 사용하는 연산자를 모두 추출하여 연산자의 관계를 생각해봅니다.

사용하는 연산자는 다음과 같습니다.

대입 연산자 `=`

비교 연산자 `<`

증가 연산자 `++`

등호 연산자 `==`

여기서 가장 연산 속도에 영향을 많이 주는 연산자 `==` 에 대해 집중을 합니다.

각 `=` , `<` , `++`  연산자들은 return 문에 의해 `==` 연산의 성립이 되면 중단되는 종속적인 관계에 해당됩니다.

따라서 최악의 경우(Worst Case) 를 고려 했을 때 T(n) = n으로 O(n)에 해당됩니다.

 <img width="100%" alt="2" src="https://user-images.githubusercontent.com/100746863/192072207-6142d953-fca1-4c84-9a83-1336d26999ee.PNG">

<br>

<br>
