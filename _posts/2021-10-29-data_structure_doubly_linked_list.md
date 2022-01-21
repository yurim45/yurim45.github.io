---
title: "🌈 자료구조:: 양방향 연결 리스트"
tags:
  - [dataStructure-algorithm]
permalink: /data_structure/doubly_linked_list

navigation: true
toc: true
toc_sticky: true

date: 2021-10-29
last_modified_at: 2021-10-29
---

![]()

`개인 공부 과정을 기록합니다.`

### 🚀 What I Will Learn

- <span style="color:hotpink">**양방향 연결 리스트**</span>의 동작 원리와 구현 방법에 대해 익히기...

---

# 양방향 연결 리스트

## 1️⃣ 양방향 연결 리스트란?

1. 양방향 연결 리스트는 머리(Head)와 꼬리(Tail)를 모두 가진다는 특징이 있다
2. 양방향 연결 리스트의 각 노드는 <span style="color:hotpink">**앞 노드와 뒤 노트의 정보를 모두 저장**</span>하고 있다

![](https://images.velog.io/images/april_5/post/a240106b-7121-42d9-8db8-7e47ee256ab8/image.png)

<br />

### ✔️ 양방향 연결리스트 구현

<span style="color:dodgerblue">**1) 연결 리스트 선언하기**</span>

```c
#include <stdio.h>
#include <stdlib.h>

typedef struct {
	int data;
	struct Node *prev; // 앞 노드와
	struct Node *next; // 뒤 노드 선언
} Node;
Node *head, *tail;
```

<br />

<span style="color:dodgerblue">**2) 연결 리스트 삽입 **</span>

- [ 1 ]: 삽입할 노드의 앞 노드가, 삽입 할 노드를 바라보게 한다
- [ 2 ]: 삽입할 노드가 앞 노드를 바라보게 한다
  - 이때 삽입할 노드와 삽입할 노드의 앞 노드가 서로 바라보는 형태
- [ 3 ]: 삽입할 노드의 뒤 노드가, 삽입 할 노드를 바라보게 한다
- [ 4 ]: 삽입할 노드가 뒤 노드를 바라보게 한다
  - 이때 삽입할 노드와 삽입할 노드의 뒤 노드가 서로 바라보는 형태

![](https://images.velog.io/images/april_5/post/3e85ab2a-172e-4177-9e93-6435bf559ea6/image.png)

```c
// 양방향 연결 리스트 삽입 함수
void insert(int data) {
	Node* node = (Node*) malloc(sizeof(Node));  // 새로운 노드 할당
	node->data = data;  // 데이터 초기화
	Node* cur;
	cur = head->next;

	while (cur->data < data && cur != tail) {
		cur = cur->next;  // cur변수가 다음 노드를 가리키도록 변경
	}

	Node* prev = cur->prev;  // 삽입할 노드의 앞 노드를 prev로 설정
	prev->next = node;  // 앞 노드의 next가 현재 삽입할 노드를 바라보게 하고
	node->prev = prev;  // 노드의 prev가 앞 노드가 되고
	cur->prev = node;  // 뒤 노드의 prev가 노드가 되고
	node->next = cur;  // 노드의 next가 삽입할 노드의 바로 뒤에 들어갈 노드가 될 수 있도록
}
```

<br />

<span style="color:dodgerblue">**3) 연결 리스트 삭제**</span>

- [ 1 ]: 삭제할 노드의 앞 노드가 삭제할 노드의 뒤를 바라보게 한다
- [ 2 ]: 삭제할 노드의 뒤 노드가 삭제할 노드의 앞을 바라보게 한다
- [ 3 ]: 삭제할 노드 할당 해제

![](https://images.velog.io/images/april_5/post/0cd265f8-f881-48f1-8a7c-b408b2399d86/image.png)

```c
// 양방향 연결 리스트 삭제 함수
void removeFront() {
	Node* node = head->next;
	head->next = node->next;
	Node* next = node->next;
	next->prev = head; free(node);
}
```

<br />

<span style="color:dodgerblue">**4) 연결 리스트 출력**</span>

```c
// 양방향 연결 리스트 전체 출력 함수
void show() {
      Node* cur = head->next;
      while (cur != tail) {
            printf("%d ", cur->data);
            cur = cur->next;
      }
}
```

<br />

<span style="color:dodgerblue">**5) 연결 리스트 사용하기**</span>

```c
int main(void) {
    head = (Node*) malloc(sizeof(Node));
    tail = (Node*) malloc(sizeof(Node));
    head->next = tail;
    head->prev = head;
    tail->next = tail;
    tail->prev = head;
    insert(2);
    insert(1);
    insert(3);
    insert(9);
    insert(7);
    removeFront();
    show();
    system("pause");
    return 0;
}
```

<br /><br />

---

### ✨ tl;dr

- 양방향 연결 리스트에서는 각 노드가 앞 노드와 뒤 노드의 정보를 저장하고 있다
- 양방향 연결 리스트를 이용하면 리스트의 앞에서부터 혹은 뒤에서부터 모두 접근할 수 있다
