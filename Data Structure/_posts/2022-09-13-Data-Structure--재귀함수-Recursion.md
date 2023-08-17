---
title: "Data Structure : Recursion 재귀함수"
excerpt: "간결하고 명확한 코드를 위한 재귀함수"
categories:
  - Data Structure
---

<br>

<br>

## Recursion

DFS (Depth First Search), BackTracking 알고리즘에서 주로 사용되는 재귀 함수(Recursion) 입니다.

예제

1. Binary Search
2. Factorial
3. Fibonacci Numbers
4. The Tower of hanoi

<br>

Recursion을 설계할 때에 고려해야 하는 것은 주로 3가지입니다.

1. 입력 데이터
2. 출력 데이터
3. 종료 조건

재귀 함수의 경우 자신의 함수를 호출 하는 것 처럼 보이지만 실제로 Stack에 새로운 함수를 선언하기 때문에 복제라고 볼 수 있습니다. 따라서 메모리 사용량이 많아지게 되므로 종료 조건을 명확하게 설정해주어야 합니다.

<img width="100%" alt="6" src="https://user-images.githubusercontent.com/100746863/192078053-61c3e44e-7116-44b4-962b-a5a5143622d2.PNG">

<br>

<br>
