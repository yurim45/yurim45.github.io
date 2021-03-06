---
title: "π―CoreJS:: νλ‘ν νμ"
tags:
  - [Javascript]
permalink: /study/JS/prototype

navigation: true
toc: true
toc_sticky: true

date: 2021-08-21
last_modified_at: 2021-08-21
---

![](https://images.velog.io/images/april_5/post/8dc70d82-08d1-4fd8-bbe5-27fe0d8e7f90/%E1%84%91%E1%85%B3%E1%84%85%E1%85%A9%E1%84%90%E1%85%A9%E1%84%90%E1%85%A1%E1%84%8B%E1%85%B5%E1%86%B8.png)

`μ£Όλμ΄ κ°λ°μμ κ°μΈ κ³΅λΆ κ³Όμ μ κΈ°λ‘ν©λλ€.`

μλ°μ€ν¬λ¦½νΈλ νλ‘ν νμ κΈ°λ° μΈμ΄μ΄λ€.

- ν΄λμ€ κΈ°λ° μΈμ΄μμλ `μμ`μ μ¬μ©νμ§λ§
- νλ‘ν νμ κΈ°λ° μΈμ΄μμλ <U>μ΄λ€ κ°μ²΄λ₯Ό μν(prototype)μΌλ‘ μΌκ³  μ΄λ₯Ό λ³΅μ (μ°Έμ‘°)ν¨</U>μΌλ‘μ¨ μμκ³Ό λΉμ·ν ν¨κ³Όλ₯Ό μ»λλ€.

μ΄λ° λνΉν κ°λμΈ νλ‘ν νμμ λν΄ μμλ³΄μ.

<br />

---

# νλ‘ν νμμ κ°λ μ΄ν΄

## `Constructor`, `prototype`, `instance`

![](https://images.velog.io/images/april_5/post/beb16828-941f-4489-92a4-b18cdebb2034/image.png)

μ΄ κ·Έλ¦Όμ μ’ λ κ΅¬μ²΄μ μΈ ννλ‘ λ°κΎΈλ©΄,

![](https://images.velog.io/images/april_5/post/59f2f065-efba-4c93-8c04-89adbe9b13a3/image.png)

μ΄λ° κ·Έλ¦Όμ΄ λλ€. μμ μλμ κ·Έλ¦Όμ λ³΄λ©΄μ νλ¦μ λ°λΌκ° λ³΄μ.

- μ΄λ€ μμ±μ ν¨μ`Constructor`λ₯Ό `new` μ°μ°μμ ν¨κ» νΈμΆνλ©΄
- `Constructor`μμ μ μλ λ΄μ©μ λ°νμΌλ‘ μλ‘μ΄ μΈμ€ν΄μ€`instance`κ° μμ±λλ€
- μ΄λ `instance`μλ `__proto__`λΌλ νλ‘νΌν°κ° μλμΌλ‘ λΆμ¬λλλ°,
- μ΄ νλ‘νΌν°λ `Constructor`μ `prototype`λΌλ νλ‘νΌν°λ₯Ό μ°Έμ‘°νλ€.

> λͺ¨λ  κ°μ²΄λ€μ΄ λ©μλμ μμ±λ€μ μμ λ°κΈ° μν ννλ¦ΏμΌλ‘μ¨ νλ‘ν νμ κ°μ²΄(prototype object)λ₯Ό κ°μ§λ€λ μλ―Έ

<br />

<span style="color:dodgerblue">**`prototype`μ `__proto__`λΌλ νλ‘νΌν°μ κ΄κ³κ° νλ‘ν νμμ ν΅μ¬**</span>μ΄λ€.

- `prototype`μ κ°μ²΄μ΄λ€. μ΄λ₯Ό μ°Έμ‘°νλ `__proto__`(dunder proto: λλ νλ‘ν ) μ­μ κ°μ²΄μ΄λ€.
- `prototype` κ°μ²΄ λ΄λΆμλ μΈμ€ν΄μ€κ° μ¬μ©ν  λ©μλλ₯Ό μ μ₯νλ€.
- κ·Έλ¬λ©΄ μΈμ€ν΄μ€μμλ μ¨κ²¨μ§ νλ‘νΌν°μΈ `__proto__` κ°μ²΄λ₯Ό ν΅ν΄ μ΄ λ©μλλ€μ μ κ·Όν  μ μκ² λλ€.

<br />

| μ°Έκ³ λ‘,                                                                                                                                                                                                                                                                                                        |
| :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ES5.1 λͺμΈμλ **proto**κ° μλλΌ [[prototype]]μ΄λΌλ λͺμΉ­μΌλ‘ μ μλμ΄ μλ€. λͺμΈμλ instance.**proto**μ κ°μ λ°©μμΌλ‘ μ κ·Όνλ κ²μ νμ©νμ§ μκ³ , μ€μ§ <span style="color:dodgerblue">**Object.getPrototypeOf(instance)/Reflelect.getPrototypeOf(instance)**</span>λ₯Ό ν΅ν΄μλ§ μ κ·Όν  μ μλλ‘ μ μνλ€. |
| μ€λ¬΄μμλ κ°κΈμ  `__proto__`λ₯Ό μ¬μ©νμ§ μκΈ°λ₯Ό κΆμ₯. λμ  <span style="color:dodgerblue">**Object.getPrototypeOf()/Object.create()**</span> λ±μ μ΄μ©νλλ‘ νμ.                                                                                                                                             |

<br /><br />

---

![](https://images.velog.io/images/april_5/post/f3952c8a-38aa-4d07-af1c-bb3509d4a2a0/image.png)

μμ λ₯Ό ν΅ν΄ μ΄ν΄ν΄λ³΄μ.

```jsx
const Person = (name) => {
  this._name = name;
};

Person.prototype.getName = () => {
  return this._name;
};
```

`Person`μ μΈμ€ν΄μ€λ `__proto__` νλ‘νΌν°λ₯Ό ν΅ν΄ `getName`μ νΈμΆν  μ μλ€.

```jsx
const april = new Person("april");

april.__proto__.getName(); // (1) undefined
```

`instance`μ `__proto__`κ° `Constructor`μ `prototype` νλ‘νΌν°λ₯Ό μ°Έμ‘°νλ―λ‘ κ²°κ΅­ λμ κ°μ κ°μ²΄λ₯Ό λ°λΌλ³΄κΈ° λλ¬Έμ΄λ€.

(1) λ€λ§, μ¬κΈ°μ `undefined`κ° λ°νλ μ΄μ λ `this`μ λ°μΈλ© λ λμμ΄ μλͺ»λκΈ° λλ¬ΈμΈλ°, μ΄λ€ ν¨μλ₯Ό **λ©μλλ‘μ** νΈμΆν  λλ λ©μλλͺ λ°λ‘ μμ κ°μ²΄κ° κ³§ `this`κ° λλ€. [π― Javascript this](https://yurim45.github.io/study/JS/this)

`__proto__` κ°μ²΄μ `name` νλ‘νΌν°κ° μλ€λ©΄?

```jsx
const april = new Person("april");

april.__proto__._name = "april__proto__";
april.__proto__.getName(); // (1) april__proto__
```

κ΄κ±΄μ `this`μΈλ°, `this`λ₯Ό μΈμ€ν΄μ€λ‘ νλ λ°©λ²μ `__proto__` μμ΄ μΈμ€ν΄μ€μμ κ³§λ°λ‘ λ©μλλ₯Ό μ°λ κ²μ΄λ€.

```jsx
const april = new Person("april");

april.getName(); // (1) april
```

μ΄ ννμ΄ κ°λ₯ν μ΄μ λ <span style="color:dodgerblue">**`__proto__`κ° μλ΅ κ°λ₯ν νλ‘νΌν°**</span>μ΄κΈ° λλ¬Έμ΄λ€.

> μ λ¦¬νμλ©΄,
> `new` μ°μ°μλ‘ `Constructor`λ₯Ό νΈμΆνλ©΄ `instance`κ° λ§λ€μ΄μ§λλ°,
> μ΄ `instance`μ μλ΅ κ°λ₯ν νλ‘νΌν°μΈ `__proto__`λ `Constructor`μ `prototype`μ μ°Έμ‘°νλ€.

<br />

μ΄λ²μ μ°λ¦¬κ° μμ£Ό μ¬μ©νλ λ°°μ΄μ ν΅ν΄ μ΄ν΄ν΄λ³΄μ.

![](https://images.velog.io/images/april_5/post/d709d6ea-942e-4712-b7aa-1e3a5ab82620/image.png)

λ°°μ΄μ μ¬λ¬ λ©μλλ€μ μ¬μ©ν  μ μμλ μ΄μ μ λν΄ μ΄ν΄ν  μ μμ κ²μ΄λ€.

<br /><br />

---

## νλ‘ν νμ μ²΄μΈ

μ΄λ€ λ°μ΄ν°μ `__proto__` νλ‘νΌν° λ΄λΆμ λ€μ `__proto__` νλ‘νΌν°κ° μ°μμ μΌλ‘ μ΄μ΄μ§ κ²μ <span style="color:dodgerblue">**νλ‘ν νμ μ²΄μΈ(prototype chain)**</span>μ΄λΌ νκ³ ,
μ΄ μ²΄μΈμ λ°λΌκ°λ©° κ²μνλ κ²μ <span style="color:blue">**νλ‘ν νμ μ²΄μ΄λ(prototype chaining)**</span>μ΄λΌκ³  νλ€.

**νλ‘ν νμ μ²΄μ΄λ(prototype chaining)**μ
μ΄λ€ λ©μλλ₯Ό νΈμΆνλ©΄ μλ°μ€ν¬λ¦½νΈ μμ§μ

- λ°μ΄ν° μμ μ νλ‘νΌν°λ€μ κ²μν΄μ μνλ λ©μλκ° μμΌλ©΄ κ·Έ λ©μλλ₯Ό μ€ννκ³ ,
- μμΌλ©΄ `__proto__`λ₯Ό κ²μν΄μ μμΌλ©΄ κ·Έ λ©μλλ₯Ό μ€ννκ³ ,
- μμΌλ©΄ λ€μ `__proto__`λ₯Ό κ²μν΄μ μ€ννλ μμΌλ‘ μ§ννλ€.

<br />

| μ°Έκ³ λ‘, λ©μλ μ€λ²λΌμ΄λ(method overriding)μ λμΌν λ§₯λ½μ΄λ€.                                                                                                                                                                                                                                                        |
| :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| λ©μλ μμ λ©μλλ₯Ό μμ΄μμ λ€λ νν.                                                                                                                                                                                                                                                                                |
| μλ°μ€ν¬λ¦½νΈ μμ§μ΄ λ©μλλ₯Ό μ°Ύλ λ°©μμ κ°μ₯ κ°κΉμ΄ λμμΈ μμ μ νλ‘νΌν°λ₯Ό κ²μνκ³ , μμΌλ©΄ κ·Έ λ€μμΌλ‘ κ°κΉμ΄ λμμΈ `__proto__`λ₯Ό κ²μνλ μμλ‘ μ§νλλ€. '**κ΅μ²΄**'νλ ννλΌλ©΄ μλ³Έμλ μ κ·Όν  μ μλ ννκ° λκ² μ§λ§ '**μΉλ**, **λ?μ΄ μμ΄**' ννλΌλ©΄ μλ³Έμ΄ μλμ μ μ§λκ³  μκ³  μλ³Έμ μ κ·Όν  μ μλ€. |

<br />

![](https://images.velog.io/images/april_5/post/ff511f17-c666-49d0-8c66-2a1dd5b7823e/%E1%84%91%E1%85%B3%E1%84%85%E1%85%A9%E1%84%90%E1%85%A9%E1%84%90%E1%85%A1%E1%84%8B%E1%85%B5%E1%86%B8.png)

<br />
<br />

### βοΈ κ°μ²΄ μ μ© λ©μλμ μμΈμ¬ν­

- μ΄λ€ μμ±μ ν¨μμ΄λ  `prototype`μ λ°λμ κ°μ²΄μ΄λ€.
- `Object.prototype`μ΄ μΈμ λ νλ‘ν νμ μ²΄μΈμ μ΅μλ¨μ μ‘΄μ¬νλ€.
- λ°λΌμ, κ°μ²΄μμλ§ μ¬μ©ν  λ©μλλ λ€λ₯Έ μ¬λ λ°μ΄ν° νμμ²λΌ νλ‘ν νμ κ°μ²΄ μμ μ μν  μκ° μλ€.
- λ°λΌμ, `Object.prototype`μ μλ λ©μλλ μ΄λ μλ£νμ΄λ μΈμ€ν΄μ€μμ λ°λ‘ νΈμΆν  μ μλ€.
- λ°λΌμ, κ°μ²΄μμλ§ μ¬μ©ν  λ©μλλ `prototype` μμ μ μνμ§ μλλ€. κ°μ²΄μμλ§ μ¬μ©ν  λ©μλλ₯Ό `prototype` λ΄λΆμ μ μνλ©΄ λ€λ₯Έ λ°μ΄ν°νμλ νλ‘ν νμ μ²΄μΈμ νκ³  μ¬λΌμμ ν΄λΉ λ©μλλ₯Ό μ¬μ©ν  μ μκ² λκΈ° λλ¬Έμ΄λ€.
- μ΄λ° λ©μλλ₯Ό Static methodλΌ νλ€.

<br />
<br />

### βοΈ λ€μ€ νλ‘ν νμ μ²΄μΈ

νλ‘ν νμ μ²΄μΈμ 2λ¨κ³ μ΄μμΌλ‘ μ°κ²°νκ³  μΆλ€λ©΄,

> `__proto__`κ° κ°λ¦¬ν€λ λμ, μ¦ μμ±μ ν¨μμ `prototype`μ΄
> μ°κ²°νκ³ μ νλ μμ μμ±μ ν¨μμ μΈμ€ν΄μ€λ₯Ό λ°λΌλ³΄κ²λ ν΄μ£Όλ©΄ λλ€.

```jsx
const Grade = () => {
  const ars = Array.prototype.slice.call(arguments);
  for (var i = 0; i < args.length; i++) {
    this[i] = args[i];
  }
  this.length = args.length;
};

const g = new Grade(100, 80); // (1)
```

(1) λ³μ `g`λ `Grade`μ μΈμ€ν΄μ€λ₯Ό λ°λΌλ³Έλ€.
`Grade`μ μΈμ€ν΄μ€λ μ¬λ¬ κ°μ μΈμλ₯Ό λ°μ κ°κ° μμλλ‘ μΈλ±μ±ν΄μ μ μ₯νκ³  `length` νλ‘νΌν°κ° μ‘΄μ¬νλ λ±μΌλ‘ λ°°μ΄μ ννλ₯Ό μ§λμ§λ§, λ°°μ΄μ λ©μλλ₯Ό μ¬μ©ν  μ μλ μ μ¬λ°°μ΄κ°μ²΄μ΄λ€.
`g { 0: 100, 1: 80, length: 2 }`

λ°λΌμ, λ°°μ΄ λ©μλλ₯Ό λ°λ‘ μ¬μ©ν  μ μλ€.
μ΄λ₯Ό κ°λ₯νκ² νκ³  μΆλ€λ©΄, μΈμ€ν΄μ€ gμ `__proto__`, μ¦ `Grade.prototype`μ΄ λ°°μ΄μ μΈμ€ν΄μ€λ₯Ό λ°λΌλ³΄κ² ν΄μ£Όλ©΄ λλ€.

<br /><br />

---

### β¨ tl;dr

- μ΄λ€ μμ±μ ν¨μλ₯Ό `new` μ°μ°μμ ν¨κ» νΈμΆνλ©΄
  - `Constructor`μμ μ μλ λ΄μ©μ λ°νμΌλ‘ μλ‘μ΄ μΈμ€ν΄μ€κ° μμ±λλλ°,
  - μ΄ μΈμ€ν΄μ€μλ `__proto__`λΌλ, `Constructor`μ `ptototype` νλ‘νΌν°λ₯Ό μ°Έμ‘°νλ νλ‘νΌν°κ° μλμΌλ‘ λΆμ¬λλ€.
  - `__proto__`λ μλ΅ κ°λ₯ν μμ±μ΄λΌμ,
  - μΈμ€ν΄μ€λ `Constructor.ptototype`μ λ©μλλ₯Ό λ§μΉ μμ μ λ©μλμΈ κ²μ²λΌ νΈμΆν  μ μλ€.

<br />

- `Constructor.ptototype`μλ `constructor`λΌλ νλ‘νΌν°κ° μλλ°, μ΄λ λ€μ μμ±μ ν¨μ μμ μ κ°λ¦¬ν¨λ€.
  - μ΄ νλ‘νΌν°λ **μΈμ€ν΄μ€κ° μμ μ μμ±μ ν¨μκ° λ¬΄μμΈμ§λ₯Ό μκ³ μ ν  λ νμν μλ¨**μ΄λ€.

<br />

- μ§κ°μΌκ°νμ λκ°μ  λ°©ν₯, μ¦ `__proto__` λ°©ν₯μ κ³μ μ°Ύμκ°λ©΄ μ΅μ’μ μΌλ‘λ `Object.ptototype`μ λλ¬νκ² λλ€.
  - μ΄λ° μμΌλ‘ `__proto__` μμμ λ€μ `__proto__`λ₯Ό μ°Ύμκ°λ κ³Όμ μ <span style="color:dodgerblue">**νλ‘ν νμ μ²΄μ΄λ**</span>μ΄λΌκ³  νλ©°,
  - μ΄ νλ‘ν νμ μ²΄μ΄λμ ν΅ν΄ κ° νλ‘ν νμ λ©μλλ₯Ό μμ μ κ²μ²λΌ νΈμΆν  μ μλ€.
  - μ΄λ μ κ·Ό λ°©μμ μμ μΌλ‘λΆν° κ°μ₯ κ°κΉμ΄ λμλΆν° μ μ°¨ λ¨Ό λμμΌλ‘ λμκ°λ©°, μνλ κ°μ μ°ΎμΌλ©΄ κ²μμ μ€λ¨νλ€.

<br />

- `Object.ptototype`μλ λͺ¨λ  λ°μ΄ν° νμμμ μ¬μ©ν  μ μλ λ²μ©μ μΈ λ©μλλ§μ΄ μ‘΄μ¬νλ©°
  - κ°μ²΄ μ μ© λ©μλλ μ¬λ λ°μ΄ν° νμκ³Ό λ¬λ¦¬ `Object` μμ±μ ν¨μμ μ€νν±νκ² λ΄κ²¨ μλ€.

<br />

- <span style="color:dodgerblue">**νλ‘ν νμ μ²΄μΈ**</span>μ λ°λμ 2λ¨κ³λ‘λ§ μ΄λ€μ§λ κ²μ΄ μλλΌ λ¬΄νλλ‘ μμ±ν  μλ μλ€.
