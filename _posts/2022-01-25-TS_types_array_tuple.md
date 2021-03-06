---
title: "๐ซTS:: โจ ๋ฐฐ์ด๊ณผ ํํ, ์ธ์  ํํ์ ์ฌ์ฉํด์ผ ํ ๊น?"
tags:
  - [Typescript]
permalink: /study/TS/types_array_tuple

navigation: true
toc: true
toc_sticky: true

date: 2022-01-25
last_modified_at: 2022-01-25
---

![](https://images.velog.io/images/april_5/post/fef3266f-5808-4e74-a394-3cc0c8bd35a3/typescript.png)

# โจ`Array`์ `Tuple`

## ๐ท `Array`

<br />

### โ๏ธ `Array` ์์ 1

```tsx
let list: number[] = [1, 2, 3];
let list: Array<number> = [1, 2, 3];
```

<br />

### โ๏ธ `Array` ์์ 2

```tsx
// Array
const fruits: string[] = ["๐", "๐"];
const scroes: Array<number> = [1, 3, 4]; // number[] = [1, 2, 3];

function printArray(fruits: readonly string[]) {
  // readonly ๋ผ๋ ํค์๋๋ ๋ง ๊ทธ๋๋ก ์ฝ๊ธฐ ์ ์ฉ
  // object์ ๋ถ๋ณ์ฑ์ ์งํค๋ ๊ฒ์ ๋งค์ฐ ์ค์ํ๋ฏ๋ก, readonly๊ฐ ๋ง์ด ์ฌ์ฉ ๋จ
}
```

<br />

---

## ๐ท `Tuple`

> `Tuple`์ ๋ฐฐ์ด์ ๋ฐฐ์ด์ธ๋ฐ ์๋ก ๋ค๋ฅธ ํ์์ ๊ฐ์ง ์ ์๋ ๋ฐฐ์ด

<br />

### โ๏ธ `Tuple` ์์ 1

```tsx
// Declare a tuple type
let x: [string, number];

// Initialize it
x = ["hello", 10]; // OK

// Initialize it incorrectly
x = [10, "hello"]; // ๐ฉError
```

<br />

### โ๏ธ `Tuple` ์์ 2

> `Tuple`์ ์ฌ์ฉํ๋ ๊ณณ์ด๋ผ๋ฉด `interface`, `type alias`, `class` ๋ฑ์ผ๋ก ๋์ฒดํด์ ์ฌ์ฉํ๋ ๊ฒ์ ์ถ์ฒ!

- Tuple์ ์ ๊ทผํ  ๋์, index๋ก ์ ๊ทผ์ด ๊ฐ๋ฅํ๋ฐ ์ด๋ฌ๋ฉด ์ด๋ค ๋ฐ์ดํฐ๊ฐ ๋ค์ด์๋์ง ๋ฐ๋ก ํ์ธ์ด ์ด๋ ค์ฐ๋ฏ๋ก <span style='color:tomato'>**๊ฐ๋์ฑ โฌ๏ธ**</span>
  โก๏ธ ์ด๋ฐ ๊ฒฝ์ฐ <span style='color:dodgerblue'>**๊ตฌ์กฐ ๋ถํด ํ ๋น**</span>๋ฅผ ํ์ฉํ์!

```tsx
let student: [string, number];
student = ["name", 123];
student[0]; // name
student[1]; // 123
const [name, age] = student; // ๊ตฌ์กฐ ๋ถํด ํ ๋น Destructuring
```

<br />

### โ๏ธ `Tuple` ์์ 3 `useState()`

> `useState()`: ์ฒซ ๋ฒ์งธ์ ๋ ๋ฒ์งธ์ ํ์์ด ๋ค๋ฅด๋ค. ๋ ๋ฒ์งธ๋ ํจ์ํ

```tsx
const [num, setNum] = useState(null);
```
