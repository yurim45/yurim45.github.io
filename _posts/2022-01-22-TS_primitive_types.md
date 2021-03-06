---
title: "๐ซTS:: Typescript ๊ธฐ๋ณธ ํ์ ์์๋ณด๊ธฐ!"
tags:
  - [Typescript]
permalink: /study/TS/primitive_types

navigation: true
toc: true
toc_sticky: true

date: 2022-01-22
last_modified_at: 2022-01-22
---

![](https://images.velog.io/images/april_5/post/fef3266f-5808-4e74-a394-3cc0c8bd35a3/typescript.png)

# [๊ธฐ๋ณธ ํ์](https://www.typescriptlang.org/docs/handbook/basic-types.html)

## 1๏ธโฃ ๊ธฐ๋ณธํ์: `number`, `string`, `boolean`, `undefined`, `null`

### โ๏ธ `number`

```tsx
let decimal: number = 6;
let hex: number = 0xf00d;
let binary: number = 0b1010;
let octal: number = 0o744;
let big: bigint = 100n;
```

<br />

### โ๏ธ `string`

```tsx
let color: string = "blue";
color = "red";

let name: string = `april`;
let age: number = 35;
let sentence: string = `Hello, my name is ${name}.
 
I'll be ${age + 1} years old next month.`;
```

<br />

### โ๏ธ `boolean`

```tsx
let isDone: boolean = false;
```

<br />

### โ๏ธ `undefined`

> `undefined`: ๊ฐ์ด ์๋์ง ์๋์ง ์ ํด์ง์ง ์์ ์ํ, ํํ ๋น์๋์ง ์๋์ง ๊ฒฐ์ ๋์ง ์์ ์ํ

```tsx
let name: undefined; // ๐ฉ์ด๋ฐ์์ผ๋ก ํ ๋นํ์ง ์์

let age: number | undefined; // number ๋๋ undefined์ ํ ๋นํ  ์ ์๋ค
age = undefined;
age = 21;
```

<br />

### โ๏ธ `null`

> `null`: ํํ ๋น์๋ค

```tsx
let person: null; // ๐ฉ๋ง์ฐฌ๊ฐ์ง๋ก ์ด๋ฐ์์ผ๋ก ํ ๋นํ์ง ์์

let person2: string | null;
person2 = null;
person2 = "yurim";
```

<br />

---

## 2๏ธโฃ ๊ธฐ๋ณธํ์: `unknown`, `any`, `void`, `never`, `object`

### โ๏ธ ๐ฉ`unknown`

> `unknown` ์ด๋ค ํ์์ธ์ง ์ ์ ์๋ค // ๐ฉ

```tsx
let notSure: unknown = 0; // number๋ฅผ ํ ๋น ํ์์๋
notSure = "hi"; // string์ ํ ๋นํ  ์ ์๋ค
notSure = true;
```

<br />

### โ๏ธ ๐ฉ`any`

> `any` ์ด๋ค ๊ฒ์ด๋  ๋ค ๋ด์ ์ ์๋ค // ๐ฉ

```tsx
let anything: any = 0; // number๋ฅผ ํ ๋น ํ์์๋
anything = "hi"; // string์ ํ ๋นํ  ์ ์๋ค
anything = true;
```

<br />

### โ๏ธ `void`

> `void` ํจ์์ ๋ฆฌํด์ด ์์ ๋์ ํ์. ์๋ต๋ ๊ฐ๋ฅํ๋ค

```tsx
function print(): void {
  console.log("hello");
  return;
}
let unusable: void = undefined; // ๐ฉ undefined ๋ฐ์ ํ ๋น์ด ์๋๊ธฐ ๋๋ฌธ์ ์ฌ์ฉํ์ง ์์
```

<br />

### โ๏ธ `never`

> `never` ์๋ฌ๊ฐ ๋ฐ์ํ๋ฉด ์ดํ๋ฆฌ์ผ์ด์์ด ์ฃฝ์ผ๋๊น ๋ฆฌํด๊ฐ์ด ์ ๋ ์๋ค. ๊ทธ๋ด ๋ never ํ์์ ์ง์ .
> never ํ์์ ์ง์ ํ๋๋ฐ ๋ฆฌํด์ด ์๋ค๋ฉด ์๋ฌ ๋ฐ์.

```tsx
// throwError ์ดํ๋ฆฌ์ผ์ด์์์ ์์์น ๋ชปํ ์๋ฌ ๋ฐ์๊ฐ ๋ฐ์ํ  ๊ฒฝ์ฐ ์ฒ๋ฆฌํ๋ ํจ์
function throwError(message: string): never {
  // message -> server (log)
  throw new Error(message);
  while (true) {}
}
let neverEnding: never; // ๐ฉ

// objet
let obj: object; // ๐ฉ
function acceptSomeObject(obj: object) {}
acceptSomeObject({ name: "ellie" });
acceptSomeObject({ animal: "dog" });
```

<br />

### โ๏ธ `object`

> `object`: ์๋ฐ์คํฌ๋ฆฝํธ์ ๊ฐ์ฒด ํ์๊ณผ ๋์ผ.
> ๊ฐ์ฒด ์์ฑ์ ๋ํ ์ ๋ณด๊ฐ ์๊ธฐ ๋๋ฌธ์ ํ์ ์๋ฌ๊ฐ ๋ฐ์ํ๋ค. ์์ฑ ์ ๋ณด๋ฅผ ํฌํจํด์ ํ์์ ์ ์ํ๊ธฐ ์ํด์๋ ์ธํฐํ์ด์ค([interface](https://velog.io/@april_5/%ED%95%A8%EC%88%98%EC%97%90%EC%84%9C-%ED%83%80%EC%9E%85-%EC%9D%B4%EC%9A%A9%ED%95%98%EA%B8%B0-JS-TS))๋ฅผ ์ฌ์ฉํด์ผ ํ๋ค.

```tsx
interface Person {
  name: string;
  age?: number; // ๋ฌผ์ํ๊ฐ ๋ค์ด๊ฐ๋ค๋ ๊ฒ์, ์ค์ ์ ํด๋ ๋๊ณ  ์ํด๋ ๋๋ ๊ฐ์ด๋ผ๋ ๊ฒ์ ์๋ฏธํฉ๋๋ค.
}

const person: Person = {
  name: "april",
  age: 20,
};

// interface ๋ฅผ extends ํด์ ์์๋ฐ๊ธฐ
interface Developer extends Person {
  skills: string[];
}

const expert: Developer = {
  name: "april",
  skills: ["typescript", "react"],
};

const people: Person[] = [person, expert];
```

<br />
