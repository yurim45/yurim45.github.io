---
title: '🌈 자료구조:: 큐(Queue)'
tags:
  - [data-structureㅤalgorithm]
permalink: /dataStructure/queue

navigation: true
toc: true
toc_sticky: true

date: 2021-11-04
last_modified_at: 2021-11-04
---

![]()

`개인 공부 과정을 기록합니다.`

### 🚀 What I Will Learn

- <span style="color:hotpink">**큐(Queue)**</span> 자료구조의 개념과 å 방법에 대해 이해하기
- C언어를 이용해 큐 자료구조 구현하기.......

><span style="color:hotpink">**큐(Queue)**</span>란? 뒤쪽으로 들어가서 앞쪽으로 나오는(<span style="background-color:pink">선입선출</span>) 자료 구조 형태.

![](https://images.velog.io/images/april_5/post/aa1ae86a-2cb6-4da6-9d6f-b4a2ee2a54ff/image.png)


---

# 큐(Queue)

## 1️⃣ 큐(Queue)란?

1) 뒤쪽으로 들어가서 앞쪽으로 나오는(<span style="background-color:pink">**선입선출**</span>) 자료 구조 형태.
2) 스케줄링, 탐색 알고리즘 등에서 다방면으로 활용됨
  - `PUSH`: 큐에 데이터 추가
  - `POP`: 큐에서 데이터 삭제

3) 예시: PUSH(7) – PUSH(5) – PUSH(4) – POP() – PUSH(6) – POP()

![](https://images.velog.io/images/april_5/post/e0e1d205-1cf1-448b-91e7-003822750407/image.png)

<br />

---

## 2️⃣ 스택의 구현

1) 큐(Queue)의 구현 방법에는
  - 배열을 이용한 구현 방법과
  - 연결 리스트를 이용한 구현 방법이 있다

2) 가장 기본적인 형태의 자료구조로 구현 난이도는 낮은 편


### ✔️ 배열을 이용한 큐의 구현

<span style="color:dodgerblue">**1) 큐의 선언**</span>

```c
#include <stdio.h>
#define SIZE 10000
#define INF 99999999

int queue[SIZE];
int front = 0;
int rear = 0;
```

<br />

<span style="color:dodgerblue">**2) 큐 삽입 함수**</span>

```c
void push(int data) {
  if (rear >= SIZE) {
    printf("큐 오버플로우가 발생했습니다.\n");
    return; }
  queue[rear++] = data;
}
```

<br />

<span style="color:dodgerblue">**3) 큐 추출 함수**</span>

```c
int pop() {
  if (front == rear) {
    printf("큐 언더플로우가 발생했습니다.\n");
    return -INF;
  }
  return queue[front++];
}
```

<br />

<span style="color:dodgerblue">**4) 큐 전체출력 함수**</span>

```c
void show() {
  printf("--- 큐의 앞 ---\n");
  for (int i = front; i < rear; i++) {
      printf("%d\n", queue[i]);
  }
  printf("--- 큐의 뒤 ---\n"); 
}
```

<br />

<span style="color:dodgerblue">**5) 완성된 큐 사용하기**</span>

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

### ✔️ 연결리스트를 이용한 큐의 구현

<span style="color:dodgerblue">**1) 큐의 선언**</span>

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

<span style="color:dodgerblue">**2) 큐 삽입 함수**</span>

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


<span style="color:dodgerblue">**3) 큐 추출 함수**</span>

![](https://images.velog.io/images/april_5/post/16667b53-392c-463f-8ed9-1f7338d4d666/image.png)


```c
int pop(Queue *queue) {
  if (queue->count == 0) {
    printf("큐 언더플로우가 발생했습니다.\n");
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


<span style="color:dodgerblue">**4) 큐 전체출력 함수**</span>

```c
void show(Queue *queue) {
  Node *cur = queue->front; 
  printf("--- 큐의 앞 ---\n"); 
  while (cur != NULL) {
      printf("%d\n", cur->data);
      cur = cur->next;
  }
  printf("--- 큐의 뒤 ---\n"); 
}
```

<br />


<span style="color:dodgerblue">**5) 완성된 큐 사용하기**</span>

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

### ✨ tl;dr

- 큐는 배열 혹은 연결 리스트를 이용해서 구현할 수 있다

  
  
  	
    
    
    
