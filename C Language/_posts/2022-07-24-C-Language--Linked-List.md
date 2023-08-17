---
title: "C Language : Linked List"
excerpt: "Linked List를 이해를 하기 위해 제일 먼저, linked list를 그려보도록 하자."
categories:
  - C Language
---

<br>

<br>

# ⭐ Linked List ⭐

Linked List를 이해를 하기 위해 제일 먼저, linked list를 그려보도록 하자.

# CURD (Create Update Read Delete)

insert

```cpp
#include <stdio.h>
#include <assert.h>
#include "list.h"

void insert(struct node **phead, int data)
{
	struct node *newnode;

	newnode = MALLOC(struct node);
	if (newnode == NULL) {
		printf("메모리가 부족하여 자료 %d를 삽입할 수 없습니다.\\n", data);
		return;
	}
	newnode->data = data;
	newnode->next = *phead;
	*phead = newnode;
}
```

delete_first

```cpp
int delete_first(struct node **phead)
{
	int data;
	struct node *tmpnode;

	assert(*phead != NULL);		/* 비어 있지 않은 연결 리스트 인지 확인 */
	 tmpnode = *phead;
	data = tmpnode->data;			/* 반환할 자료 저장 */
	*phead = tmpnode->next;		/* 헤드 노드 변경 */
	free(tmpnode);						/* 삭제되는 첫 번째 노드 공간 반납 */
	return data;							/* 자료 반환 */
}
```

insert_order

```cpp
/* 자료 data를 연결 리스트에 오름차순으로 삽입 */
void insert_order(struct node **phead, int data)
{
	struct node *p, *newnode;

	p = *phead;			/* 헤드 노드 */
	if (p == NULL || data < p->data) {
		insert(phead, data); return;
	}

	newnode = MALLOC(struct node);
	if (newnode == NULL) {
		printf("메모리가 부족하여 자료 %d를 삽입할 수 없습니다.\\n", data);
		return;
	}
	newnode->data = data;

	while (p->next != NULL) {	/* 자료가 삽입될 위치를 찾음 */
		if (data < p->next->data) break;
		p = p->next;
	}
	newnode->next = p->next;	/* 노드 p 다음에 삽입 */
	p->next = newnode;		
}
```

print_list

```cpp
/* 연결 리스트의 모든 자료를 순서대로 출력 */
void print_list(struct node *head) {
	struct node *p;

	p = head;
	while (p != NULL) {
		printf("%6d",p->data);
		p = p->next; }
	printf("\\n");
}
```

<br>

<br>
