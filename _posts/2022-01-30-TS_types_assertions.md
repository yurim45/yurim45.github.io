---
title: "๐ซTS:: ๊ฑด๋ฐฉ์ง ๋์ Type Assertion!"
tags:
  - [Typescript]
permalink: /study/TS/types_assertions

navigation: true
toc: true
toc_sticky: true

date: 2022-01-30
last_modified_at: 2022-01-30
---

![](https://images.velog.io/images/april_5/post/fef3266f-5808-4e74-a394-3cc0c8bd35a3/typescript.png)

## | Type [Assertion](https://ko.wikipedia.org/wiki/%ED%91%9C%EB%AA%85)!

TypeScript์ ํ์ ํ๋ช์ ํ๋ก๊ทธ๋๋จธ๊ฐ ์ปดํ์ผ๋ฌ์๊ฒ
<i>"๋ด๊ฐ ๋๋ณด๋ค ํ์์ ๋ ์ ์๊ณ  ์๊ณ , ๋์ ์ฃผ์ฅ์ ๋ํด ์์ฌํ์ง ๋ง๋ผ"</i>
๊ณ  ํ๋ ๊ฒ๊ณผ ๊ฐ๋ค

> `Type Assertion`: ํ์์ ๊ฐ์ํด์ผ ํ๋ ๊ฒฝ์ฐ์ ์ฌ์ฉ?? ๋จ, ์ง์ํ๋ ๊ฒ์ด ์ข๋ค. ๐ฉ

<br />

### โ๏ธ Type Assertion ์์ 1

```tsx
function jsStrFunc(): any {
  return "hello";
}
const result = jsStrFunc();
console.log((result as string).length); // (1)
console.log((<string>result).length);
```

(1) `result as string`: result๋ string์ด์ผ!! string์์ ํ์ธํ๊ธฐ ๋๋ฌธ์ string method๋ฅผ ์ฌ์ฉํ  ์ ์๋ค

![](https://images.velog.io/images/april_5/post/93dca28a-a421-4aaf-9d72-604346b2c066/image.png)

<br />

### โ๏ธ Type Assertion๋ฅผ ์ง์ํด์ผ ํ๋์ด์ ! ์์ 2

```tsx
function jsStrFunc(): any {
  return 2; // (2) ๐ฑ์๋์์ ๋ฌธ์์ด์์๋ ์ซ์๋ฅผ ์ง์ ํ  ๊ฒฝ์ฐ์๋ ์๋ฌ๋ ๋ฐ์ํ์ง ์๋๋ค;;
}
const result = jsStrFunc();
console.log((result as string).length); // (3)
console.log((<string>result).length); // ์์ as์ ๊ฐ์ ๋ฌธ๋ฒ
```

(3) ๐ฑ๐ฑ `as`๋ฅผ ๋ถํ ํ์์ ์ฅ๋ดํ๊ธฐ ๋๋ฌธ์ ์ปดํ์ผ ์๋ฌ๋ ๋ฐ์ํ์ง ์๋๋ค;; ๋ค๋ง ์คํํ  ๊ฒฝ์ฐ `undefined`๊ฐ ์ถ๋ ฅ๋๋ค.

<br />

### โ๏ธ Type Assertion ์์ 3: Type Assertion์ ์ง์ํด์ผ ํ๋ ์ด์ !! ๐ฑ

```tsx
const wrong: any = 5;
console.log((wrong as Array<number>).push(1)); // ๐ฑ
```

![](https://images.velog.io/images/april_5/post/4e447eb5-babc-4ffe-9433-5a5bf9601387/image.png)

> ์ ํ๋ฆฌ์ผ์ด์์ด ์ฃฝ์ด๋ฒ๋ ธ์ด!!! ๐ฑ๐ฑ๐ฑ๐ฑ๐ฑ๐ฑ

<br />

### โ๏ธ Type Assertion ์์ 4: `!`๋ฅผ ๋ถํ๋ฉด ํ์ ํด

```tsx
function findNumbers(): number[] | undefined {
  return undefined;
}
const numbers = findNumbers()!;
numbers.push(2); // ๐ฑ numbers๋ number[]์ผ์๋ ์๊ณ ,
// undefined ์ผ์๋ ์๊ธฐ ๋๋ฌธ์
// push()๋ฅผ ์ฌ์ฉํ  ๊ฒฝ์ฐ ์๋ฌ ๋ฐ์.
```

> ๐ <span style="color:tomato">**`!`๋ฅผ ๋ถํ๋ฉด ํ์ ํด**</span>๋ฅผ ํํ.
> ์ฆ, numbers๋ ๋ฐฐ์ด์์ ํ์ ํ๋ฏ๋ก push๋ฅผ ์ฌ์ฉํ  ์ ์์ด!
> ์ฐธ๊ณ ๋ก `as`๋ <span style="color:tomato">**์ฅ๋ดํด!**</span>๋ฅผ ํํ.

<br />

### โ๏ธ Type Assertion [์์ 5](https://www.typescriptlang.org/docs/handbook/2/everyday-types.html#type-assertions)

```tsx
const myCanvas = document.getElementById("main_canvas") as HTMLCanvasElement;

const button = document.querySelector("class")!;
```

<br />
