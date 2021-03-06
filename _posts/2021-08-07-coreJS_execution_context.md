---
title: "π―CoreJS:: μ€ν μ»¨νμ€νΈ"
tags:
  - [Javascript]
permalink: /study/JS/execution_context

navigation: true
toc: true
toc_sticky: true

date: 2021-08-07
last_modified_at: 2021-08-07
---

![]()

`μ£Όλμ΄ κ°λ°μμ κ°μΈ κ³΅λΆ κ³Όμ μ κΈ°λ‘ν©λλ€.`

---

# μ€ν μ»¨νμ€νΈ

μλ°μ€ν¬λ¦½νΈλ μ΄λ€ <span style="color:dodgerblue">**μ€ν μ»¨νμ€νΈκ° νμ±νλλ μμ **</span>μ

- μ μΈλ λ³μλ₯Ό μλ‘ λμ΄μ¬λ¦¬κ³ (νΈμ΄μ€ν hoisting)
- μΈλΆ νκ²½ μ λ³΄λ₯Ό κ΅¬μ±νκ³ 
- `this` κ°μ μ€μ νλ λ±μ λμμ μν

νλλ°, μ΄λ‘ μΈν΄ λ€λ₯Έ μΈμ΄μμλ λ°κ²¬ν  μ μλ νΉμ΄ν νμλ€μ΄ λ°μνλ€.

---

## μ€ν μ»¨νμ€νΈλ?

> **execution context**
> μ€νν  μ½λμ νκ²½ μ λ³΄λ€μ λͺ¨μλμ **κ°μ²΄**

- μλ°μ€ν¬λ¦½νΈμμ <span style="color:red">**κ°μ₯ μ€μν κ°λ**</span>
- ν¨μλ₯Ό μ€νν  λ μ€ν μ»¨νμ€νΈκ° κ΅¬μ±λ¨
- ν¨μκ° μ€νλ  λ `call stack`μ μμμ¬λ € μ½λμ νκ²½κ³Ό μμλ₯Ό λ³΄μ₯ν¨

### π‘Stackκ³Ό Queueβ

- Stack : FILO(First In Last Out), LIFO(Last In First Out)
- Queue : FIFO(First In First Out), LILO(Last In Last Out)
  ![](https://images.velog.io/images/april_5/post/7b6280e4-447f-4ad7-8f66-11acaa9d5998/image.png)

---

## μ€ν μ»¨νμ€νΈμ κ΅¬μ±

- μ μ­ κ³΅κ° β μλμΌλ‘ μμ±
- ~~eval() ν¨μ β μ¬μ©μ κΆμ₯νμ§ μμ~~
- **ν¨μλ₯Ό μ€ν** β κ°μ₯ νν μ€ν μ»¨νμ€νΈ κ΅¬μ± λ°©λ²
- ES6 λΆν°λ λΈλ‘`{ }`μ μν΄μλ μ€ν μ»¨νμ€νΈκ° μμ±

<br />

### :: μ€ν μ»¨νμ€νΈμ μ½ μ€ν μμ 

```js
// ------------------- (1)
var a = 1;
function outer() {
  function inner() {
    console.log(a); // undefined
    var a = 3;
  }
  inner(); // -------- (2)
  console.log(a); // 1
}
outer(); // ---------- (3)
console.log(a); // 1
```

μ μ½λλ₯Ό μ€ννλ μκ°
(1)μ μ­ μ»¨νμ€νΈκ° μ½ μ€νμ λ΄κΈ΄λ€.

- **μ μ­ μ»¨νμ€νΈ**λΌλ κ°λμ μΌλ°μ μΈ **μ€ν μ»¨νμ€νΈ**μ νΉλ³ν λ€λ₯Ό κ²μ΄ μλ€.
- λ³λμ μ€ν λͺλ Ήμ΄ μμ΄λ λΈλΌμ°μ μμ μλμΌλ‘ μ€νλλ€.

κ·Έ μ΄ν μ½λλ€μ μμ°¨λ‘ μ§ννλ€κ°
(3)μμ `outer`ν¨μλ₯Ό νΈμΆνλ©΄ μλ°μ€ν¬λ¦½νΈ μμ§μ

- `outer`μ λν νκ²½ μ λ³΄λ₯Ό μμ§
- `outer μ€ν μ»¨νμ€νΈ`λ₯Ό μμ±ν ν μ½ μ€νμ λ΄λλ€

μ΄ λ, μ½ μ€ν λ§¨ μμ outerμ€ν μ»¨νμ€νΈκ° λμΈ μνμ΄λ―λ‘ μ μ­ μ»¨νμ€νΈμ κ΄λ ¨λ μ½λμ μ€νμ μΌμ μ€λ¨νκ³  outer μ€ν μ»¨νμ€νΈμ κ΄λ ¨λ μ½λ(μ¦, outerν¨μ λ΄λΆ μ½λ)λ€μ μμ°¨λ‘ μ€ννλ€.

λ€μ (2)μμ `inner`ν¨μμ μ€ν μ»¨νμ€νΈκ° μ½ μ€ν κ°μ₯ μμμ λ΄κΈ°λ©΄ outer μ»¨νμ€νΈμ κ΄λ ¨λ μ½λμ μ€νμ μ€λ¨νκ³  inner ν¨μ λ΄λΆμ μ½λλ€μ μμλλ‘ μ§ννλ€.

![](https://images.velog.io/images/april_5/post/cf167098-2f0d-4883-ab98-b903e7d7d0f9/image.png)

μ΄λ κ² μ΄λ€ μ€ν μ»¨νμ€νΈκ° νμ±νλ  λ μλ°μ€ν¬λ¦½νΈ μμ§μ ν΄λΉ μ»¨νμ€νΈμ **κ΄λ ¨λ μ½λλ€μ μ€ννλ λ° νμν νκ²½ μ λ³΄λ€μ μμ§**ν΄μ <span style="color:dodgerblue">**μ€ν μ»¨νμ€νΈ κ°μ²΄**</span>μ μ μ₯νλ€.
μ΄ κ°μ²΄λ μλ°μ€ν¬λ¦½νΈ μμ§μ΄ νμ©ν  λͺ©μ μ μμ±λ  λΏ, κ°λ°μκ° μ½λλ₯Ό ν΅ν΄ νμΈμ ν  μ μλ€.

---

## νμ±ν λ μ€ν μ»¨νμ€νΈ κ°μ²΄μ μμ§ μ λ³΄

### 1. VariableEnvironment

> μ΅μ΄ μ€ν μμ μ€λμ·μ μ μ§. VariableEnvironmentμ μ λ³΄λ₯Ό λ³΅μ¬ν΄μ LexicalEnvironmentλ₯Ό μμ±, κ·Έ μ΄νμ LexicalEnvironmentλ₯Ό μ£Όλ‘ νμ©νκ² λλ€.

- νμ¬ μ»¨νμ€νΈ λ΄μ **μλ³μλ€μ λν μ λ³΄** + **μΈλΆ νκ²½ μ λ³΄**
- μ μΈ μμ μ LexicalEnvironmentμ snapshotμΌλ‘, <span style="color:dodgerblue">**λ³κ²½ μ¬ν­μ λ°μλμ§ μλλ€**</span>.

> VariableEnvironmentμ LexicalEnvironmentμ λ΄λΆλ **environmentRecord**μ **outerEnvironmentReference**λ‘ κ΅¬μ±λΌ μλ€.

### 2. LexicalEnvironment

: μ²μμλ VariableEnvironmentμ κ°μ§λ§ <span style="color:dodgerblue">**λ³κ²½ μ¬ν­μ΄ μ€μκ°μΌλ‘ λ°μ**</span>λλ€.

#### π© environmentRecordμ <span style="color:dodgerblue">**νΈμ΄μ€ν**</span> β¨

- environmentRecordμλ νν μ»¨νμ€νΈμ κ΄λ ¨λ μ½λμ λ§€κ°λ³μ μ΄λ¦, ν¨μ μ μΈ, λ³μλͺ λ± **μλ³μ μ λ³΄λ€μ΄ μ μ₯**(μ μΈλ λ³μμ μλ³μ λ±)
  > μ»¨νμ€νΈ λ΄λΆ μ μ²΄λ₯Ό μ²μλΆν° λκΉμ§ **μμλλ‘** μμ§νλ€.
  > λ³μ μ λ³΄λ₯Ό μμ§νλ κ³Όμ μ λͺ¨λ λ§μ³€λλΌλ μμ§ μ€ν μ»¨νμ€νΈκ° κ΄μ¬ν  μ½λλ€μ μ€ν μ  μνμΈλ°,
  > μ½λκ° μ€νλμ§ μ μμλ λΆκ΅¬νκ³  μλ°μ€ν¬λ¦½νΈ μμ§μ μ΄λ―Έ ν΄λΉ νκ²½μ μν μ½λμ λ³μλͺλ€μ λͺ¨λ μκ³  μκ² λλ€. μ¬κΈ°μ **νΈμ΄μ€ν**μ΄λΌλ κ°λμ΄ λ±μ₯νλ€.

#### π© μ€μ½ν, μ€μ½ν μ²΄μΈ, outerEnvironmentReference

- μ€μ½νscope?

  > μλ³μμ λν μ ν¨λ²μ

  - ES5κΉμ§λ μ μ­ κ³΅κ°μ μ μΈνλ©΄ **μ€μ§ ν¨μμ μν΄μλ§** μ€μ½νκ° μμ±
  - <span style="color:dodgerblue">**ES6μμλ λΈλ‘μ μν΄μλ μ€μ½ν κ²½κ³κ° λ°μνκ² ν¨**</span>μΌλ‘μ¨ λ€λ₯Έ μΈμ΄μ λΉμ·ν΄μ‘λ€.
  - λ€λ§, `var` λ³μμ λν΄μλ μμ©νμ§ μκ³  μλ‘ μκΈ΄ `let`, `const`, `class`, `strict modeμμμ ν¨μ μ μΈ` λ±μ λν΄μλ§ μμ©νλ€.
    - ES6μμλ λμ κ΅¬λΆνκΈ° μν΄ ν¨μ μ€μ½ν, λΈλ‘ μ€μ½νλΌλ μ©μ΄λ₯Ό μ¬μ©νλ€.

- μ€μ½ν μ²΄μΈ?
  > μ¬λ¬ μ€μ½νμμ λμΌν μλ³μλ₯Ό μ μΈν κ²½μ°μλ **λ¬΄μ‘°κ±΄ μ€μ½ν μ²΄μΈ μμμ κ°μ₯ λ¨Όμ  λ°κ²¬λ μλ³μμλ§ μ κ·Ό κ°λ₯**νκ² νλ κ²

### 3. ThisBinding

- `this` μλ³μκ° λ°λΌλ΄μΌ ν  λμ κ°μ²΄

---

## μ μ­λ³μμ μ§μ­λ³μ

- μ μ­λ³μ : μ μ­ κ³΅κ°μμ μ μΈν λ³μ. μ μ­ μ»¨νμ€νΈμ `LexicalEnvironment`μ λ΄κΈ΄ λ³μ
- μ§μ­λ³μ : ν¨μ λ΄λΆμμ μ μΈν λ³μ

> μμ ν μ½λ κ΅¬μ±μ μν΄ κ°κΈμ  μ μ­λ²μμ μ¬μ©μ μ΅μννλ κ²μ΄ μ’λ€

---

## this

- μ€ν μ»¨νμ€νΈμ thisBindingμλ thisλ‘ μ§μ  λ κ°μ²΄κ° μ μ₯λ¨
- μ€ν μ»¨νμ€νΈ νμ±ν λΉμμ thisκ° μ§μ λμ§ μμ κ²½μ°, thisμλ μ μ­ κ°μ²΄κ° μ μ₯ λ¨
- κ·Έ λ°μλ ν¨μλ₯Ό νΈμΆνλ λ°©λ²μ λ°λΌ thisμ μ μ₯λλ λμμ΄ λ€λ¦

---

![](https://images.velog.io/images/april_5/post/1f2612fe-98c3-48e0-9e51-606c2dfa834a/%E1%84%89%E1%85%B5%E1%86%AF%E1%84%92%E1%85%A2%E1%86%BC%20%E1%84%8F%E1%85%A5%E1%86%AB%E1%84%90%E1%85%A6%E1%86%A8%E1%84%89%E1%85%B3%E1%84%90%E1%85%B3.jpeg)
