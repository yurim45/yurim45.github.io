---
title: "π«TS:: νμμ€ν¬λ¦½νΈμ κ½ π· Type Alias"
tags:
  - [Typescript]
permalink: /study/TS/types_aliases

navigation: true
toc: true
toc_sticky: true

date: 2022-01-27
last_modified_at: 2022-01-27
---

![](https://images.velog.io/images/april_5/post/fef3266f-5808-4e74-a394-3cc0c8bd35a3/typescript.png)

## | νμ μ€ν¬λ¦½νΈ νμ λ³μΉ­

λκ°μ νμμ ν λ² μ΄μ <span style='color:dodgerblue'>**μ¬μ¬μ©**</span>νκ±°λ, λ λ€λ₯Έ μ΄λ¦μΌλ‘ λΆλ₯΄κ³  μΆμ κ²½μ°μ μ¬μ©!

> `Type Aliases`: type ν€μλλ₯Ό μ¬μ©ν΄μ μλ‘μ΄ νμμ μ μν  μ μλ€

### βοΈ `Type Alias` μμ 1

```tsx
type Text = string;
const name: Text = "april"; // const name: string = 'april';
const address: Text = "korea";

type Num = number;
const age: Num = 30; // const age: number = 30;

type Student = {
  name: string;
  age: number;
};
const student: Student = {
  name: "april",
  age: 26,
};
```

<br />

### βοΈ `Type Alias` [μμ 2](https://www.typescriptlang.org/docs/handbook/2/everyday-types.html#type-aliases)

```tsx
type Point = {
  x: number;
  y: number;
};

function printCoord(pt: Point) {
  console.log("The coordinate's x value is " + pt.x);
  console.log("The coordinate's y value is " + pt.y);
}

printCoord({ x: 100, y: 100 });
```

<br />

---

## | Literal Types

### βοΈ Literal Types μμ 1

```tsx
type Name = "name";
let aprilName: Name;
aprilName = "name";
```

<br />

### βοΈ Literal Types [μμ 2](https://www.typescriptlang.org/docs/handbook/2/everyday-types.html#literal-types)

```tsx
function printText(s: string, alignment: "left" | "right" | "center") {
  // ...
}
printText("Hello world", "left");
printText("G'day mate", "centre"); // μ΄λ΄ κ²½μ° μλ¬λ¨.
// λλ²μ§Έ μΈμμλ μΈκ°μ§μ λ¬Έμμ΄ μ€ νλλ§ μλ ₯ν  μ μκΈ° λλ¬Έμ!!
```

<br />
