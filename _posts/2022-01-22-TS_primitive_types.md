---
title: "💫TS:: Typescript 기본 타입 알아보기!"
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

# [기본 타입](https://www.typescriptlang.org/docs/handbook/basic-types.html)

## 1️⃣ 기본타입: `number`, `string`, `boolean`, `undefined`, `null`

### ✔️ `number`

```tsx
let decimal: number = 6;
let hex: number = 0xf00d;
let binary: number = 0b1010;
let octal: number = 0o744;
let big: bigint = 100n;
```

<br />

### ✔️ `string`

```tsx
let color: string = "blue";
color = "red";

let name: string = `april`;
let age: number = 35;
let sentence: string = `Hello, my name is ${name}.
 
I'll be ${age + 1} years old next month.`;
```

<br />

### ✔️ `boolean`

```tsx
let isDone: boolean = false;
```

<br />

### ✔️ `undefined`

> `undefined`: 값이 있는지 없는지 정해지지 않은 상태, 텅텅 비었는지 아닌지 결정되지 않은 상태

```tsx
let name: undefined; // 💩이런식으로 할당하진 않음

let age: number | undefined; // number 또는 undefined을 할당할 수 있다
age = undefined;
age = 21;
```

<br />

### ✔️ `null`

> `null`: 텅텅 비었다

```tsx
let person: null; // 💩마찬가지로 이런식으로 할당하진 않음

let person2: string | null;
person2 = null;
person2 = "yurim";
```

<br />

---

## 2️⃣ 기본타입: `unknown`, `any`, `void`, `never`, `object`

### ✔️ 💩`unknown`

> `unknown` 어떤 타입인지 알 수 없다 // 💩

```tsx
let notSure: unknown = 0; // number를 할당 했음에도
notSure = "hi"; // string을 할당할 수 있다
notSure = true;
```

<br />

### ✔️ 💩`any`

> `any` 어떤 것이든 다 담을 수 있다 // 💩

```tsx
let anything: any = 0; // number를 할당 했음에도
anything = "hi"; // string을 할당할 수 있다
anything = true;
```

<br />

### ✔️ `void`

> `void` 함수의 리턴이 없을 때의 타입. 생략도 가능하다

```tsx
function print(): void {
  console.log("hello");
  return;
}
let unusable: void = undefined; // 💩 undefined 밖에 할당이 안되기 때문에 사용하지 않음
```

<br />

### ✔️ `never`

> `never` 에러가 발생하면 어플리케이션이 죽으니까 리턴값이 절대 없다. 그럴 때 never 타입을 지정.
> never 타입을 지정했는데 리턴이 있다면 에러 발생.

```tsx
// throwError 어플리케이션에서 예상치 못한 에러 발생가 발생할 경우 처리하는 함수
function throwError(message: string): never {
  // message -> server (log)
  throw new Error(message);
  while (true) {}
}
let neverEnding: never; // 💩

// objet
let obj: object; // 💩
function acceptSomeObject(obj: object) {}
acceptSomeObject({ name: "ellie" });
acceptSomeObject({ animal: "dog" });
```

<br />

### ✔️ `object`

> `object`: 자바스크립트의 객체 타입과 동일.
> 객체 속성에 대한 정보가 없기 때문에 타입 에러가 발생한다. 속성 정보를 포함해서 타입을 정의하기 위해서는 인터페이스([interface](https://velog.io/@april_5/%ED%95%A8%EC%88%98%EC%97%90%EC%84%9C-%ED%83%80%EC%9E%85-%EC%9D%B4%EC%9A%A9%ED%95%98%EA%B8%B0-JS-TS))를 사용해야 한다.

```tsx
interface Person {
  name: string;
  age?: number; // 물음표가 들어갔다는 것은, 설정을 해도 되고 안해도 되는 값이라는 것을 의미합니다.
}

const person: Person = {
  name: "april",
  age: 20,
};

// interface 를 extends 해서 상속받기
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
