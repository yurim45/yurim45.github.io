---
title: '☀️ 알고리즘:: 계수 정렬(Counting Sort)'
tags:
  - [dataStructure-algorithm]
permalink: /algorithm/countingSort

navigation: true
toc: true
toc_sticky: true

date: 2021-11-09
last_modified_at: 2021-11-09
---

![]()

### 🚀 What I Will Learn

- <span style="color:hotpink">**계수 정렬(Counting Sort)**</span>의 원리를 이해한다

> 카운팅 정렬(Counting Sort)은 작은 양의 정수인 키에 따라 개체 컬렉션을 정렬하는 알고리즘이다. 즉, **정수 정렬 알고리즘**

![](https://images.velog.io/images/april_5/post/6ebcd171-cd25-4173-a8d5-cf1455736e0a/image.png)

<br />

---

# 계수 정렬 알고리즘

## 1️⃣ 계수 정렬이란?

1. 크기를 기준으로 데이터의 개수를 세는 정렬 알고리즘
2. 각 데이터를 크기 기준으로 분류하므로 `0(N)`의 시간 복잡도를 가진다

<br />

### ✔️ 계수 정렬 알고리즘 예시

- 정렬해야 하는 데이터는 0~3까지 값.
- 0~3까지의 인덱스가 있는 배열 선언.

![](https://images.velog.io/images/april_5/post/06bcad66-25e6-4c18-857f-89c529383f75/image.png)

1. 데이터를 찾아 해당하는 값과 인덱스가 일치하면 원소값을 증가시킨다

![](https://images.velog.io/images/april_5/post/a66bc731-c6a8-40b9-adec-d8fbdea8def5/image.png)

2. 값을 모두 찾아 원소값을 증가시켰다면, 차례대로 원소의 개수만큼 출력한다

- 차례대로 원소의 개수만큼 출력: 0 0 1 1 1 2 2 2 3 3

![](https://images.velog.io/images/april_5/post/b0914801-c37b-49ff-92e5-026c20dcc64c/image.png)

<br /><br />

---

### ✨ tl;dr

- 계수 정렬은 시간 복잡도가 `𝑂(𝑁)`인 **정렬 알고리즘**이다
- 개수 정렬은 데이터의 크기가 한정적일 떄 사용할 수 있다
