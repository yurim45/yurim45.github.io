---
title: '☀️ 알고리즘:: 퀵 정렬(Quicksort)'
tags:
  - [dataStructure-algorithm]
permalink: /algorithm/quicksort

navigation: true
toc: true
toc_sticky: true

date: 2021-11-13
last_modified_at: 2021-11-13
---

![]()

### 🚀 What I Will Learn

- <span style="color:hotpink">**퀵 정렬(Quicksort)**</span>의 원리를 이해한다

>**퀵 정렬(Quicksort)**은 *찰스 앤터니 리처드 호어*가 개발한 정렬 알고리즘이다. **다른 원소와의 비교만으로 정렬을 수행**하는 <span style="color:hotpink">**비교 정렬**</span>에 속한다

<br />

---

# 퀵 정렬 알고리즘

## 1️⃣ 퀵 정렬이란?

1) 피벗(pivot)을 기준으로 큰 값과 작은 값을 서로 교체하는 정렬 기법
2) 값을 서로 교체하는 데에 N번, 엇갈린 경우 교체 이후에 원소가 반으로 나누어지므로
3) 전체 원소를 나누는 데에 평균적으로 `logN`번이 소요된다
4) 평균적으로 `0(NlogN)`의 시간 복잡도를 가진다

>**시간복잡도**: <u>문제를 해결하는데 걸리는 시간과 입력의 함수 관계</u>. <br /> 컴퓨터과학에서 알고리즘의 시간복잡도는 입력을 나타내는 문자열 길이의 함수로서 작동하는 알고리즘을 취해 시간을 정량화하는 것을 의미

<br />

### ✔️ 퀵 정렬 알고리즘 예시 

퀵 정렬을 수행할 때 피벗값이 가장 왼쪽 값이라고 가정.

1) 가장 왼쪽 값인 5를 기준으로 오른쪽으로 출발해서 5보다 <span style="color:blue">**큰 값**</span>을 찾는다. 그럼 8

![](https://images.velog.io/images/april_5/post/bd2b9098-f88d-495e-a3ea-54bc1bb1349a/image.png)

2) 배열의 오른쪽부터 시작해서 5보다 <span style="color:blue">**작은 값**</span>을 구하면 2

![](https://images.velog.io/images/april_5/post/5c5cf4d7-6fd0-408b-8862-b0c0fa33579e/image.png)

3) 비교를 통해 찾았던 8과 2의 자리를 <span style="color:blue">**서로 교체**</span>

![](https://images.velog.io/images/april_5/post/9e8464a2-890e-4a9b-acce-47c49f7e58c4/image.png)

4) 마찬가지로 원소를 찾는다. 
  - 왼쪽에서 부터 5보다 큰 값은 9, 
  - 오른쪽에서 부터 5보다 작은 값은 1

![](https://images.velog.io/images/april_5/post/59c7c1df-c368-456a-8994-7d0167c9c303/image.png)

5) 같은 방법으로 원소를 찾는다.
  - 왼쪽에서 부터 5보다 큰 값은 6,
  - 오른쪽에서 부터 5보다 작은 값은 1
  
![](https://images.velog.io/images/april_5/post/f75547ad-c443-465b-a8f1-5b387a498db9/image.png)

6) 원소를 찾다보면 5)번과 같이 엇갈리는 경우가 발생하는데, 이렇게 큰 값과 작은 값이 엇갈리는 경우에는 피벗값과 더 작은 값을 서로 교체

![](https://images.velog.io/images/april_5/post/8c4a6195-ec48-4e62-9a0d-58446af8221a/image.png)

7) 다시 피벗값을 기준으로 재귀적으로 반복하며 퀵 정렬을 수행

![](https://images.velog.io/images/april_5/post/1865427a-3f05-429f-95bd-d552230f3b37/image.png)

8) 각각의 부분 배열들이 정렬을 수행하면서 정렬 수행

![](https://images.velog.io/images/april_5/post/db5f128f-c72d-4e61-96e5-2c53a4f34c81/image.png)

<br />

### 📌 참고

퀵 정렬은 원소를 절반씩 나눌 때 logN의 시간 복잡도가 나오는 대표적인 **완전 이진 트리**와 흡사한 구조를 갖는다.

>이진트리: 원소를 절반씩 나눌 때 𝑙𝑜𝑔𝑁의 시간 복잡도가 나오는 대표적인 예시는 **완전 이진 트리**. 완전 이진 트리 형태는 흔히 컴퓨터 공학에서 가장 선호하는 이상적인 형태이다.
![](https://images.velog.io/images/april_5/post/cbd19fad-a0b4-4d70-8aa0-5e4276542299/image.png)

<br />
<br />

---

## 2️⃣ 퀵 정렬의 구현

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

<span style="color:dodgerblue">**2) 퀵 정렬 구현**</span>

```c
void quickSort(int start, int end) {
  if (start >= end) return;
  int key = start, i = start + 1, j = end, temp; 
    while (i <= j) {  // 엇갈릴 때까지 반복합니다.
      while (i <= end && a[i] <= a[key]) i++; 
      while (j > start && a[j] >= a[key]) j--; 
      if (i > j) swap(&a[key], &a[j]);
      else swap(&a[i], &a[j]);
    }
  quickSort(start, j - 1); 
  quickSort(j + 1, end);
}
```

<br />

<span style="color:dodgerblue">**3) 퀵 정렬 사용**</span>

```c
int main(void) {
  int n;
  scanf("%d", &n);
  for (int i = 0; i < n; i++) scanf("%d", &a[i]);
  quickSort(0, n - 1);
  for (int i = 0; i < n; i++) printf("%d ", a[i]);
  system("pause");
  return 0;
}
```

<br /><br />

---

### ✨ tl;dr

- 퀵 정렬은 시간 복잡도가 `𝑂(𝑁𝑙𝑜𝑔𝑁)`인 **가장 보편적인 정렬 알고리즘**이다




