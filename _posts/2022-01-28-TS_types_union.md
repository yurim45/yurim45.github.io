---
title: "💫TS:: 🌈 진정한 타입스크립트의 시작! Union Type"
tags:
  - [Typescript]
permalink: /study/TS/types_union

navigation: true
toc: true
toc_sticky: true

date: 2022-01-28
last_modified_at: 2022-01-28
---

![](https://images.velog.io/images/april_5/post/fef3266f-5808-4e74-a394-3cc0c8bd35a3/typescript.png)

## 🌈 Union Types

받을 수 있는 인자를 정해준다?!

> `유니온 타입(Union Type)`이란? 자바스크립트의 OR 연산자(||)와 같이 'A' 이거나 'B'이다 라는 의미의 타입.

- OR의 너낌?? 🤔

<br />

### ✔️ Union Types 예제1

![](https://images.velog.io/images/april_5/post/ced52337-18e2-4cf8-a4d5-5c3dc14b9773/Union%20%E1%84%90%E1%85%A1%E1%84%8B%E1%85%B5%E1%86%B8.png)

> 인자를 선택할 때 위의 그림처럼 선택하게끔 알려줌.
> <span style='color:dodgerblue'>**받을 수 있는 인자를 정해준다.**</span>

- 리터럴 타입의 확장된 너낌?!🤔

```tsx
type Direction = "left" | "right" | "up" | "down";
function move(direction: Direction) {
  console.log(direction);
}
move("down");

type TileSize = 8 | 16 | 32;
const tile: TileSize = 16;
```

<br />

### ✔️ Union Types [예제2](https://www.typescriptlang.org/docs/handbook/2/everyday-types.html#union-types)

함수의 파라미터 `id`는 `number` 타입이나 `string` 타입이 모두 올 수 있다.

> 이처럼 `|` 연산자를 이용하여 <span style='color:dodgerblue'>**타입을 여러 개 연결**</span>하는 방식

```tsx
function printId(id: number | string) {
  if (typeof id === "string") {
    console.log(id.toUpperCase());
  } else {
    console.log(id);
  }
}
```

<br />

### ✔️ Union Types 예제3

```tsx
// function: login -> success or fail ⏱
type SuccessState = {
  response: {
    body: string;
  };
};
type FailState = {
  reason: string;
};
type LoginState = SuccessState | FailState;

function login(id: string, password: string): LoginState {
  return {
    response: {
      body: "logged in!",
    },
  };
}
```

<br />

---

## Intersection Types: & ✨

> Union type과 반대되는 타입?

- `Intersection type`이란?
  - 인터섹션 타입(Intersection Type)은 <span style='color:dodgerblue'>**여러 타입을 모두 만족하는 하나의 타입**</span>을 의미
  - 다양한 타입 들을 한 번에 묶어서 선언할 수 있다.
  - 단, 선언된 여러 타입 들을 모두 사용해야만 에러발생 하지 않는다 😅

<br />

### ✔️ Intersection Types 예제

> `&` 연산자를 이용해 여러 개의 타입 정의를 하나로 합치는 방식

```tsx
type Student = {
  name: string;
  score: number;
};

type Worker = {
  empolyeeId: number;
  work: () => void;
};

function internWork(person: Student & Worker) {
  console.log(person.name, person.empolyeeId, person.work());
}

internWork({
  name: "april",
  score: 1,
  empolyeeId: 123,
  work: () => {},
});
```

<br />
