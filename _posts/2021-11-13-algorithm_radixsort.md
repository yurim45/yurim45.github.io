---
title: "☀️ 알고리즘:: 기수 정렬(Radix Sort)"
tags:
  - [dataStructure-algorithm]
permalink: /algorithm/radixsort

navigation: true
toc: true
toc_sticky: true

date: 2021-11-13
last_modified_at: 2021-11-13
---

![]()

### 🚀 What I Will Learn

- <span style="color:hotpink">**기수 정렬((Radix Sort)**</span>의 원리를 이해한다

> **기수정렬**은 낮은 자리수부터 비교하여 정렬해 간다는 것을 기본 개념으로 하는 정렬 알고리즘. 기수정렬은 비교 연산을 하지 않으며 정렬 속도가 빠르지만, 데이터 전체 크기에 기수 테이블의 크기만한 메모리가 더 필요하다.

<br />

---

# 기수 정렬 알고리즘

## 1️⃣ 기수 정렬이란?

1. 자릿수를 기준으로 차례대로 데이터를 정렬하는 정렬 알고리즘
2. 각 데이터를 자릿수를 기준으로 분류하므로, 가장 큰 자릿수를 D라고 했을 때 `0(DN)`의 시간 복잡도를 가진다
3. 자릿수의 개수만큼 반복

<br />

### ✔️ 기수 정렬 알고리즘 예시

- 각 자릿수를 확인해서 배열에 값을 증가시킨다.

1. 자릿수: 1의 자리

![](https://images.velog.io/images/april_5/post/18a44a31-31b0-4059-ae10-2940583f8c4d/image.png)

2. 계수 정렬과 비슷하지만, 차이점은 누적값을 가진다. 누적값을 구하는 이유는 결과배열을 만들기 위해서이다.

- 총 7개의 원소에 대해서 누적해서 갯수를 구한다

![](https://images.velog.io/images/april_5/post/6a630583-99bd-40c7-9924-92535ffffdb5/image.png)

3. 결과배열은 원소의 뒤에서 부터 확인한다.

- 가장 뒤에 있는 34부터 시작.
- 34의 1의 자리가 4이므로,
- 기존에 4가 있는 누적값을 찾아
- 결과배열의 4번째에 해당하는 자리에 34를 추가한다

![](https://images.velog.io/images/april_5/post/3b00691c-6e0c-43bc-b8d8-14dbc00c4bf0/image.png)

4. 34를 처리했으니 -1을 처리해서 3이 되었다

![](https://images.velog.io/images/april_5/post/82485233-c384-4827-b1f5-4262753be29b/image.png)

5. 그 다음 원소도 동일한 방법으로 처리한다

![](https://images.velog.io/images/april_5/post/94a85691-eba9-4840-b23f-2fa857c2aed9/image.png)

6. 1의 자리까지 정렬 완료!

![](https://images.velog.io/images/april_5/post/22a4ac9c-f1d7-4548-857b-ddcdcd602480/image.png)

7. 자릿수: 10의 자리

- 동일한 방법으로 누적값을 구하고,
- 결과배열을 구한다

![](https://images.velog.io/images/april_5/post/9e2a079b-340c-4863-8cf5-4d2a581072f2/image.png)

- 10의 자리까지 정렬 완료!

![](https://images.velog.io/images/april_5/post/bac7abb5-dfaf-42df-872d-a606fac870bc/image.png)

8. 자릿수: 100의 자리

- 동일한 방법으로 정렬한다

![](https://images.velog.io/images/april_5/post/b5b0be91-ff88-4bbe-b55c-7cc83cb759c3/image.png)

- 100의 자리까지 정렬 완료!

![](https://images.velog.io/images/april_5/post/b623627a-bfe7-44ae-ad27-172219283f20/image.png)

9. 정렬 완료

![](https://images.velog.io/images/april_5/post/4697a644-f9bc-411d-824f-ca0717b8f8f9/image.png)

<br /><br />

---

### ✨ tl;dr

- 기수 정렬은 시간 복잡도가 `𝑂(ㅇ𝑁)`인 **정렬 알고리즘**이다
- 개수 정렬보다 약간 더 느리지만 숫자가 매우 큰 상황에서도 사용할 수 있다
