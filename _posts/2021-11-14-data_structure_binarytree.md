---
title: "π μλ£κ΅¬μ‘°:: μ΄μ§ νΈλ¦¬(binary tree)"
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

### π What I Will Learn

- <span style="color:hotpink">**μ΄μ§ νΈλ¦¬(binary tree)**</span> μλ£κ΅¬μ‘°μ νμμ±μ λν΄ μ΄ννλ€
- μ΄μ§ νΈλ¦¬μ κ΄λ ¨ν λ€μν μ©μ΄λ₯Ό μ΄ν΄νλ€

> <span style="color:hotpink">**μ΄μ§ νΈλ¦¬(binary tree)**</span>λ? κ°κ°μ λΈλκ° μ΅λ λ κ°μ μμ λΈλλ₯Ό κ°μ§λ νΈλ¦¬ μλ£ κ΅¬μ‘°. μ΄μ§ νΈλ¦¬(Binary Tree)λ μ΅λ 2κ°μ μμμ κ°μ§ μ μλ νΈλ¦¬μ΄λ€.

![](https://images.velog.io/images/april_5/post/7c8a1989-05cf-47e6-a528-8ecebc869f67/image.png)

<br />

---

# μ΄μ§ νΈλ¦¬(binary tree)

## 1οΈβ£ μ΄μ§ νΈλ¦¬λ?

νΈλ¦¬(Tree)λ λλ¬΄μ ννλ₯Ό λ€μ§μ κ²κ³Ό κ°μ ννμ μλ£κ΅¬μ‘°

<br />

### βοΈ νΈλ¦¬μ μ©μ΄ μ΄ν΄

- `λ£¨νΈ λΈλ(root node)`: μ΅μλ¨ λΈλ
- `κ°μ§`: λ₯Ό μ΄μ©ν΄μ κ°κ°μ λΈλλ‘ μ°κ²°
- `λ¦¬ν λΈλ(reaf node)`: κ°μ₯ λ§μ§λ§ λΈλ

![](https://images.velog.io/images/april_5/post/31bf41af-089b-4a11-9c76-a6bc031245a8/image.png)

- `λΆλͺ¨ λΈλ`: μ΄λ€ λΈλμ λ°λ‘ μμ μ°κ²°λμ΄ μλ λΈλ
- `μμ λΈλ`: μ΄λ€ λΈλμ λ°λ‘ μλμ μ°κ²°λμ΄ μλ λΈλ

![](https://images.velog.io/images/april_5/post/3f296e95-9b55-4185-9e1f-c6c3e3cfb4d1/image.png)

- `νμ  λΈλ`: κ°μ λΆλͺ¨ λΈλμ μμλ€

![](https://images.velog.io/images/april_5/post/66277017-62bb-4bb4-af5c-9b72b82bd660/image.png)

- νΈλ¦¬μ `κΈΈμ΄(length)`: μΆλ° λΈλμμ λͺ©μ μ§ λΈλκΉμ§ κ±°μ³μΌ νλ κ°μ§μ μλ₯Ό μλ―Έ

![](https://images.velog.io/images/april_5/post/0e9885ad-c285-42fb-b6cb-3e92f67ad3b9/image.png)

- `κΉμ΄(Depth)`: λ£¨νΈ λΈλμμ νΉμ  λΈλκΉμ§μ κΈΈμ΄

![](https://images.velog.io/images/april_5/post/f9be910d-21a1-4d0e-94fc-1058d23d3d1b/image.png)

- νΈλ¦¬μ `λμ΄(Height)`: λ£¨νΈ λΈλμμ κ°μ₯ κΉμ λΈλκΉμ§μ κΈΈμ΄

![](https://images.velog.io/images/april_5/post/78ece759-5c0a-422a-af21-f2acb349d500/image.png)

<br />

### βοΈ νΈλ¦¬μ μ’λ₯

- `μ΄μ§ νΈλ¦¬(Binary Tree)`λ μ΅λ 2κ°μ μμμ κ°μ§ μ μλ νΈλ¦¬

![](https://images.velog.io/images/april_5/post/34f51501-d800-4cfc-b89b-6380117889d4/image.png)

- `ν¬ν μ΄μ§ νΈλ¦¬(Full Binary Tree)`: λ¦¬ν λΈλλ₯Ό μ μΈν λͺ¨λ  λΈλκ° λ μμμ κ°μ§κ³  μλ νΈλ¦¬

![](https://images.velog.io/images/april_5/post/c9d956e6-aa90-4661-a16a-9294f433f409/image.png)

- `μμ  μ΄μ§ νΈλ¦¬(Complete Binary Tree)`: λͺ¨λ  λΈλλ€μ΄ μΌμͺ½ μμλΆν° μ°¨κ·Όμ°¨κ·Ό μ±μμ§ λΈλ

![](https://images.velog.io/images/april_5/post/266c673a-0371-49a2-a23e-fcfb36afc55a/image.png)

- `λμ΄ κ· ν νΈλ¦¬(Height Balanced Tree)`λ μΌμͺ½ μμ νΈλ¦¬μ μ€λ₯Έμͺ½ μμ νΈλ¦¬μ λμ΄κ° 1 μ΄μ μ°¨μ΄ λμ§ μλ νΈλ¦¬

![](https://images.velog.io/images/april_5/post/475f7c9d-8cc2-473e-af93-c476245c67ed/image.png)

<br /><br />

---

### β¨ tl;dr

- μ΄μ§ νΈλ¦¬λ λ§μ μμ λΈλλ₯Ό λ?μ λμ΄μμ κ΄λ¦¬ν  μ μλ€λ μ μμ λ°μ΄ν° νμ©μ ν¨μ¨μ±μ΄ λμμ§λ€
- λ°μ΄ν° μ μ₯, νμ λ±μ λ€μν λͺ©μ μμ μ¬μ©ν  μ μλ€
