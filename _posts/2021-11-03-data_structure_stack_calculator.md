---
title: "π μλ£κ΅¬μ‘°:: μ€ν(Stack) κ³μ°κΈ° λ§λ€κΈ°"
tags:
  - [dataStructure-algorithm]
permalink: /data_structure/stack_calculator

navigation: true
toc: true
toc_sticky: true

date: 2021-11-03
last_modified_at: 2021-11-03
---

![]()

`κ°μΈ κ³΅λΆ κ³Όμ μ κΈ°λ‘ν©λλ€.`

### π What I Will Learn

- <span style="color:hotpink">**μ€νμ νμ©ν κ³μ°κΈ° λ§λ€κΈ°
  **</span>
  - μ€μ νκΈ°λ²μ νμ νκΈ°λ²μΌλ‘ λ³ννλ λ°©λ²μ μ΄ν΄νλ€
  - νμ νκΈ°λ²μ κ³μ°νμ¬ κ²°κ³Ό κ°μ λμΆνλ λ°©λ²μ μ΄ν΄νλ€

> <span style="color:hotpink">**μ€μ νκΈ°λ²**</span>μ΄λ? μΌλ°μ μΌλ‘ μ¬λμ΄ μμμ νκΈ°ν  λ μ¬μ©νλ νκΈ° λ°©λ². μμ) 7 \* 5 + 3

> <span style="color:hotpink">**νμ νκΈ°λ²**</span>μ΄λ? μ»΄ν¨ν°κ° κ³μ°νκΈ°μ νΈν μμμ νν. νμ νκΈ°λ²μμ μ°μ°μλ λ€μͺ½μ μμΉ. μμ) 7 5 \* 3 +

---

# μ€ν(Stack)μ νμ©ν κ³μ°κΈ° λ§λ€κΈ°

### βοΈ μ€μ νκΈ°λ²μ΄λ?

1. μΌλ°μ μΌλ‘ μ¬λμ΄ μμμ νκΈ°ν  λ μ¬μ©νλ νκΈ° λ°©λ²

- μμ) 7 \* 5 + 3

### βοΈ νμ νκΈ°λ²μ΄λ?

1. μ»΄ν¨ν°κ° κ³μ°νκΈ°μ νΈν μμμ νν
2. νμ νκΈ°λ²μμ μ°μ°μλ λ€μͺ½μ μμΉ

- μμ) 7 5 \* 3 +

<br />

---

## 1οΈβ£ μ€νμ νμ©ν΄ μμμ κ³μ°νλ λ°©λ²

### βοΈ μ€νμ νμ©ν΄ μμμ κ³μ°νλ λ°©λ²

1. μμμ νμ νκΈ°λ²μΌλ‘ λ³ν
2. νμ νκΈ°λ²μ κ³μ°νμ¬ κ²°κ³Ό λμΆ

<br />

### βοΈ μ€νμ νμ©ν΄ κ³μ°κΈ° λ§λ€κΈ°1:: μ€ν κ΅¬ν

<span style="color:dodgerblue">**1) μ€ν κ΅¬ν**</span>

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <stdlib.h>
#include <string.h>  // λ¬Έμμ΄ μ²λ¦¬λ₯Ό μν΄
#define INF 99999999

typedef struct {  // κ΅¬μ‘°μ²΄ μ μ
  char data[100];
  struct Node *next;  // λ€μ λΈλλ‘ μ°κ²°νκΈ° μν΄ μ μΈ
} Node;
typedef struct {
  Node *top;  // top pointer μ μΈ
} Stack;
```

<br />

<span style="color:dodgerblue">**2) μ€ν ν¨μ κ΅¬ν**</span>

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
  printf("μ€ν μΈλνλ‘μ°κ° λ°μνμ΅λλ€.\n");
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

### βοΈ μ€νμ νμ©ν΄ κ³μ°κΈ° λ§λ€κΈ°2:: μ€μ νκΈ°λ²μ νμ νκΈ°λ²μΌλ‘ λ°κΎΈκΈ°

1. νΌμ°μ°μκ° λ€μ΄μ€λ©΄ λ°λ‘ μΆλ ₯
2. μ°μ°μκ° λ€μ΄μ€λ©΄ μκΈ°λ³΄λ€ μ°μ  μμκ° λκ±°λ κ°μ κ²λ€μ λΉΌκ³  μμ μ μ€νμ λ΄κΈ°
3. μ¬λ κ΄νΈ `(`λ₯Ό λ§λλ©΄ λ¬΄μ‘°κ±΄ μ€νμ λ΄κΈ°
4. λ«λ κ΄νΈ `)`λ₯Ό λ§λλ©΄ `(`λ₯Ό λ§λ  λκΉμ§ μ€νμμ μΆλ ₯

<br />

<span style="color:dodgerblue">**3) νμ νκΈ°λ²μΌλ‘ λ³ν:: μ°μ μμ ν¨μ λ§λ€κΈ°**</span>

```c
int getPriority(char *i) {
  if (!strcmp(i, "(")) return 0;
  if (!strcmp(i, "+") || !strcmp(i, "-")) return 1;
  if (!strcmp(i, "*") || !strcmp(i, "/")) return 2; return 3;
}
```

<br />

<span style="color:dodgerblue">**4) νμ νκΈ°λ²μΌλ‘ λ³ν:: λ³ν ν¨μ λ§λ€κΈ°
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

### βοΈ νμ νκΈ°λ²μ κ³μ°νλ λ°©λ²

1. νΌμ°μ°μκ° λ€μ΄μ€λ©΄ μ€νμ λ΄κΈ°
2. μ°μ°μλ₯Ό λ§λλ©΄ μ€νμμ λ κ°μ μ°μ°μλ₯Ό κΊΌλ΄μ μ°μ°ν λ€μ κ·Έ κ²°κ³Όλ₯Ό μ€νμ λ΄κΈ°
3. μ°μ°μ λ§μΉ λ€μ μ€νμ λ¨μμλ νλμ νΌμ°μ°μκ° μ°μ° μν κ²°κ³Ό

<span style="color:dodgerblue">**5) νμ νκΈ°λ² κ³μ°**</span>

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

<span style="color:dodgerblue">**6) λ§λ€μ΄μ§ κ³μ°κΈ° μ¬μ©νκΈ° 1**</span>

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
  printf("νμ νκΈ°λ²: %s\n", b); system("pause");
  return 0;
}
```

<br />

<span style="color:dodgerblue">**6) λ§λ€μ΄μ§ κ³μ°κΈ° μ¬μ©νκΈ° 2**</span>

```c
size = 1;
for (int i = 0; i < strlen(b) - 1; i++) { // λ§μ§λ§μ ν­μ κ³΅λ°±μ΄ λ€μ΄κ°λ―λ‘ 1μ λΉΌκΈ°
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

### β¨ tl;dr

- μ€νμ νμ©νμ¬ μ€μ νκΈ°λ²μ νμ νκΈ°λ²μΌλ‘ λ³νν  μ μλ€
- μ€νμ νμ©νμ¬ νμ νκΈ°λ²μ μ°μ°ν  μ μλ€
