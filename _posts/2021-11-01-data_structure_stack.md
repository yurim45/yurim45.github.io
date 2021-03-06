---
title: "๐ ์๋ฃ๊ตฌ์กฐ:: ์คํ(Stack)"
tags:
  - [dataStructure-algorithm]
permalink: /data_structure/stack

navigation: true
toc: true
toc_sticky: true

date: 2021-11-01
last_modified_at: 2021-11-01
---

![]()

`๊ฐ์ธ ๊ณต๋ถ ๊ณผ์ ์ ๊ธฐ๋กํฉ๋๋ค.`

### ๐ What I Will Learn

- <span style="color:hotpink">**์คํ**</span>์๋ฃ๊ตฌ์กฐ์ ๊ฐ๋๊ณผ ํ์ฉ ๋ฐฉ๋ฒ์ ๋ํด ์ดํดํ๊ธฐ
- C์ธ์ด๋ฅผ ์ด์ฉํด ์คํ ์๋ฃ๊ตฌ์กฐ ๊ตฌํํ๊ธฐ

![](https://images.velog.io/images/april_5/post/1561d0b1-b096-4ca2-92e6-d65b0941c054/image.png)

---

# ์คํ(Stack)

## 1๏ธโฃ ์คํ๋?

1. ์คํ์ ํ์ชฝ์ผ๋ก ๋ค์ด๊ฐ์ ํ์ชฝ์ผ๋ก ๋์ค๋ ์๋ฃ๊ตฌ์กฐ์ด๋ค.
2. ์์ ๊ณ์ฐ ๋ฑ์ ์๊ณ ๋ฆฌ์ฆ์์ ๋ค๋ฐฉ๋ฉด์ผ๋ก ํ์ฉ๋๋ค

- PUSH: ์คํ์ ๋ฐ์ดํฐ ์ถ๊ฐ
- POP: ์คํ์ ๋ฐ์ดํฐ ์ ๊ฑฐ

![](https://images.velog.io/images/april_5/post/2ccc4199-48d7-497b-9c07-dc86334f5621/image.png)

<br />

---

## 2๏ธโฃ ์คํ์ ๊ตฌํ

1. ์คํ์ ๊ตฌํ ๋ฐฉ๋ฒ์๋

- ๋ฐฐ์ด์ ์ด์ฉํ ๊ตฌํ ๋ฐฉ๋ฒ๊ณผ
- ์ฐ๊ฒฐ ๋ฆฌ์คํธ๋ฅผ ์ด์ฉํ ๊ตฌํ ๋ฐฉ๋ฒ์ด ์๋ค

2. ๊ฐ์ฅ ๊ธฐ๋ณธ์ ์ธ ํํ์ ์๋ฃ๊ตฌ์กฐ๋ก, ๊ตฌํ ๋์ด๋๋ ๋ฎ์ํธ

<br />

### โ๏ธ ๋ฐฐ์ด์ ์ด์ฉํ ์คํ ๊ตฌํ

<span style="color:dodgerblue">**1) ์คํ ์ ์ธ**</span>

```c
#include <stdio.h>
#define SIZE 10000    // ์คํ ํฌ๊ธฐ
#define INF 99999999  //

int stack[SIZE]; // ์คํ ํฌ๊ธฐ ์ ์ธ
int top = -1;
```

<br />

<span style="color:dodgerblue">**2) ์คํ ์ฝ์ ํจ์**</span>

```c
void push(int data) {
  if (top == SIZE - 1) {
	printf("์คํ ์ค๋ฒํ๋ก์ฐ๊ฐ ๋ฐ์ํ์ต๋๋ค.\n");
	return;
  }
  stack[++top] = data;
}
```

<br />

<span style="color:dodgerblue">**3) ์คํ ์ถ์ถ ํจ์**</span>

```c
int pop() {
  if (top == -1) {
	printf("์คํ ์ธ๋ํ๋ก์ฐ๊ฐ ๋ฐ์ํ์ต๋๋ค.\n");
	return -INF;
  }
  return stack[top--];
}
```

<br />

<span style="color:dodgerblue">**4) ์คํ ์ ์ฒด ์ถ๋ ฅ ํจ์**</span>

```c
void show() {
  printf("--- ์คํ์ ์ต์๋จ ---\n");
	for (int i = top; i >= 0; i--) {
    	  printf("%d\n", stack[i]);
  	}
  printf("--- ์คํ์ ์ตํ๋จ ---\n");
}
```

<br />

<span style="color:dodgerblue">**5) ์์ฑ๋ ์คํ ์ฌ์ฉํ๊ธฐ**</span>

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

### โ๏ธ ์ฐ๊ฒฐ๋ฆฌ์คํธ๋ฅผ ์ด์ฉํ ์คํ ๊ตฌํ

<span style="color:dodgerblue">**1) ์คํ ์ ์ธ**</span>

```c
#include <stdio.h>
#include <stdlib.h>
#define INF 99999999

typedef struct {
  int data;
  struct Node *next;
} Node;
typedef struct {
  Node *top;
} Stack;
```

<br />

<span style="color:dodgerblue">**2) ์คํ ์ฝ์ ํจ์**</span>

![](https://images.velog.io/images/april_5/post/d2c21874-652b-4716-9c53-8858024aff66/image.png)

```c
void push(Stack *stack, int data) {
  Node *node = (Node*) malloc(sizeof(Node)); node->data = data;
  node->next = stack->top;
  stack->top = node;
}
```

<br />

<span style="color:dodgerblue">**3) ์คํ ์ถ์ถ ํจ์**</span>

![](https://images.velog.io/images/april_5/post/b52722cb-0f38-4b84-a253-89a8b8096c49/image.png)

```c
int pop(Stack *stack) {
  if (stack->top == NULL) {
	printf("์คํ ์ธ๋ํ๋ก์ฐ๊ฐ ๋ฐ์ํ์ต๋๋ค.\n");
        return -INF;
  }
  Node *node = stack->top;
  int data = node->data;
  stack->top = node->next;
  free(node);
  return data;
}
```

<br />

<span style="color:dodgerblue">**4) ์คํ ์ ์ฒด ์ถ๋ ฅ ํจ์**</span>

```c
void show(Stack *stack) {
  Node *cur = stack->top;
  printf("--- ์คํ์ ์ต์๋จ ---\n");

  while (cur != NULL) {
      printf("%d\n", cur->data);
      cur = cur->next;
  }
  printf("--- ์คํ์ ์ตํ๋จ ---\n");
}
```

<br />

<span style="color:dodgerblue">**5) ์์ฑ๋ ์คํ ์ฌ์ฉํ๊ธฐ**</span>

```c
int main(void) {
  Stack stack;
  stack.top = NULL;
  show(&stack);
  push(&stack, 7);
  push(&stack, 5);
  push(&stack, 4);
  pop(&stack);
  push(&stack, 6);
  pop(&stack);
  show(&stack);
  system("pause");
  return 0;
}
```

<br /><br />

---

### โจ tl;dr

- ์คํ์ ๋ฐฐ์ด ํน์ ์ฐ๊ฒฐ ๋ฆฌ์คํธ๋ฅผ ์ด์ฉํด์ ๊ตฌํํ  ์ ์๋ค
