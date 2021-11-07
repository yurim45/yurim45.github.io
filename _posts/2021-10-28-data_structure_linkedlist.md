---
title: '🌈 자료구조:: 연결리스트'
tags:
  - [data-structure💥algorithm]
permalink: /dataStructure/linkedList

navigation: true
toc: true
toc_sticky: true

date: 2021-10-28
last_modified_at: 2021-10-28
---

![]()

`개인 공부 과정을 기록합니다.`

### 🚀 What I Will Learn

- <span style="color:hotpink">**연결 리스트**</span>의 필요성과 사용에 대해 학습한다
- C언어를 활용하여 단일 연결 리스트를 구현해본다...

<br />

---

# 연결 리스트(Linked List)

## 1️⃣ 연결 리스트의 필요성

1. 일반적으로 배열을 사용하여 데이터를 순차적으로 저장하고, 나열할 수 있지만
2. 배열을 사용하는 경우, 메모리 공간이 불필요하게 낭비될 수 있드므로
3. 이때 연결 리스트로 대체할 수 있다

<br />

### ✔️ 배열 기반 리스트란?

1. 데이터를 순차적으로 저장, 처리할 때는 배열 기반의 리스트를 이용

![](https://images.velog.io/images/april_5/post/ebb2fd1e-a65f-48d6-83be-bd38ca8f63cb/image.png)

<br />

```c
#include <stdio.h>
#define INF 10000

int arr[INF];

int count = 0;
void addBack(int data) {
	arr[count] = data;
	count++;
}

void addFirst(int data) {
	for (int i = count; i >= 1; i--) {
		arr[i] = arr[i - 1];
	}
	arr[0] = data;
	count++;
}

void show() {
for (int i = 0; i < count; i++) {
    printf("%d ", arr[i]);
  }
}

int main(void) {
	addFirst(4);
    	addFirst(5);
        addFirst(1);
        addBack(7);
        addBack(6);
        addBack(8);
        show();
        system("pause");
        return 0;
}
```

> 그렇다면?! <span style="color:hotpink">**특정한 위치의 원소를 삭제하는 함수**</span>는 어떻게 만들 수 있을까?

```c
// 특정한 index를 받아서 해당 index 위치의 뒷 원소를 앞으로 당기는 방식으로 구현
void removeAt(int index) {
	for (int i = index; i < count - 1; i++) {
		arr[i] = arr[i + 1];
	}
	count--;
}
```

### ✔️ 배열 기반 리스트의 특징

- 배열로 만들었으므로 특정한 위치의 원소에 즉시 접근할 수 있다는 장점
  - `index`를 활용
- 데이터가 들어갈 공간을 미리 메모리에 할당한다는 단점
  - `#define INF 10000`
- 원하는 위치로의 삽입 또는 삭제가 비효율적
  - for문으로 앞으로 당기거나 뒤로 밀어서 추가 또는 삭제했던 위의 코드

<br /><br />

---

## 2️⃣ 연결 리스트

- 일반적으로 연결 리스트는 <span style="color:hotpink">**구조체**</span>와 <span style="color:hotpink">**포인터**</span>를 함께 사용하여 구현
- 연결 리스트는 리스트의 중간 지점에 노드를 추가하거나 삭제할 수 있어야 함
- <span style="color:hotpink">**필요할 때 마다 메모리 공간을 할당**</span> 받는다

> 📌 **참고!**

- [포인터란?](https://velog.io/@april_5/포인터pointer-개념-이해) ⬅️클릭
- 구조체란?

<br />

### ✔️ 단일 연결리스트

- 단일 연결 리스트는 데이터**`data`**와 다음 노드를 가리키는 **`next`** 로 구성되어 있다
- **포인터**를 이용해 단방향적으로 다음 노드를 가리킨다
- 연결 리스트의 시작 노드를 **`헤드(Head)`**라고 하며 별도로 관리한다
- 다음 노드가 없는 끝 노드의 다음 위치 값으로 `**NULL`\*\*을 추가한다

![](https://images.velog.io/images/april_5/post/628562a0-00f6-40be-a9ec-29d4a0c3d4f4/image.png)

<br />

### ✔️ 단일 연결리스트 구현

<span style="color:dodgerblue">**1) 연결 리스트 구조체 만들기**</span>

```c
#include <stdio.h>
#include <stdlib.h>

typedef struct {
  int data;
  struct Node *next;  // 다음 노드를 가리키는 변수. 포인터 변수
} Node;

Node *head;  // 포인터 변수를 활용해 동적 할당이 이루어지도록 한다
```

<br />

<span style="color:dodgerblue">**2) 연결 리스트 구조체 사용해보기**</span>

- `malloc()` 함수로 동적 할당하기

```c
int main(void) {
  head = (Node*) malloc(sizeof(Node));
  Node *node1 = (Node*) malloc(sizeof(Node));
  node1->data = 1;
  Node *node2 = (Node*) malloc(sizeof(Node));
  node2->data = 2;
  head->next = node1;
  node1->next = node2;
  node2->next = NULL;
  Node *cur = head->next;

  while (cur != NULL) {
  	printf("%d ", cur->data);
  	cur = cur->next;
  }

  system("pause");
  return 0;
}
```

- 결과는 1, 2가 출력되며 아래의 그림의 모양이 완성

![](https://images.velog.io/images/april_5/post/47afd59d-74f0-4485-a7bd-884a315273a9/image.png)

<br />

<span style="color:dodgerblue">**3) 노드 삽입**</span>

![](https://images.velog.io/images/april_5/post/f558b7df-6932-4096-88f6-1207ffb48e00/image.png)

- 연결 리스트 삽입 함수 구현

```c
void addFront(Node *root, int data) {
	Node *node = (Node*) malloc(sizeof(Node));
    	node->data = data;
	node->next = root->next;
	root->next = node;
}
```

![](https://images.velog.io/images/april_5/post/176898b7-4bce-4c12-b16a-93caf38e23a2/image.png)

<br />

<span style="color:dodgerblue">**4) 노드 삭제**</span>

- 연결 리스트 삭제 함수 구현

```c
void removeFront(Node *root) {
  Node *front = root->next;
  root->next = front->next;
  free(front);
}
```

<br />

<span style="color:dodgerblue">**5) 할당된 메모리 해제**</span>

- `free()` 함수로 노드를 하나씩 접근해서 해제해야 함

```c
void freeAll(Node *root) {
	Node *cur = head->next;
	while (cur != NULL) {
	    Node *next = cur->next;
            free(cur);
            cur = next;
	}
}
```

<br />

<span style="color:dodgerblue">**6) 연결 리스트 전체 출력 함수**</span>

```c
void showAll(Node *root) {
	Node *cur = head->next;

	while (cur != NULL) {
 	    printf("%d ", cur->data);
	    cur = cur->next;
	}
}
```

<br />

<span style="color:dodgerblue">**7) 완성된 연결 리스트 사용하기**</span>

```c
int main(void) {
	head = (Node*) malloc(sizeof(Node));
    	head->next = NULL;
	addFront(head, 2);
	addFront(head, 1);
	addFront(head, 7);
	addFront(head, 9);
	addFront(head, 8);
	removeFront(head);
	showAll(head);
	freeAll(head);

	system("pause");
	return 0;
}
```

<br />

### ✔️ 연결 리스트 특징

- 삽입과 삭제가 배열에 비해 간단하다는 장점
- 배열과 다르게 특정 인덱스로 즉시 접근하지 못하고, 원소를 차례대로 검색해야 한다는 단점
- 추가적인 포인터 변수가 사용되므로 메모리 공간이 낭비된다.....

<br /><br />

---

### ✨ tl;dr

- 연결 리스트는 데이터를 선형적으로 저장하고 처리하는 한 방법이다
- 기존에 배열을 이용했을 때 보다 삽입과 삭제가 많은 경우에 효율적이다
- 다만, 특정 인덱스에 바로 참조해야 할 때가 많다면 배열을 이용하는 것이 효율적이다....
