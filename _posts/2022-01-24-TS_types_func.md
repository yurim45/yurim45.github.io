---
title: "π«TS:: ν¨μμμ νμ μ΄μ©νκΈ° (JS π© β TS β¨)"
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

## [ν¨μ](https://www.typescriptlang.org/docs/handbook/2/everyday-types.html#functions)μμ νμ μ΄μ©νκΈ°: κΈ°λ³Έ

### βοΈ μμ 1

```tsx
// JavaScript π©
function jsAdd(num1, num2) {
  return num1 + num2;
}

// TypeScript β¨
function add(num1: number, num2: number): number {
  return num1 + num2;
}
```

<br />

### βοΈ μμ 2

```tsx
// JavaScript π©
function jsFetchNum(id) {
  // code ...
  // code ...
  // code ...
  return new Promise((resolve, reject) => {
    resolve(100);
  });
}

// TypeScript β¨
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

## ν¨μ parameter νμ: `spread`, `default`, `optional`

### βοΈ `optional parameter`

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

### βοΈ `Default parameter`

```tsx
// Default parameter
function printMessage(message: string = "default message") {
  console.log(message);
}
printMessage();
```

<br />

### βοΈ `Rest parameter`

```tsx
// Rest parameter
//                 μΈμλ₯Ό μ«μ νμμ λ°°μ΄λ‘ λ°μμ¨λ€ number[]
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

## [interface](https://www.typescriptlang.org/docs/handbook/2/everyday-types.html#interfaces) μ¬μ©ν΄λ³΄κΈ°

> `interface`λ <span style='color:dodgerblue'>**ν΄λμ€ λλ κ°μ²΄λ₯Ό μν νμμ μ§μ **</span> ν  λ μ¬μ©λλ λ¬Έλ²

### βοΈ μΌλ° κ°μ²΄λ₯Ό interface λ‘ νμ μ€μ νκΈ°

[λ²¨λ‘νΌνΈ μ°Έκ³  μλ£](https://velog.io/@velopert/typescript-basics)
