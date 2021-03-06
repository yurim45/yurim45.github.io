---
title: "๐ ์๋ฃ๊ตฌ์กฐ:: ํ(Queue)"
tags:
  - [dataStructure-algorithm]
permalink: /data_structure/queue

navigation: true
toc: true
toc_sticky: true

date: 2021-11-04
last_modified_at: 2021-11-04
---

![]()

`๊ฐ์ธ ๊ณต๋ถ ๊ณผ์ ์ ๊ธฐ๋กํฉ๋๋ค.`

### ๐ What I Will Learn

- <span style="color:hotpink">**ํ(Queue)**</span> ์๋ฃ๊ตฌ์กฐ์ ๊ฐ๋๊ณผ รฅ ๋ฐฉ๋ฒ์ ๋ํด ์ดํดํ๊ธฐ
- C์ธ์ด๋ฅผ ์ด์ฉํด ํ ์๋ฃ๊ตฌ์กฐ ๊ตฌํํ๊ธฐ.......

> <span style="color:hotpink">**ํ(Queue)**</span>๋? ๋ค์ชฝ์ผ๋ก ๋ค์ด๊ฐ์ ์์ชฝ์ผ๋ก ๋์ค๋(<span style="background-color:pink">์ ์์ ์ถ</span>) ์๋ฃ ๊ตฌ์กฐ ํํ.

![](https://images.velog.io/images/april_5/post/aa1ae86a-2cb6-4da6-9d6f-b4a2ee2a54ff/image.png)

---

# ํ(Queue)

## 1๏ธโฃ ํ(Queue)๋?

1. ๋ค์ชฝ์ผ๋ก ๋ค์ด๊ฐ์ ์์ชฝ์ผ๋ก ๋์ค๋(<span style="background-color:pink">**์ ์์ ์ถ**</span>) ์๋ฃ ๊ตฌ์กฐ ํํ.
2. ์ค์ผ์ค๋ง, ํ์ ์๊ณ ๋ฆฌ์ฆ ๋ฑ์์ ๋ค๋ฐฉ๋ฉด์ผ๋ก ํ์ฉ๋จ

- `PUSH`: ํ์ ๋ฐ์ดํฐ ์ถ๊ฐ
- `POP`: ํ์์ ๋ฐ์ดํฐ ์ญ์ 

3. ์์: PUSH(7) โ PUSH(5) โ PUSH(4) โ POP() โ PUSH(6) โ POP()

![](https://images.velog.io/images/april_5/post/e0e1d205-1cf1-448b-91e7-003822750407/image.png)

<br />

---

## 2๏ธโฃ ์คํ์ ๊ตฌํ

1. ํ(Queue)์ ๊ตฌํ ๋ฐฉ๋ฒ์๋

- ๋ฐฐ์ด์ ์ด์ฉํ ๊ตฌํ ๋ฐฉ๋ฒ๊ณผ
- ์ฐ๊ฒฐ ๋ฆฌ์คํธ๋ฅผ ์ด์ฉํ ๊ตฌํ ๋ฐฉ๋ฒ์ด ์๋ค

2. ๊ฐ์ฅ ๊ธฐ๋ณธ์ ์ธ ํํ์ ์๋ฃ๊ตฌ์กฐ๋ก ๊ตฌํ ๋์ด๋๋ ๋ฎ์ ํธ

### โ๏ธ ๋ฐฐ์ด์ ์ด์ฉํ ํ์ ๊ตฌํ

<span style="color:dodgerblue">**1) ํ์ ์ ์ธ**</span>

```c
#include <stdio.h>
#define SIZE 10000
#define INF 99999999

int queue[SIZE];
int front = 0;
int rear = 0;
```

<br />

<span style="color:dodgerblue">**2) ํ ์ฝ์ ํจ์**</span>

```c
void push(int data) {
  if (rear >= SIZE) {
    printf("ํ ์ค๋ฒํ๋ก์ฐ๊ฐ ๋ฐ์ํ์ต๋๋ค.\n");
    return; }
  queue[rear++] = data;
}
```

<br />

<span style="color:dodgerblue">**3) ํ ์ถ์ถ ํจ์**</span>

```c
int pop() {
  if (front == rear) {
    printf("ํ ์ธ๋ํ๋ก์ฐ๊ฐ ๋ฐ์ํ์ต๋๋ค.\n");
    return -INF;
  }
  return queue[front++];
}
```

<br />

<span style="color:dodgerblue">**4) ํ ์ ์ฒด์ถ๋ ฅ ํจ์**</span>

```c
void show() {
  printf("--- ํ์ ์ ---\n");
  for (int i = front; i < rear; i++) {
      printf("%d\n", queue[i]);
  }
  printf("--- ํ์ ๋ค ---\n");
}
```

<br />

<span style="color:dodgerblue">**5) ์์ฑ๋ ํ ์ฌ์ฉํ๊ธฐ**</span>

```c
int main(void) {
  push(7);
  push(5);
  push(4);
  pop();
  push(6);
  pop();
  show();
  system("pause");
  return 0;
}

```

<br />
<br />

### โ๏ธ ์ฐ๊ฒฐ๋ฆฌ์คํธ๋ฅผ ์ด์ฉํ ํ์ ๊ตฌํ

<span style="color:dodgerblue">**1) ํ์ ์ ์ธ**</span>

```c
#include <stdio.h>
#include <stdlib.h>
#define INF 99999999

typedef struct {
  int data;
  struct Node *next;
} Node;

typedef struct {
  Node *front;
  Node *rear;
  int count;
} Queue;
```

<br />

<span style="color:dodgerblue">**2) ํ ์ฝ์ ํจ์**</span>

![](https://images.velog.io/images/april_5/post/601166af-a50e-4d33-af37-8f1eaa24222b/image.png)

```c
void push(Queue *queue, int data) {
  Node *node = (Node*)malloc(sizeof(Node));
  node->data = data;
  node->next = NULL;
  if (queue->count == 0) {
      queue->front = node;
  } else {
  queue->rear->next = node;
  }
  queue->rear = node;
  queue->count++;
}
```

<br />

<span style="color:dodgerblue">**3) ํ ์ถ์ถ ํจ์**</span>

![](https://images.velog.io/images/april_5/post/16667b53-392c-463f-8ed9-1f7338d4d666/image.png)

```c
int pop(Queue *queue) {
  if (queue->count == 0) {
    printf("ํ ์ธ๋ํ๋ก์ฐ๊ฐ ๋ฐ์ํ์ต๋๋ค.\n");
    return -INF;
  }
  Node *node = queue->front;
  int data = node->data;
  queue->front = node->next;
  free(node);
  queue->count--;
  return data;
}
```

<br />

<span style="color:dodgerblue">**4) ํ ์ ์ฒด์ถ๋ ฅ ํจ์**</span>

```c
void show(Queue *queue) {
  Node *cur = queue->front;
  printf("--- ํ์ ์ ---\n");
  while (cur != NULL) {
      printf("%d\n", cur->data);
      cur = cur->next;
  }
  printf("--- ํ์ ๋ค ---\n");
}
```

<br />

<span style="color:dodgerblue">**5) ์์ฑ๋ ํ ์ฌ์ฉํ๊ธฐ**</span>

```c
int main(void) {
  Queue queue;
  queue.front = queue.rear = NULL;
  queue.count = 0;
  push(&queue, 7);
  push(&queue, 5);
  push(&queue, 4);
  pop(&queue);
  push(&queue, 6);
  pop(&queue);
  show(&queue);
  system("pause");
  return 0;
}

```

<br /><br />

---

### โจ tl;dr

- ํ๋ ๋ฐฐ์ด ํน์ ์ฐ๊ฒฐ ๋ฆฌ์คํธ๋ฅผ ์ด์ฉํด์ ๊ตฌํํ  ์ ์๋ค
