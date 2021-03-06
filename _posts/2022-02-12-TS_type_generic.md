---
title: "π«TS:: λλμ΄! <T>μ λ€λ¦­(Generics)π«"
tags:
  - [Typescript]
permalink: /study/TS/generic

navigation: true
toc: true
toc_sticky: true

date: 2022-02-12
last_modified_at: 2022-02-12
---

![](https://images.velog.io/images/april_5/post/3e7eaeea-e9c5-4886-8c4a-fad46fc21452/%E1%84%8C%E1%85%A6%E1%84%82%E1%85%A6%E1%84%85%E1%85%B5%E1%86%A8.png)

> π‘ <span style='color:royalblue'>**μ μ°**</span>νκ³ ! <span style='color:royalblue'>**νμμ΄ λ³΄μ₯**</span>λκ³ , <span style='color:royalblue'>**μ¬μ¬μ©μ±**</span>μ΄ λμ <span style='color:fuchsia'>**μ λ€λ¦­(Generics)!!**</span>

## [μ λ€λ¦­](https://www.typescriptlang.org/ko/docs/handbook/2/generics.html)μ΄λ?

> μ μΈ μμ μ΄ μλλΌ <span style='color:royalblue'>**μμ± μμ μ νμμ λͺμ**</span>νμ¬ νλμ νμλ§μ΄ μλ <span style='color:fuchsia'>**λ€μν νμμ μ¬μ©ν  μ μλλ‘**</span> νλ κΈ°λ²

- Genericμ΄λ λ°μ΄ν°μ νμμ μΌλ°ννλ€(generalize)νλ€λ μλ―Έ
- <span style='color:royalblue'>**νμ μ λ³΄κ° λμ μΌλ‘ κ²°μ λλ νμ**</span>
  - κ°μ κ·μΉμ μ¬λ¬ νμμ μ μ©ν  μ μκΈ° λλ¬Έμ
  - νμ μ½λλ₯Ό μμ±ν  λ λ°μν  μ μλ <span style='color:royalblue'>**μ€λ³΅ μ½λλ₯Ό μ κ±°**</span>ν  μ μλ€
- `C#`κ³Ό `Java` κ°μ μΈμ΄μμ, **μ¬μ¬μ©μ±μ΄ λμ μ»΄ν¬λνΈλ₯Ό λ§λ€ λ μμ£Ό νμ©**νλ μ λ€λ¦­(Generics)!!!
  - μ¦, **λ¨μΌ νμμ΄ μλ λ€μν νμμμ μλ**νλ μ»΄ν¬λνΈλ₯Ό μμ±ν  μ μλ€.
- μ λ€λ¦­μ ν΅ν΄ **μ¬λ¬ νμμ μ»΄ν¬λνΈ**λ **μμ λ§μ νμ**μ μ¬μ©ν  μ μλ€.

<br />

---

## [μ λ€λ¦­ κΈ°λ³Έ λ¬Έλ²](https://joshua1988.github.io/ts/guide/generics.html#%EC%A0%9C%EB%84%A4%EB%A6%AD%EC%9D%98-%ED%95%9C-%EC%A4%84-%EC%A0%95%EC%9D%98%EC%99%80-%EC%98%88%EC%8B%9C)

### βοΈ κΈ°λ³Έ μ½λ

```ts
// textλΌλ νλΌλ―Έν°μ κ°μ λκ²¨ λ°μ textλ₯Ό λ°ννλ ν¨μ
const getText = (text) => {
  return text;
};

// νλΌλ―Έν°μ μ΄λ€ κ°μ λκ²¨μ£ΌλλΌλ κ·Έλλ‘ λ°νλλ€.
getText("april"); // 'april'
getText(20); // 10
getText(true); // true
```

<br />

### βοΈ μ λ€λ¦­ μ½λ

```ts
// μ λ€λ¦­ κΈ°λ³Έ λ¬Έλ²μ΄ μ μ©λ ν¨μ
const getText = <T>(text: T): T => {
  return text;
};

// ν¨μλ₯Ό νΈμΆν  λ, ν¨μ μμμ μ¬μ©ν  νμμ λκ²¨μ€ μ μλ€
getText<string>("april"); // 'april'
getText<number>(20); // 10
getText<boolean>(true); // true
```

<br />

### βοΈ λ κ° μ΄μμ μ λ€λ¦­ μ¬μ©ν μ½λ

```ts
// λ κ°μ μ λ€λ¦­μ΄ μ μ©λ ν¨μ
const getUserInfo = <T, K>(name: T, age: K): [T, K] => {
  return [name, age];
};

// ν¨μλ₯Ό νΈμΆν  λ, ν¨μ μμμ μ¬μ©ν  νμμ λκ²¨μ€ μ μλ€
getUserInfo("april", 20);
```

<br />

---

## μ λ€λ¦­μ μ¬μ©νλ μ΄μ ? π€

νλΌλ―Έν°μ νμμ΄ μ¬λ¬ μ’λ₯μΌ λ `any`λ₯Ό μ¬μ©νκ² λλλ°,
`any` νμμ νμ κ²μ¬λ₯Ό νμ§ μκΈ° λλ¬Έμ λ¬Έμ κ° μκΈΈ μ μλ€

### μ λ€λ¦­μ μ¬μ©νμ§ μμ μ½λ

```ts
const getText = (text: any): any => {
  return text;
};
```

<br />

### μ λ€λ¦­ μ μ© μ½λ

λ¨Όμ  ν¨μμ μ΄λ¦ λ°λ‘ λ€μ `<T>` λΌλ μ½λλ₯Ό μΆκ°νκ³  ν¨μμ μΈμμ λ°ν κ°μ λͺ¨λ `T` λΌλ νμμ μΆκ°νλ©΄,
ν¨μλ₯Ό νΈμΆν  λ λκΈ΄ νμμ λν΄ νμμ€ν¬λ¦½νΈκ° μΆμ ν  μ μκ² λλ€.

> π‘ λ°λΌμ, ν¨μμ μλ ₯ κ°μ λν νμκ³Ό μΆλ ₯ κ°μ λν νμμ΄ λμΌνμ§ κ²μ¦ν  μ μκ² λλ€.

```ts
const getText = <T>(text: T): T => {
  return text;
};
```

<br />

---

## μ λ€λ¦­ μμ  μ½λ

> λ°°μ΄μ μμ±νλ ν¨μλ‘ μ΅νλ, μ λ€λ¦­ μμ  μ½λ

### βοΈ μ λ€λ¦­ μ¬μ© μ 

μ«μ λ°°μ΄μ μμ±νλ ν¨μμ λ¬Έμ λ°°μ΄μ μμ±νλ ν¨μ π³
μ€λ³΅λ μ½λκ° λ§λ€... π¬π?βπ¨

```ts
const makeNumberArray = (defaultValue: number, size: number): number[] => {
  const arr: number[] = [];
  for (let i = 0; i < size; i++) {
    arr.push(defaultValue);
  }
  return arr;
};

const makeStringArray = (defaultValue: string, size: number): string[] => {
  const arr: string[] = [];
  for (let i = 0; i < size; i++) {
    arr.push(defaultValue);
  }
  return arr;
};

const arr1 = makeNumberArray(1, 10);
const arr2 = makeStringArray("empty", 10);
```

<br />

### βοΈ μ λ€λ¦­μΌλ‘ μ½λ λ¦¬νν λ§ νκΈ°

```ts
const makeArray = <T>(defaultValue: T, size: number): T[] => {
  const arr: T[] = [];
  for (let i = 0; i < size; i++) {
    arr.push(defaultValue);
  }
  return arr;
};

const arr1 = makeArray<number>(1, 10);
const arr2 = makeArray<string>("empty", 5);

// makeArray ν¨μμ μ²« λ²μ§Έ νλΌλ―Έν°λ₯Ό μλ©΄ νμ Tλ μ μ μκΈ° λλ¬Έμ,
// νΈμΆ μ νμ Tμ μ λ³΄λ₯Ό λͺμμ μΌλ‘ μ λ¬νμ§ μμλ λλ€.
const arr3 = makeArray(1, 10);
const arr4 = makeArray(1, 10);
```

<br />

---

## `extends` ν€μλλ‘ μ λ€λ¦­ νμ μ ννκΈ°

<span style='color:royalblue'>**λ¦¬μ‘νΈ**</span>μ κ°μ λΌμ΄λΈλ¬λ¦¬μ APIλ <span style='color:royalblue'>**μλ ₯ κ°λ₯ν κ°μ λ²μλ₯Ό μ ν**</span>νλ€.
μλ₯Ό λ€μ΄, <span style='color:royalblue'>**λ¦¬μ‘νΈμ μμ±κ° μ μ²΄λ κ°μ²΄ νμλ§ νμ©**</span>λλ€.
μ΄λ₯Ό μν΄ <u><span style='color:fuchsia'>νμμ€ν¬λ¦½νΈμ μ λ€λ¦­μ **νμμ μ’λ₯λ₯Ό μ ν**ν  μ μλ κΈ°λ₯μ μ κ³΅</span></u>νλ€.

<br />

### βοΈ μμ  μ½λ

```ts
// μ λ€λ¦­ T νμμ number | stringμ ν λΉ κ°λ₯ν νμμΌλ‘ μ ν
const identity = <T extends number>(p1: T): T => {
  return p1;
};

identity(1);
identity("a");
identity([]); // νμ μλ¬
```

<br />

### βοΈ μμ  μ½λ

```ts
// μ λ€λ¦­ T νμμ number | stringμ ν λΉ κ°λ₯ν νμμΌλ‘ μ ν
const identity = <T extends number>(p1: T): T => {
  return p1;
};

identity(1);
identity("a");
identity([]); // νμ μλ¬
```

<br />

### βοΈ μμ  μ½λ2

```ts
interface IPerson {
  name: string;
  age: number;
}

interface IKorean extends IPerson {
  liveInSeoul: boolean;
}

// μ λ€λ¦­ Tλ IPersonμ ν λΉ κ°λ₯ν νμμ΄μ΄μΌ νλ€
// μ λ€λ¦­ Kλ IPersonμ μμ± μ΄λ¦μ΄μ΄μΌ νλ€.
// μ°Έκ³ λ‘ keyofλ μΈν°νμ΄μ€μ λͺ¨λ  μμ± μ΄λ¦μ μ λμ¨ νμμΌλ‘ λ§λ€μ΄ μ€λ€.
const swapProperty = <T extends IPerson, K extends keyof IPerson>(
  p1: T,
  p2: T,
  name: K
): void => {
  const temp = p1[name];
  p1[name] = p2[name];
  p2[name] = temp;
};

const p1: IKorean = {
  name: "april",
  age: 20,
  liveInSeoul: true,
};

const p2: IKorean = {
  name: "yrkim",
  age: 20,
  liveInSeoul: true,
};

swapProperty(p1, p2, "age"); // p1, p2λ IPersonμ ν λΉ κ°λ₯νκΈ° λλ¬Έμ νμμλ¬κ° λ°μνμ§ μλλ€
```

<br />
