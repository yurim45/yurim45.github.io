---
title: "๐ ์๋ฃ๊ตฌ์กฐ:: ์๋ฐฉํฅ ์ฐ๊ฒฐ ๋ฆฌ์คํธ"
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

`๊ฐ์ธ ๊ณต๋ถ ๊ณผ์ ์ ๊ธฐ๋กํฉ๋๋ค.`

### ๐ What I Will Learn

- <span style="color:hotpink">**์๋ฐฉํฅ ์ฐ๊ฒฐ ๋ฆฌ์คํธ**</span>์ ๋์ ์๋ฆฌ์ ๊ตฌํ ๋ฐฉ๋ฒ์ ๋ํด ์ตํ๊ธฐ...

---

# ์๋ฐฉํฅ ์ฐ๊ฒฐ ๋ฆฌ์คํธ

## 1๏ธโฃ ์๋ฐฉํฅ ์ฐ๊ฒฐ ๋ฆฌ์คํธ๋?

1. ์๋ฐฉํฅ ์ฐ๊ฒฐ ๋ฆฌ์คํธ๋ ๋จธ๋ฆฌ(Head)์ ๊ผฌ๋ฆฌ(Tail)๋ฅผ ๋ชจ๋ ๊ฐ์ง๋ค๋ ํน์ง์ด ์๋ค
2. ์๋ฐฉํฅ ์ฐ๊ฒฐ ๋ฆฌ์คํธ์ ๊ฐ ๋ธ๋๋ <span style="color:hotpink">**์ ๋ธ๋์ ๋ค ๋ธํธ์ ์ ๋ณด๋ฅผ ๋ชจ๋ ์ ์ฅ**</span>ํ๊ณ  ์๋ค

![](https://images.velog.io/images/april_5/post/a240106b-7121-42d9-8db8-7e47ee256ab8/image.png)

<br />

### โ๏ธ ์๋ฐฉํฅ ์ฐ๊ฒฐ๋ฆฌ์คํธ ๊ตฌํ

<span style="color:dodgerblue">**1) ์ฐ๊ฒฐ ๋ฆฌ์คํธ ์ ์ธํ๊ธฐ**</span>

```c
#include <stdio.h>
#include <stdlib.h>

typedef struct {
	int data;
	struct Node *prev; // ์ ๋ธ๋์
	struct Node *next; // ๋ค ๋ธ๋ ์ ์ธ
} Node;
Node *head, *tail;
```

<br />

<span style="color:dodgerblue">**2) ์ฐ๊ฒฐ ๋ฆฌ์คํธ ์ฝ์ **</span>

- [ 1 ]: ์ฝ์ํ  ๋ธ๋์ ์ ๋ธ๋๊ฐ, ์ฝ์ ํ  ๋ธ๋๋ฅผ ๋ฐ๋ผ๋ณด๊ฒ ํ๋ค
- [ 2 ]: ์ฝ์ํ  ๋ธ๋๊ฐ ์ ๋ธ๋๋ฅผ ๋ฐ๋ผ๋ณด๊ฒ ํ๋ค
  - ์ด๋ ์ฝ์ํ  ๋ธ๋์ ์ฝ์ํ  ๋ธ๋์ ์ ๋ธ๋๊ฐ ์๋ก ๋ฐ๋ผ๋ณด๋ ํํ
- [ 3 ]: ์ฝ์ํ  ๋ธ๋์ ๋ค ๋ธ๋๊ฐ, ์ฝ์ ํ  ๋ธ๋๋ฅผ ๋ฐ๋ผ๋ณด๊ฒ ํ๋ค
- [ 4 ]: ์ฝ์ํ  ๋ธ๋๊ฐ ๋ค ๋ธ๋๋ฅผ ๋ฐ๋ผ๋ณด๊ฒ ํ๋ค
  - ์ด๋ ์ฝ์ํ  ๋ธ๋์ ์ฝ์ํ  ๋ธ๋์ ๋ค ๋ธ๋๊ฐ ์๋ก ๋ฐ๋ผ๋ณด๋ ํํ

![](https://images.velog.io/images/april_5/post/3e85ab2a-172e-4177-9e93-6435bf559ea6/image.png)

```c
// ์๋ฐฉํฅ ์ฐ๊ฒฐ ๋ฆฌ์คํธ ์ฝ์ ํจ์
void insert(int data) {
	Node* node = (Node*) malloc(sizeof(Node));  // ์๋ก์ด ๋ธ๋ ํ ๋น
	node->data = data;  // ๋ฐ์ดํฐ ์ด๊ธฐํ
	Node* cur;
	cur = head->next;

	while (cur->data < data && cur != tail) {
		cur = cur->next;  // cur๋ณ์๊ฐ ๋ค์ ๋ธ๋๋ฅผ ๊ฐ๋ฆฌํค๋๋ก ๋ณ๊ฒฝ
	}

	Node* prev = cur->prev;  // ์ฝ์ํ  ๋ธ๋์ ์ ๋ธ๋๋ฅผ prev๋ก ์ค์ 
	prev->next = node;  // ์ ๋ธ๋์ next๊ฐ ํ์ฌ ์ฝ์ํ  ๋ธ๋๋ฅผ ๋ฐ๋ผ๋ณด๊ฒ ํ๊ณ 
	node->prev = prev;  // ๋ธ๋์ prev๊ฐ ์ ๋ธ๋๊ฐ ๋๊ณ 
	cur->prev = node;  // ๋ค ๋ธ๋์ prev๊ฐ ๋ธ๋๊ฐ ๋๊ณ 
	node->next = cur;  // ๋ธ๋์ next๊ฐ ์ฝ์ํ  ๋ธ๋์ ๋ฐ๋ก ๋ค์ ๋ค์ด๊ฐ ๋ธ๋๊ฐ ๋  ์ ์๋๋ก
}
```

<br />

<span style="color:dodgerblue">**3) ์ฐ๊ฒฐ ๋ฆฌ์คํธ ์ญ์ **</span>

- [ 1 ]: ์ญ์ ํ  ๋ธ๋์ ์ ๋ธ๋๊ฐ ์ญ์ ํ  ๋ธ๋์ ๋ค๋ฅผ ๋ฐ๋ผ๋ณด๊ฒ ํ๋ค
- [ 2 ]: ์ญ์ ํ  ๋ธ๋์ ๋ค ๋ธ๋๊ฐ ์ญ์ ํ  ๋ธ๋์ ์์ ๋ฐ๋ผ๋ณด๊ฒ ํ๋ค
- [ 3 ]: ์ญ์ ํ  ๋ธ๋ ํ ๋น ํด์ 

![](https://images.velog.io/images/april_5/post/0cd265f8-f881-48f1-8a7c-b408b2399d86/image.png)

```c
// ์๋ฐฉํฅ ์ฐ๊ฒฐ ๋ฆฌ์คํธ ์ญ์  ํจ์
void removeFront() {
	Node* node = head->next;
	head->next = node->next;
	Node* next = node->next;
	next->prev = head; free(node);
}
```

<br />

<span style="color:dodgerblue">**4) ์ฐ๊ฒฐ ๋ฆฌ์คํธ ์ถ๋ ฅ**</span>

```c
// ์๋ฐฉํฅ ์ฐ๊ฒฐ ๋ฆฌ์คํธ ์ ์ฒด ์ถ๋ ฅ ํจ์
void show() {
      Node* cur = head->next;
      while (cur != tail) {
            printf("%d ", cur->data);
            cur = cur->next;
      }
}
```

<br />

<span style="color:dodgerblue">**5) ์ฐ๊ฒฐ ๋ฆฌ์คํธ ์ฌ์ฉํ๊ธฐ**</span>

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

### โจ tl;dr

- ์๋ฐฉํฅ ์ฐ๊ฒฐ ๋ฆฌ์คํธ์์๋ ๊ฐ ๋ธ๋๊ฐ ์ ๋ธ๋์ ๋ค ๋ธ๋์ ์ ๋ณด๋ฅผ ์ ์ฅํ๊ณ  ์๋ค
- ์๋ฐฉํฅ ์ฐ๊ฒฐ ๋ฆฌ์คํธ๋ฅผ ์ด์ฉํ๋ฉด ๋ฆฌ์คํธ์ ์์์๋ถํฐ ํน์ ๋ค์์๋ถํฐ ๋ชจ๋ ์ ๊ทผํ  ์ ์๋ค
