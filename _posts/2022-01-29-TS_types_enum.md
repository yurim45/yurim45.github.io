---
title: "๐ซTS:: enum์ ๋ฌด์์ด๊ณ  ์ข์๊ฑด๊ฐ? ๐ค"
tags:
  - [Typescript]
permalink: /study/TS/types_enum

navigation: true
toc: true
toc_sticky: true

date: 2022-01-29
last_modified_at: 2022-01-29
---

![](https://images.velog.io/images/april_5/post/fef3266f-5808-4e74-a394-3cc0c8bd35a3/typescript.png)

## enum์ ๋ฌด์์ธ๊ณ ?๐ค

> ๐ก `enum`: ์ฌ๋ฌ ๊ด๋ จ๋ ์์ ๊ฐ๋ค์ ํ ๊ณณ์ ๋ชจ์์ ์ ๋ฆฌํ  ์ ์๋๋ก ํ๋ ํ์

JavaScript์์๋ enum type์ด ์กด์ฌํ์ง ์์ผ๋ฏ๋ก,
TypeScript์์ ์ ์ฒด์ ์ผ๋ก ์ ๊ณตํ๋ ํ์ ์ค ํ๋.

<br />

### โ๏ธ enum ์์ 1

> JavaScript์์, ๋ณดํต ์์(๋ณํ์ง ์๋ ์, constant)๋ฅผ ์ ์ธํ  ๋์๋ ๋ณ์๋ช์ ๋๋ฌธ์๋ก ์ ์ธํ์ง๋ง,
> TypeScript์์ `enum` ์ ์ธํ  ๋์๋ ์ฒซ ๊ธ์๋ง ๋๋ฌธ์๋ก ์ ์ธํ๋ค.

```tsx
// JavaScript
const MAX_NUM = 6;
const MAX_STUDENTS_PER_CLASS = 10;

const MONDAY = 0;
const TUESDAY = 1;
const WEDNESDAY = 2;
// JavaScript์์๋ ๊ด๋ จ๋ ๋ฐ์ดํฐ๋ฅผ ๋ฌถ์ ์ ์๋ ํ์์ด ๋ณ๋ ์กด์ฌํ์ง ์์ผ๋ฏ๋ก, ์๋์ฒ๋ผ Object๋ก ๊ตฌํ.
const DAYS_ENUM = Object.freeze({ MONDAY: 0, TUESDAY: 1, WEDNESDAY: 2 });
const dayOfToday = DAYS_ENUM.MONDAY;
```

![](https://images.velog.io/images/april_5/post/1c481436-a77a-41d7-976f-fa3320f28370/image.png)

```tsx
// TypeScript
enum Days {
  Monday,
  Tuesday,
  Wednesday,
  Thursday,
  Friday,
  Saturday,
  Sunday,
}
console.log(Days.Monday);

let day: Days = Days.Saturday;
day = Days.Tuesday;
```

ํ์์คํฌ๋ฆฝํธ์์ `enum`์ ์ฌ์ฉํ๋ฉด

- ์ ํํ ๊ฐ์ด ์ซ์ 0๋ถํฐ ์ฆ๊ฐํ๋ฉด์ ๊ฐ์ ๊ฐ์ง๊ฒ ๋๊ณ 
  - ์์) `console.log(Days.Monday);`๋ 0์ด ์ถ๋ ฅ๋จ

<br />

- 0์ด ์๋ 1๋ถํฐ ์์ํ๊ณ  ์ถ๋ค๋ฉด ์ง์ ํ๋ฉด ๋๋ค
  ![](https://images.velog.io/images/april_5/post/c8a2c93d-24d7-47a0-bda4-7d8d8b1d28ba/image.png)
  - ์์) `console.log(Days.Monday);`๋ 1์ด ์ถ๋ ฅ๋จ

<br />

- ์ซ์๊ฐ ์๋ ๋ฌธ์์ด๋ ์ง์ ์ด ๊ฐ๋ฅํ๋ค.
  ![](https://images.velog.io/images/april_5/post/95335c1e-e079-4ae6-82bf-54a862759c13/image.png)
  - ์์) `console.log(Days.Monday);`๋ monday์ด๊ฐ ์ถ๋ ฅ๋จ

<br />

### ๐ฑ ํ์์คํฌ๋ฆฝํธ์์ enum์ ์ฌ์ฉํ์ง ์๋ ์ด์ !!!!!!

```tsx
enum Days {
  Monday,
  Tuesday,
  Wednesday,
}

let day: Days = Days.Monday;

day = 10; // enum type์ด ์ง์ ๋ ๋ณ์์ ๋ค๋ฅธ ์ซ์๋ฅผ ํ ๋นํด๋ ์๋ฌ๊ฐ ๋์ง ์๋๋ค ๐ฑ
```

---

### โจ tl;dr

๐ ํ์์คํฌ๋ฆฝํธ์์ `enum` ํ์์ ์ฌ์ฉํ์ง ์๋๋ค. ์ด์ ๋,

- enum์ผ๋ก ํ์์ด ์ง์ ๋ ๋ณ์์ ๋ค๋ฅธ ์ซ์๋ฅผ ํ ๋นํ  ์ ์๊ธฐ ๋๋ฌธ์ ์ฐ๊ด๋์ง ์๋ ์ซ์๋ ํ ๋นํ  ์ ์๋ค.

๋ฐ๋ผ์ <span style="color:dodgerblue">**ํ์์คํฌ๋ฆฝํธ์์๋ enum ๋์  union ํ์์ ์ฌ์ฉ**</span>ํ๋ค.
