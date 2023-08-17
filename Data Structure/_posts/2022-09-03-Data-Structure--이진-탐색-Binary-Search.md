---
title: "Data Structure : 이진 탐색 Binary Search"
excerpt: "O(log2 n)에 해당하는 암기해야 할 이진 탐색에 대해 학습합니다."
categories:
  - Data Structure
---

<br>

<br>

## Binary Search

정렬(Sort)이 되어 있는 데이터를

데이터의 시작(Start)과 끝(End)을 합한 결과를 2로 나눈 중간(Mid)과 비교하여

<img width="" alt="3" src="https://user-images.githubusercontent.com/100746863/192074592-19c34386-a6d7-4dd7-a51d-f74495759a88.PNG">

찾고자 하는 값(SearchData) 이 중간(Mid)보다 작을 경우 왼쪽

찾고자 하는 값(SearchData) 이 중간(Mid)보다 클 경우 오른쪽을 바라보아

<img width="100%" alt="4" src="https://user-images.githubusercontent.com/100746863/192074594-db99f160-0d43-4f52-a51a-636b312f6616.PNG">

Start와 End 값을 변경하여 Start와 End가 역전 될때까지 반복 진행을 합니다. 



<img width="100%" alt="5" src="https://user-images.githubusercontent.com/100746863/192074595-bd83e194-3a0f-44db-92f7-3dd6361f0d9e.PNG">

```c
#include <stdio.h>

int binarySearch(int* arr, int start, int end, int searchData);

int main()
{
	int arr[] = { 1, 3, 6, 8, 9, 14, 18, 25, 29 };
	int searchData = 0;

	scanf_s("%d", &searchData);

	printf("%d",binarySearch(arr, 0, sizeof(arr) / sizeof(int), searchData));

	return 1;
}

int binarySearch(int* arr, int start, int end, int searchData)
{
	int mid = 0;
	if (start <= end)
	{
		mid = (start + end) / 2;
		if (arr[mid] < searchData) binarySearch(arr, mid + 1, end, searchData);
		else if (arr[mid] > searchData) binarySearch(arr, start, mid - 1, searchData);
		else return mid;
	}
	else return -1;
}
```

Recursion 을 사용할 때에는 입력 데이터, 출력 데이터, 종료 조건을 설정해야 합니다.

<br>

## 알고리즘 분석

우선 사용하는 연산자를 모두 추출하여 연산자의 관계를 생각해봅니다.

대입 연산자 `=`

나누기 연산자 `/`

비교 연산자 `<`

덧셈 연산자 `+`

T(n) = log2 n + 1로 O(log2 n) 이 됩니다.

<img width="100%" alt="2" src="https://user-images.githubusercontent.com/100746863/192072207-6142d953-fca1-4c84-9a83-1336d26999ee.PNG">

<br>

<br>
