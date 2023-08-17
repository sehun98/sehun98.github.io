---
title: "C Language : 동적할당 malloc() free()"
excerpt: "생성된 메모리 공간은 free()를 통한 회수가 이루어지지 않으면 메모리 할당을 유지하고 있는 상태가 됩니다."
categories:
  - C Language
---

<br>

<br>

# 동적 할당 malloc() free()

# ⭐ 자료구조 선행 학습 ⭐

앞으로 배우게 될 자료 구조에서 사용되는 malloc() 함수와 free() 함수에 대해서 알아보겠습니다.

malloc() 함수는 memory allocation으로 runtime 시 동적으로 메모리를 할당해주는 역할을 합니다.

기존에는 소스 코드를 작성한 그대로 정적으로 statac 영역에 메모리를 할당해주었다면 runtime 시 동적으로 메모리 할당을 해준다는 차이점이 생기게 됩니다.

이때 생성된 메모리 공간은 free()를 통한 회수가 이루어지지 않으면 메모리 할당을 유지하고 있는 상태가 됩니다. 따라서 Memory Leak에 원인이 됩니다.

<br>

<br>
