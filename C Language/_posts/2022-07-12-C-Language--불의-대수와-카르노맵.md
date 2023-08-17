---
title: "C Language : 불의 대수 & 카르노 맵"
excerpt: "임베디드 영역에서는 비트를 자유자재로 다루는 법과 마찬가지로 연산자를 자유자재로 다루는 법이 중요합니다."
categories:
  - C Language
---

<br>

<br>

## ⭐ 불의 대수 & 카르노 맵 ⭐

## 임베디드 영역에서는 비트를 자유자재로 다루는 법과 마찬가지로 연산자를 자유자재로 다루는 법이 중요합니다.

간단한 예를 들어

GPIO 선언 시 struct를 통해 선언된 레지스터들을 조작할 때 일정 비트를 ON/OFF 하거나,

데이터를 받아드릴때 하위/상위 비트를 뽑아 사용할 때,

데이터를 나누거나 곱하는 가공에도 사용됩니다.

```
&` , `|` , `&&` , `||
```

------

<br>

## Basic Boolean algebra laws

|                     | AND                         | OR                           |
| ------------------- | --------------------------- | ---------------------------- |
| Commutative         | A · B = B · A               | A + B = B + A                |
| Associative         | (A · B) · C = A · (B · C)   | (A + B) + C = A + (B + C)    |
| Distributive        | A · (B + C) = A · B + A · C | A + (B · C) = (A + B)(A + C) |
| De Morgan's Theorem | (A · B)' = A' + B'          | (A + B)' = A' · B'           |
|                     | (A · B · C)' = A' + B' + C' | (A + B + C)' = A' · B' · C'  |
|                     | A · 0 = 0                   | A + 0 = A                    |
|                     | A · 1 = A                   | A + 1 = 1                    |
|                     | A · A = A                   | A + A = A                    |
|                     | A · A' = 0                  | A + A' = 1                   |
|                     | A · (A + B) = A             | A + (A · B) = A              |
|                     | A · (A' + B) = A · B        | A + (A' · B) = A + B         |
|                     | A · B + A · B' = A          | (A + B)(A + B') = A          |
|                     | (A')' = A                   | 0' = 1                       |

<br>

<br>
