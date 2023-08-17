---
title: "C Language : 메모리 영역"
excerpt: "프로그래머는 메모리의 영역을 고려해야 한다고 생각합니다. "
categories:
  - C Language
---

<br>

<br>

# ⭐ 메모리 영역 ⭐

기본적으로 데이터를 다루는 직업인 프로그래머는 메모리의 영역을 고려해야 한다고 생각합니다.  어느 부분에 데이터가 할당되고 참조하는지를 알아야 Memory Leak을 피할 수 있습니다.

Memory Leak이 걸리는 상황과 어떻게 대응하는지에 대해서는 심화 과정에서 알아보도록 합니다.

------

C Memory

| Code Area  | 코드                          |
| ---------- | ----------------------------- |
| Data Area  | 전역변수, Static 변수, 문자열 |
| Stack Area | 지역변수, formal Parameter    |
| Heap Area  | malloc(), free()              |

JVM Runtime Area

| Method Area         |      |
| ------------------- | ---- |
| Heap Area           |      |
| Stack Area          |      |
| PC register         |      |
| Native Method Stack |      |

<br>

<br>
