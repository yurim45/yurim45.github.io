---
title: '☀️ 알고리즘:: 정렬 알고리즘_ 선택 정렬과 삽입 정렬'
tags:
  - [data-structure💥algorithm]
permalink: /algorithm/sort

navigation: true
toc: true
toc_sticky: true

date: 2021-11-07
last_modified_at: 2021-11-07
---

![]()
### 🚀 What I Will Learn

- <span style="color:hotpink">**선택 정렬**</span> 의 원리를 이해한다
- <span style="color:hotpink">**삽입 정렬**</span> 의 원리를 이해한다

>컴퓨터 과학과 수학에서 **정렬 알고리즘**이란 원소들을 번호순이나 사전 순서와 같이 일정한 순서대로 열거하는 알고리즘이다. 


<br />

---

# 정렬 알고리즘

## 1️⃣ 선택 정렬이란?

1) 가장 기본적인 정렬 알고리즘
2) 가장 작은 것을 선택해서 앞으로 보내는 정렬 기법
3) 가장 작은 것을 선택하는 데에 N번, 앞으로 보내는 데에 N번의 연산으로 `O(n²)`의 시간복잡도를 가진다

  - 정렬 전

![](https://images.velog.io/images/april_5/post/d083fe83-9fc1-4bc2-b82f-82f19c30957f/image.png)

  - 정렬 후
  
![](https://images.velog.io/images/april_5/post/9a678518-18b4-4d1f-a92b-68c062d45b8a/image.png)


<br />

---

## 2️⃣ 선택 정렬의 구현

<span style="color:dodgerblue">**1) 배열 선언**</span>

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <limits.h>
#define SIZE 1000

int a[SIZE];
int swap(int *a, int *b) { 
  int temp = *a;
  *a = *b;
  *b = temp;
}
```

<br />

<span style="color:dodgerblue">**2) 선택정렬수행**</span>

```c
int main(void) {
  int n, min, index;
  scanf("%d", &n);
  for (int i = 0; i < n; i++) scanf("%d", &a[i]); 
  for (int i = 0; i < n; i++) {
    min = INT_MAX;
    for (int j = i; j < n; j++) {
      if (min > a[j]) {
        min = a[j];
        index = j;
      } 
    }
    swap(&a[i], &a[index]); 
  }
  system("pause");
  return 0; 
}
```

<br /><br />

---

## 3️⃣ 삽입 정렬이란?

1) 각 숫자를 적절한 위치에 삽입하는 정렬 기법
2) 들어갈 위치를 선택하는 데에 N번, 선택하는 횟수로 N번이므로 `O(n²)`의 시간복잡도를 가진다
3) 일반적으로 선택 정렬보다 빠르게 동작한다

  - 정렬 전

![](https://images.velog.io/images/april_5/post/8aba5c72-80c7-4824-8526-04877147efe8/image.png)

  - 정렬 중
    - 두 번째 원소인 4부터 출발해서 4가 들어갈 공간을 확인한다
    - 그 다음인 3은 2와 4의 위치를 확인했을 때에 2와 4의 사이에 들어간다
  
![](https://images.velog.io/images/april_5/post/3cb4aef9-62a5-4da1-b803-a5011151fe6c/image.png)

  - 정렬 후
  
![](https://images.velog.io/images/april_5/post/086b1379-15c2-4b97-a53e-df2735f9859a/image.png)

<br />

---

## 4️⃣ 삽입 정렬의 구현

<span style="color:dodgerblue">**1) 배열 선언**</span>

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#define SIZE 1000

int a[SIZE];
int swap(int *a, int *b) {
  int temp = *a;
  *a = *b;
  *b = temp;
}
```

<br />

<span style="color:dodgerblue">**2) 삽입정렬수행**</span>

```c
int main(void) {
  int n;
  scanf("%d", &n);
  for (int i = 0; i < n; i++) scanf("%d", &a[i]); 
  for (int i = 0; i < n - 1; i++) {
      int j = i;
      while (j >= 0 && a[j] > a[j + 1]) {
        swap(&a[j], &a[j + 1]);
  	j--; 
      }
  } 
  system("pause"); 
  return 0;
}
```

<br /><br />

---

### ✨ tl;dr

- 선택 정렬과 삽입 정렬은 시간복잡도가 `O(n²)`인 가장 간단한 형태의 정렬 알고리즘이다


