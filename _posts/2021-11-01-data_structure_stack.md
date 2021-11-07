---
title: '🌈 자료구조:: 스택(Stack)'
tags:
  - [data-structure💥algorithm]
permalink: /dataStructure/stack

navigation: true
toc: true
toc_sticky: true

date: 2021-11-01
last_modified_at: 2021-11-01
---

![]()

`개인 공부 과정을 기록합니다.`

### 🚀 What I Will Learn

- <span style="color:hotpink">**스택**</span>자료구조의 개념과 활용 방법에 대해 이해하기
- C언어를 이용해 스택 자료구조 구현하기

![](https://images.velog.io/images/april_5/post/1561d0b1-b096-4ca2-92e6-d65b0941c054/image.png)

---

# 스택(Stack)

## 1️⃣ 스택란?

1. 스택은 한쪽으로 들어가서 한쪽으로 나오는 자료구조이다.
2. 수식 계산 등의 알고리즘에서 다방면으로 활용된다

- PUSH: 스택에 데이터 추가
- POP: 스택에 데이터 제거

![](https://images.velog.io/images/april_5/post/2ccc4199-48d7-497b-9c07-dc86334f5621/image.png)

<br />

---

## 2️⃣ 스택의 구현

1. 스택의 구현 방법에는

- 배열을 이용한 구현 방법과
- 연결 리스트를 이용한 구현 방법이 있다

2. 가장 기본적인 형태의 자료구조로, 구현 난이도는 낮은편

<br />

### ✔️ 배열을 이용한 스택 구현

<span style="color:dodgerblue">**1) 스택 선언**</span>

```c
#include <stdio.h>
#define SIZE 10000    // 스택 크기
#define INF 99999999  //

int stack[SIZE]; // 스택 크기 선언
int top = -1;
```

<br />

<span style="color:dodgerblue">**2) 스택 삽입 함수**</span>

```c
void push(int data) {
  if (top == SIZE - 1) {
	printf("스택 오버플로우가 발생했습니다.\n");
	return;
  }
  stack[++top] = data;
}
```

<br />

<span style="color:dodgerblue">**3) 스택 추출 함수**</span>

```c
int pop() {
  if (top == -1) {
	printf("스택 언더플로우가 발생했습니다.\n");
	return -INF;
  }
  return stack[top--];
}
```

<br />

<span style="color:dodgerblue">**4) 스택 전체 출력 함수**</span>

```c
void show() {
  printf("--- 스택의 최상단 ---\n");
	for (int i = top; i >= 0; i--) {
    	  printf("%d\n", stack[i]);
  	}
  printf("--- 스택의 최하단 ---\n");
}
```

<br />

<span style="color:dodgerblue">**5) 완성된 스택 사용하기**</span>

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

### ✔️ 연결리스트를 이용한 스택 구현

<span style="color:dodgerblue">**1) 스택 선언**</span>

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

<span style="color:dodgerblue">**2) 스택 삽입 함수**</span>

![](https://images.velog.io/images/april_5/post/d2c21874-652b-4716-9c53-8858024aff66/image.png)

```c
void push(Stack *stack, int data) {
  Node *node = (Node*) malloc(sizeof(Node)); node->data = data;
  node->next = stack->top;
  stack->top = node;
}
```

<br />

<span style="color:dodgerblue">**3) 스택 추출 함수**</span>

![](https://images.velog.io/images/april_5/post/b52722cb-0f38-4b84-a253-89a8b8096c49/image.png)

```c
int pop(Stack *stack) {
  if (stack->top == NULL) {
	printf("스택 언더플로우가 발생했습니다.\n");
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

<span style="color:dodgerblue">**4) 스택 전체 출력 함수**</span>

```c
void show(Stack *stack) {
  Node *cur = stack->top;
  printf("--- 스택의 최상단 ---\n");

  while (cur != NULL) {
      printf("%d\n", cur->data);
      cur = cur->next;
  }
  printf("--- 스택의 최하단 ---\n");
}
```

<br />

<span style="color:dodgerblue">**5) 완성된 스택 사용하기**</span>

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

### ✨ tl;dr

- 스택은 배열 혹은 연결 리스트를 이용해서 구현할 수 있다
