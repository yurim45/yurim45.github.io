---
title: "💫TS:: 타입스크립트의 꽃 🌷 Type Alias"
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

## | 타입 스크립트 타입 별칭

똑같은 타입을 한 번 이상 <span style='color:dodgerblue'>**재사용**</span>하거나, 또 다른 이름으로 부르고 싶은 경우에 사용!

> `Type Aliases`: type 키워드를 사용해서 새로운 타입을 정의할 수 있다

### ✔️ `Type Alias` 예제1

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

### ✔️ `Type Alias` [예제2](https://www.typescriptlang.org/docs/handbook/2/everyday-types.html#type-aliases)

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

### ✔️ Literal Types 예제1

```tsx
type Name = "name";
let aprilName: Name;
aprilName = "name";
```

<br />

### ✔️ Literal Types [예제2](https://www.typescriptlang.org/docs/handbook/2/everyday-types.html#literal-types)

```tsx
function printText(s: string, alignment: "left" | "right" | "center") {
  // ...
}
printText("Hello world", "left");
printText("G'day mate", "centre"); // 이럴 경우 에러남.
// 두번째 인자에는 세가지의 문자열 중 하나만 입력할 수 있기 때문에!!
```

<br />
