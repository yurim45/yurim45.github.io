---
title: "🌈 자료구조의 개요"
tags:
  - [dataㅤstructureㅤ&ㅤalgorithm]
permalink: /dataStructure

navigation: true
toc: true
toc_sticky: true

date: 2021-10-17
last_modified_at: 2021-10-17
---

![]()

`개인 공부 과정을 기록합니다.`

### 🚀 What I Will Learn

- 자료구조의 필요성을 이해한다
- 자료구조의 성능 측정 방법에 대해 이해한다

---

# 자료구조의 개요

## 1️⃣ 자료구조의 필요성

- 자료구조는 데이터를 효과적으로 저장하고, 처리하는 방법에 대한 학문이다.
- 자료구조를 제대로 이해하지 못하면 불필요하게 메모리와 성능을 낭비할 여지가 있다.

> 예시) 프로그램 내에서 `INT`형 데이터가 1억개 가량 사용된다고 가정하자. 이때 <span style="color:hotpink">**원하는 데이터를 가장 빠르게 찾도록 해주는 자료구조**</span>는 무엇인가?

<br />

### ✔️ 기본적인 자료구조의 형태

1) 선형 구조
  - 배열
  - 연결 리스트
  - 스택
  - 큐
  
2) 비선형 구조
  - 트리(Tree)
  - 그래프(Graph)

<br />

### ✔️ 자료구조와 알고리즘 상관 관계?!

- 효율적인 자료구조 설계를 위해 알고리즘 지식이 필요
- 효율적인 알고리즘을 작성하기 위해서는 문제 상황에 맞는 적절한 자료구조 사용 필요

즉, 자료구조와 알고리즘은 떼려야 뗄 수 없는 관계이다!

<br />

### ✔️ 프로그램의 성능 측정 방법론

- <span style="color:hotpink">**시간 복잡도(Time Complexity)**</span>란?
  - 알고리즘에 사용되는 <span style="color:hotpink">**연산 횟수**</span>를 의미
- <span style="color:green">**공간 복잡도(Space Complexity)**</span>란?
  - 알고리즘에 사용되는 <span style="color:green">**메모리 양**</span>을 의미
  
즉, 효율적인 알고리즘을 사용한다고 가정했을 때, 일반적으로 시간과 공간은 반비례 관계이다

> 📌 참고! 
<span style="color:hotpink">**시간 복잡도**</span>를 표현할 때는 최악의 경우를 나타내는 Big-O 표기법을 사용한다.

![](https://images.velog.io/images/april_5/post/a182752b-b9d2-443e-809d-bb741a21886c/image.png)

- 프로그램 성능 측정 방법론 예시 이미지: 
  - 보통 연산 횟수가 10억을 넘어가면 1초 이상의 시간이 소요된다.

<br />

> 📌 참고! 
<span style="color:green">**공간 복잡도**</span>를 표기할 때는 일반적으로 MB 단위로 표기한다

- `int a[1000]`: 4KB
- `int a[1000000]`: 4MB
- `int a[2000][2000]`: 16MB

<br /><br />

---

### ✨ tl;dr

- 자료구조의 종류는 `스택`, `큐`, `트리` 등이 있다
- 프로그램을 작성할 때는 자료구조를 적절히 활용하여 성능 최적화를 노려야 한다

