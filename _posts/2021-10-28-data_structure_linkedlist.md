---
title: "๐ ์๋ฃ๊ตฌ์กฐ:: ์ฐ๊ฒฐ๋ฆฌ์คํธ"
tags:
  - [dataStructure-algorithm]
permalink: /data_structure/linked_list

navigation: true
toc: true
toc_sticky: true

date: 2021-10-28
last_modified_at: 2021-10-28
---

![]()

`๊ฐ์ธ ๊ณต๋ถ ๊ณผ์ ์ ๊ธฐ๋กํฉ๋๋ค.`

### ๐ What I Will Learn

- <span style="color:hotpink">**์ฐ๊ฒฐ ๋ฆฌ์คํธ**</span>์ ํ์์ฑ๊ณผ ์ฌ์ฉ์ ๋ํด ํ์ตํ๋ค
- C์ธ์ด๋ฅผ ํ์ฉํ์ฌ ๋จ์ผ ์ฐ๊ฒฐ ๋ฆฌ์คํธ๋ฅผ ๊ตฌํํด๋ณธ๋ค...

<br />

---

# ์ฐ๊ฒฐ ๋ฆฌ์คํธ(Linked List)

## 1๏ธโฃ ์ฐ๊ฒฐ ๋ฆฌ์คํธ์ ํ์์ฑ

1. ์ผ๋ฐ์ ์ผ๋ก ๋ฐฐ์ด์ ์ฌ์ฉํ์ฌ ๋ฐ์ดํฐ๋ฅผ ์์ฐจ์ ์ผ๋ก ์ ์ฅํ๊ณ , ๋์ดํ  ์ ์์ง๋ง
2. ๋ฐฐ์ด์ ์ฌ์ฉํ๋ ๊ฒฝ์ฐ, ๋ฉ๋ชจ๋ฆฌ ๊ณต๊ฐ์ด ๋ถํ์ํ๊ฒ ๋ญ๋น๋  ์ ์๋๋ฏ๋ก
3. ์ด๋ ์ฐ๊ฒฐ ๋ฆฌ์คํธ๋ก ๋์ฒดํ  ์ ์๋ค

<br />

### โ๏ธ ๋ฐฐ์ด ๊ธฐ๋ฐ ๋ฆฌ์คํธ๋?

1. ๋ฐ์ดํฐ๋ฅผ ์์ฐจ์ ์ผ๋ก ์ ์ฅ, ์ฒ๋ฆฌํ  ๋๋ ๋ฐฐ์ด ๊ธฐ๋ฐ์ ๋ฆฌ์คํธ๋ฅผ ์ด์ฉ

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

> ๊ทธ๋ ๋ค๋ฉด?! <span style="color:hotpink">**ํน์ ํ ์์น์ ์์๋ฅผ ์ญ์ ํ๋ ํจ์**</span>๋ ์ด๋ป๊ฒ ๋ง๋ค ์ ์์๊น?

```c
// ํน์ ํ index๋ฅผ ๋ฐ์์ ํด๋น index ์์น์ ๋ท ์์๋ฅผ ์์ผ๋ก ๋น๊ธฐ๋ ๋ฐฉ์์ผ๋ก ๊ตฌํ
void removeAt(int index) {
	for (int i = index; i < count - 1; i++) {
		arr[i] = arr[i + 1];
	}
	count--;
}
```

### โ๏ธ ๋ฐฐ์ด ๊ธฐ๋ฐ ๋ฆฌ์คํธ์ ํน์ง

- ๋ฐฐ์ด๋ก ๋ง๋ค์์ผ๋ฏ๋ก ํน์ ํ ์์น์ ์์์ ์ฆ์ ์ ๊ทผํ  ์ ์๋ค๋ ์ฅ์ 
  - `index`๋ฅผ ํ์ฉ
- ๋ฐ์ดํฐ๊ฐ ๋ค์ด๊ฐ ๊ณต๊ฐ์ ๋ฏธ๋ฆฌ ๋ฉ๋ชจ๋ฆฌ์ ํ ๋นํ๋ค๋ ๋จ์ 
  - `#define INF 10000`
- ์ํ๋ ์์น๋ก์ ์ฝ์ ๋๋ ์ญ์ ๊ฐ ๋นํจ์จ์ 
  - for๋ฌธ์ผ๋ก ์์ผ๋ก ๋น๊ธฐ๊ฑฐ๋ ๋ค๋ก ๋ฐ์ด์ ์ถ๊ฐ ๋๋ ์ญ์ ํ๋ ์์ ์ฝ๋

<br /><br />

---

## 2๏ธโฃ ์ฐ๊ฒฐ ๋ฆฌ์คํธ

- ์ผ๋ฐ์ ์ผ๋ก ์ฐ๊ฒฐ ๋ฆฌ์คํธ๋ <span style="color:hotpink">**๊ตฌ์กฐ์ฒด**</span>์ <span style="color:hotpink">**ํฌ์ธํฐ**</span>๋ฅผ ํจ๊ป ์ฌ์ฉํ์ฌ ๊ตฌํ
- ์ฐ๊ฒฐ ๋ฆฌ์คํธ๋ ๋ฆฌ์คํธ์ ์ค๊ฐ ์ง์ ์ ๋ธ๋๋ฅผ ์ถ๊ฐํ๊ฑฐ๋ ์ญ์ ํ  ์ ์์ด์ผ ํจ
- <span style="color:hotpink">**ํ์ํ  ๋ ๋ง๋ค ๋ฉ๋ชจ๋ฆฌ ๊ณต๊ฐ์ ํ ๋น**</span> ๋ฐ๋๋ค

> ๐ **์ฐธ๊ณ !**

- [ํฌ์ธํฐ๋?](https://velog.io/@april_5/ํฌ์ธํฐpointer-๊ฐ๋-์ดํด) โฌ๏ธํด๋ฆญ
- ๊ตฌ์กฐ์ฒด๋?

<br />

### โ๏ธ ๋จ์ผ ์ฐ๊ฒฐ๋ฆฌ์คํธ

- ๋จ์ผ ์ฐ๊ฒฐ ๋ฆฌ์คํธ๋ ๋ฐ์ดํฐ**`data`**์ ๋ค์ ๋ธ๋๋ฅผ ๊ฐ๋ฆฌํค๋ **`next`** ๋ก ๊ตฌ์ฑ๋์ด ์๋ค
- **ํฌ์ธํฐ**๋ฅผ ์ด์ฉํด ๋จ๋ฐฉํฅ์ ์ผ๋ก ๋ค์ ๋ธ๋๋ฅผ ๊ฐ๋ฆฌํจ๋ค
- ์ฐ๊ฒฐ ๋ฆฌ์คํธ์ ์์ ๋ธ๋๋ฅผ **`ํค๋(Head)`**๋ผ๊ณ  ํ๋ฉฐ ๋ณ๋๋ก ๊ด๋ฆฌํ๋ค
- ๋ค์ ๋ธ๋๊ฐ ์๋ ๋ ๋ธ๋์ ๋ค์ ์์น ๊ฐ์ผ๋ก `**NULL`\*\*์ ์ถ๊ฐํ๋ค

![](https://images.velog.io/images/april_5/post/628562a0-00f6-40be-a9ec-29d4a0c3d4f4/image.png)

<br />

### โ๏ธ ๋จ์ผ ์ฐ๊ฒฐ๋ฆฌ์คํธ ๊ตฌํ

<span style="color:dodgerblue">**1) ์ฐ๊ฒฐ ๋ฆฌ์คํธ ๊ตฌ์กฐ์ฒด ๋ง๋ค๊ธฐ**</span>

```c
#include <stdio.h>
#include <stdlib.h>

typedef struct {
  int data;
  struct Node *next;  // ๋ค์ ๋ธ๋๋ฅผ ๊ฐ๋ฆฌํค๋ ๋ณ์. ํฌ์ธํฐ ๋ณ์
} Node;

Node *head;  // ํฌ์ธํฐ ๋ณ์๋ฅผ ํ์ฉํด ๋์  ํ ๋น์ด ์ด๋ฃจ์ด์ง๋๋ก ํ๋ค
```

<br />

<span style="color:dodgerblue">**2) ์ฐ๊ฒฐ ๋ฆฌ์คํธ ๊ตฌ์กฐ์ฒด ์ฌ์ฉํด๋ณด๊ธฐ**</span>

- `malloc()` ํจ์๋ก ๋์  ํ ๋นํ๊ธฐ

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

- ๊ฒฐ๊ณผ๋ 1, 2๊ฐ ์ถ๋ ฅ๋๋ฉฐ ์๋์ ๊ทธ๋ฆผ์ ๋ชจ์์ด ์์ฑ

![](https://images.velog.io/images/april_5/post/47afd59d-74f0-4485-a7bd-884a315273a9/image.png)

<br />

<span style="color:dodgerblue">**3) ๋ธ๋ ์ฝ์**</span>

![](https://images.velog.io/images/april_5/post/f558b7df-6932-4096-88f6-1207ffb48e00/image.png)

- ์ฐ๊ฒฐ ๋ฆฌ์คํธ ์ฝ์ ํจ์ ๊ตฌํ

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

<span style="color:dodgerblue">**4) ๋ธ๋ ์ญ์ **</span>

- ์ฐ๊ฒฐ ๋ฆฌ์คํธ ์ญ์  ํจ์ ๊ตฌํ

```c
void removeFront(Node *root) {
  Node *front = root->next;
  root->next = front->next;
  free(front);
}
```

<br />

<span style="color:dodgerblue">**5) ํ ๋น๋ ๋ฉ๋ชจ๋ฆฌ ํด์ **</span>

- `free()` ํจ์๋ก ๋ธ๋๋ฅผ ํ๋์ฉ ์ ๊ทผํด์ ํด์ ํด์ผ ํจ

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

<span style="color:dodgerblue">**6) ์ฐ๊ฒฐ ๋ฆฌ์คํธ ์ ์ฒด ์ถ๋ ฅ ํจ์**</span>

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

<span style="color:dodgerblue">**7) ์์ฑ๋ ์ฐ๊ฒฐ ๋ฆฌ์คํธ ์ฌ์ฉํ๊ธฐ**</span>

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

### โ๏ธ ์ฐ๊ฒฐ ๋ฆฌ์คํธ ํน์ง

- ์ฝ์๊ณผ ์ญ์ ๊ฐ ๋ฐฐ์ด์ ๋นํด ๊ฐ๋จํ๋ค๋ ์ฅ์ 
- ๋ฐฐ์ด๊ณผ ๋ค๋ฅด๊ฒ ํน์  ์ธ๋ฑ์ค๋ก ์ฆ์ ์ ๊ทผํ์ง ๋ชปํ๊ณ , ์์๋ฅผ ์ฐจ๋ก๋๋ก ๊ฒ์ํด์ผ ํ๋ค๋ ๋จ์ 
- ์ถ๊ฐ์ ์ธ ํฌ์ธํฐ ๋ณ์๊ฐ ์ฌ์ฉ๋๋ฏ๋ก ๋ฉ๋ชจ๋ฆฌ ๊ณต๊ฐ์ด ๋ญ๋น๋๋ค.....

<br /><br />

---

### โจ tl;dr

- ์ฐ๊ฒฐ ๋ฆฌ์คํธ๋ ๋ฐ์ดํฐ๋ฅผ ์ ํ์ ์ผ๋ก ์ ์ฅํ๊ณ  ์ฒ๋ฆฌํ๋ ํ ๋ฐฉ๋ฒ์ด๋ค
- ๊ธฐ์กด์ ๋ฐฐ์ด์ ์ด์ฉํ์ ๋ ๋ณด๋ค ์ฝ์๊ณผ ์ญ์ ๊ฐ ๋ง์ ๊ฒฝ์ฐ์ ํจ์จ์ ์ด๋ค
- ๋ค๋ง, ํน์  ์ธ๋ฑ์ค์ ๋ฐ๋ก ์ฐธ์กฐํด์ผ ํ  ๋๊ฐ ๋ง๋ค๋ฉด ๋ฐฐ์ด์ ์ด์ฉํ๋ ๊ฒ์ด ํจ์จ์ ์ด๋ค....
