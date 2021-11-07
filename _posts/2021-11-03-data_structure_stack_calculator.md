---
title: '🌈 자료구조:: 스택(Stack) 계산기 만들기'
tags:
  - [data-structure💥algorithm]
permalink: /dataStructure/stackCalculator

navigation: true
toc: true
toc_sticky: true

date: 2021-11-03
last_modified_at: 2021-11-03
---

![]()

`개인 공부 과정을 기록합니다.`

### 🚀 What I Will Learn

- <span style="color:hotpink">**스택을 활용한 계산기 만들기
  **</span>
  - 중위 표기법을 후위 표기법으로 변환하는 방법을 이해한다
  - 후위 표기법을 계산하여 결과 값을 도출하는 방법을 이해한다

> <span style="color:hotpink">**중위 표기법**</span>이란? 일반적으로 사람이 수식을 표기할 때 사용하는 표기 방법. 예시) 7 \* 5 + 3

> <span style="color:hotpink">**후위 표기법**</span>이란? 컴퓨터가 계산하기에 편한 수식의 형태. 후위 표기법에서 연산자는 뒤쪽에 위치. 예시) 7 5 \* 3 +

---

# 스택(Stack)을 활용한 계산기 만들기

### ✔️ 중위 표기법이란?

1. 일반적으로 사람이 수식을 표기할 때 사용하는 표기 방법

- 예시) 7 \* 5 + 3

### ✔️ 후위 표기법이란?

1. 컴퓨터가 계산하기에 편한 수식의 형태
2. 후위 표기법에서 연산자는 뒤쪽에 위치

- 예시) 7 5 \* 3 +

<br />

---

## 1️⃣ 스택을 활용해 수식을 계산하는 방법

### ✔️ 스택을 활용해 수식을 계산하는 방법

1. 수식을 후위 표기법으로 변환
2. 후위 표기법을 계산하여 결과 도출

<br />

### ✔️ 스택을 활용해 계산기 만들기1:: 스택 구현

<span style="color:dodgerblue">**1) 스택 구현**</span>

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <stdlib.h>
#include <string.h>  // 문자열 처리를 위해
#define INF 99999999

typedef struct {  // 구조체 정의
  char data[100];
  struct Node *next;  // 다음 노드로 연결하기 위해 선언
} Node;
typedef struct {
  Node *top;  // top pointer 선언
} Stack;
```

<br />

<span style="color:dodgerblue">**2) 스택 함수 구현**</span>

```c
void push(Stack *stack, char *data) {
  Node *node = (Node*)malloc(sizeof(Node));
  strcpy(node->data, data);
  node->next = stack->top;
  stack->top = node;
}

char* getTop(Stack *stack) {
  Node *top = stack->top;
  return top->data;
}
```

```c
char* pop(Stack *stack) {
  if (stack->top == NULL) {
  printf("스택 언더플로우가 발생했습니다.\n");
      return -INF;
  }
  Node *node = stack->top;
  char *data = (char*)malloc(sizeof(char) * 100);
  strcpy(data, node->data);
  stack->top = node->next;
  free(node);
  return data;
}
```

<br />

### ✔️ 스택을 활용해 계산기 만들기2:: 중위 표기법을 후위 표기법으로 바꾸기

1. 피연산자가 들어오면 바로 출력
2. 연산자가 들어오면 자기보다 우선 순위가 높거나 같은 것들을 빼고 자신을 스택에 담기
3. 여는 괄호 `(`를 만나면 무조건 스택에 담기
4. 닫는 괄호 `)`를 만나면 `(`를 만날 때까지 스택에서 출력

<br />

<span style="color:dodgerblue">**3) 후위 표기법으로 변환:: 우선순위 함수 만들기**</span>

```c
int getPriority(char *i) {
  if (!strcmp(i, "(")) return 0;
  if (!strcmp(i, "+") || !strcmp(i, "-")) return 1;
  if (!strcmp(i, "*") || !strcmp(i, "/")) return 2; return 3;
}
```

<br />

<span style="color:dodgerblue">**4) 후위 표기법으로 변환:: 변환 함수 만들기
**</span>

```c
char* transition(Stack *stack, char **s, int size) {
  char res[1000] = "";
  for (int i = 0; i < size; i++) {
    if (!strcmp(s[i], "+") || !strcmp(s[i], "-") || !strcmp(s[i], "*") || !strcmp(s[i], "/")) {
      while (stack->top != NULL && getPriority(getTop(stack)) >= getPriority(s[i])) {
        strcat(res, pop(stack)); strcat(res, " ");
      }
      push(stack, s[i]);
    }
    else if (!strcmp(s[i], "(")) push(stack, s[i]);
    else if (!strcmp(s[i], ")")) {
      while (strcmp(getTop(stack), "(")) {
        strcat(res, pop(stack)); strcat(res, " ");
      }
      pop(stack);
    }
    else strcat(res, s[i]); strcat(res, " ");
  }
  while (stack->top != NULL) {
    strcat(res, pop(stack)); strcat(res, " ");
  }
return res;
}

```

<br />

### ✔️ 후위 표기법을 계산하는 방법

1. 피연산자가 들어오면 스택에 담기
2. 연산자를 만나면 스택에서 두 개의 연산자를 꺼내서 연산한 뒤에 그 결과를 스택에 담기
3. 연산을 마친 뒤에 스택에 남아있는 하나의 피연산자가 연산 수행 결과

<span style="color:dodgerblue">**5) 후위 표기법 계산**</span>

```c
void calculate(Stack *stack, char **s, int size) {
  int x, y, z;
  for (int i = 0; i < size; i++) {
    if (!strcmp(s[i], "+") || !strcmp(s[i], "-") || !strcmp(s[i], "*") || !strcmp(s[i], "/")) {
          x = atoi(pop(stack));
          y = atoi(pop(stack));
          if (!strcmp(s[i],
          if (!strcmp(s[i],
          if (!strcmp(s[i],
          if (!strcmp(s[i],
          char buffer[100];
          sprintf(buffer, "%d", z);
          push(stack, buffer);
    } else {
          push(stack, s[i]);
    }
  }
    printf("%s ", pop(stack));
}
```

<br />

<span style="color:dodgerblue">**6) 만들어진 계산기 사용하기 1**</span>

```c
int main(void) {
  Stack stack;
  stack.top = NULL;
  char a[100] = "( ( 3 + 4 ) * 5 ) - 5 * 7 * 5 - 5 * 10";
  int size = 1;
  for (int i = 0; i < strlen(a); i++) {
    if (a[i] == ' ') size++;
  }
  char *ptr = strtok(a, " ");
  char **input = (char**)malloc(sizeof(char*) * size);
  for (int i = 0; i < size; i++) {
    input[i] = (char*)malloc(sizeof(char) * 100);
  }
  for (int i = 0; i < size; i++) {
    strcpy(input[i], ptr);
    ptr = strtok(NULL, " ");
  }
  char b[1000] = "";
  strcpy(b, transition(&stack, input, size));
  printf("후위 표기법: %s\n", b); system("pause");
  return 0;
}
```

<br />

<span style="color:dodgerblue">**6) 만들어진 계산기 사용하기 2**</span>

```c
size = 1;
for (int i = 0; i < strlen(b) - 1; i++) { // 마지막은 항상 공백이 들어가므로 1을 빼기
  if (b[i] == ' ') size++;
}
char *ptr2 = strtok(b, " ");
for (int i = 0; i < size; i++) {
  strcpy(input[i], ptr2);
  ptr2 = strtok(NULL, " ");
}
calculate(&stack, input, size);
system("pause");
return 0;
```

<br /><br />

---

### ✨ tl;dr

- 스택을 활용하여 중위 표기법을 후위 표기법으로 변환할 수 있다
- 스택을 활용하여 후위 표기법을 연산할 수 있다
