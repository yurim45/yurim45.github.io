---
title: "🌈 자료구조:: 이진 트리(binary tree)"
tags:
  - [dataStructure-algorithm]
permalink: /data_structure/binarytree

navigation: true
toc: true
toc_sticky: true

date: 2021-11-14
last_modified_at: 2021-11-14
---

![]()

### 🚀 What I Will Learn

- <span style="color:hotpink">**이진 트리(binary tree)**</span> 자료구조의 필요성에 대해 이하한다
- 이진 트리와 관련한 다양한 용어를 이해한다

> <span style="color:hotpink">**이진 트리(binary tree)**</span>란? 각각의 노드가 최대 두 개의 자식 노드를 가지는 트리 자료 구조. 이진 트리(Binary Tree)는 최대 2개의 자식을 가질 수 있는 트리이다.

![](https://images.velog.io/images/april_5/post/7c8a1989-05cf-47e6-a528-8ecebc869f67/image.png)

<br />

---

# 이진 트리(binary tree)

## 1️⃣ 이진 트리란?

트리(Tree)는 나무의 형태를 뒤집은 것과 같은 형태의 자료구조

<br />

### ✔️ 트리의 용어 이해

- `루트 노드(root node)`: 최상단 노드
- `가지`: 를 이용해서 각각의 노드로 연결
- `리프 노드(reaf node)`: 가장 마지막 노드

![](https://images.velog.io/images/april_5/post/31bf41af-089b-4a11-9c76-a6bc031245a8/image.png)

- `부모 노드`: 어떤 노드의 바로 위에 연결되어 있는 노드
- `자식 노드`: 어떤 노드의 바로 아래에 연결되어 있는 노드

![](https://images.velog.io/images/april_5/post/3f296e95-9b55-4185-9e1f-c6c3e3cfb4d1/image.png)

- `형제 노드`: 같은 부모 노드의 자식들

![](https://images.velog.io/images/april_5/post/66277017-62bb-4bb4-af5c-9b72b82bd660/image.png)

- 트리의 `길이(length)`: 출발 노드에서 목적지 노드까지 거쳐야 하는 가지의 수를 의미

![](https://images.velog.io/images/april_5/post/0e9885ad-c285-42fb-b6cb-3e92f67ad3b9/image.png)

- `깊이(Depth)`: 루트 노드에서 특정 노드까지의 길이

![](https://images.velog.io/images/april_5/post/f9be910d-21a1-4d0e-94fc-1058d23d3d1b/image.png)

- 트리의 `높이(Height)`: 루트 노드에서 가장 깊은 노드까지의 길이

![](https://images.velog.io/images/april_5/post/78ece759-5c0a-422a-af21-f2acb349d500/image.png)

<br />

### ✔️ 트리의 종류

- `이진 트리(Binary Tree)`는 최대 2개의 자식을 가질 수 있는 트리

![](https://images.velog.io/images/april_5/post/34f51501-d800-4cfc-b89b-6380117889d4/image.png)

- `포화 이진 트리(Full Binary Tree)`: 리프 노드를 제외한 모든 노드가 두 자식을 가지고 있는 트리

![](https://images.velog.io/images/april_5/post/c9d956e6-aa90-4661-a16a-9294f433f409/image.png)

- `완전 이진 트리(Complete Binary Tree)`: 모든 노드들이 왼쪽 자식부터 차근차근 채워진 노드

![](https://images.velog.io/images/april_5/post/266c673a-0371-49a2-a23e-fcfb36afc55a/image.png)

- `높이 균형 트리(Height Balanced Tree)`는 왼쪽 자식 트리와 오른쪽 자식 트리의 높이가 1 이상 차이 나지 않는 트리

![](https://images.velog.io/images/april_5/post/475f7c9d-8cc2-473e-af93-c476245c67ed/image.png)

<br /><br />

---

### ✨ tl;dr

- 이진 트리는 많은 양의 노드를 낮은 높이에서 관리할 수 있다는 점에서 데이터 활용의 효율성이 높아진다
- 데이터 저장, 탐색 등의 다양한 목적에서 사용할 수 있다
