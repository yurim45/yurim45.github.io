---
title: "💫TS:: 함수에서 타입 이용하기 (JS 💩 → TS ✨)"
tags:
  - [Typescript]
permalink: /study/TS/types_func

navigation: true
toc: true
toc_sticky: true

date: 2022-01-24
last_modified_at: 2022-01-24
---

![](https://images.velog.io/images/april_5/post/fef3266f-5808-4e74-a394-3cc0c8bd35a3/typescript.png)

## [함수](https://www.typescriptlang.org/docs/handbook/2/everyday-types.html#functions)에서 타입 이용하기: 기본

### ✔️ 예제1

```tsx
// JavaScript 💩
function jsAdd(num1, num2) {
  return num1 + num2;
}

// TypeScript ✨
function add(num1: number, num2: number): number {
  return num1 + num2;
}
```

<br />

### ✔️ 예제2

```tsx
// JavaScript 💩
function jsFetchNum(id) {
  // code ...
  // code ...
  // code ...
  return new Promise((resolve, reject) => {
    resolve(100);
  });
}

// TypeScript ✨
function fetchNum(id: string): Promise<number> {
  // code ...
  // code ...
  // code ...
  return new Promise((resolve, reject) => {
    resolve(100);
  });
}
```

<br />

---

## 함수 parameter 타입: `spread`, `default`, `optional`

### ✔️ `optional parameter`

```tsx
// Optional parameter
function printName(firstName: string, lastName?: string) {
  console.log(firstName);
  console.log(lastName); // undefined
}
printName("Steve", "Jobs");
printName("april");
printName("ving9");
```

<br />

### ✔️ `Default parameter`

```tsx
// Default parameter
function printMessage(message: string = "default message") {
  console.log(message);
}
printMessage();
```

<br />

### ✔️ `Rest parameter`

```tsx
// Rest parameter
//                 인자를 숫자 타입의 배열로 받아온다 number[]
function addNumbers(...numbers: number[]): number {
  return numbers.reduce((a, b) => a + b);
}
console.log(addNumbers(1, 2));
console.log(addNumbers(1, 2, 3, 4));
console.log(addNumbers(1, 2, 3, 4, 5, 0));
```

<br />
<br />

---

## [interface](https://www.typescriptlang.org/docs/handbook/2/everyday-types.html#interfaces) 사용해보기

> `interface`는 <span style='color:dodgerblue'>**클래스 또는 객체를 위한 타입을 지정**</span> 할 때 사용되는 문법

### ✔️ 일반 객체를 interface 로 타입 설정하기

[벨로퍼트 참고 자료](https://velog.io/@velopert/typescript-basics)
