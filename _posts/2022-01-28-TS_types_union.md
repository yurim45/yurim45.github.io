---
title: "π«TS:: π μ§μ ν νμμ€ν¬λ¦½νΈμ μμ! Union Type"
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

## π Union Types

λ°μ μ μλ μΈμλ₯Ό μ ν΄μ€λ€?!

> `μ λμ¨ νμ(Union Type)`μ΄λ? μλ°μ€ν¬λ¦½νΈμ OR μ°μ°μ(||)μ κ°μ΄ 'A' μ΄κ±°λ 'B'μ΄λ€ λΌλ μλ―Έμ νμ.

- ORμ λλ?? π€

<br />

### βοΈ Union Types μμ 1

![](https://images.velog.io/images/april_5/post/ced52337-18e2-4cf8-a4d5-5c3dc14b9773/Union%20%E1%84%90%E1%85%A1%E1%84%8B%E1%85%B5%E1%86%B8.png)

> μΈμλ₯Ό μ νν  λ μμ κ·Έλ¦Όμ²λΌ μ ννκ²λ μλ €μ€.
> <span style='color:dodgerblue'>**λ°μ μ μλ μΈμλ₯Ό μ ν΄μ€λ€.**</span>

- λ¦¬ν°λ΄ νμμ νμ₯λ λλ?!π€

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

### βοΈ Union Types [μμ 2](https://www.typescriptlang.org/docs/handbook/2/everyday-types.html#union-types)

ν¨μμ νλΌλ―Έν° `id`λ `number` νμμ΄λ `string` νμμ΄ λͺ¨λ μ¬ μ μλ€.

> μ΄μ²λΌ `|` μ°μ°μλ₯Ό μ΄μ©νμ¬ <span style='color:dodgerblue'>**νμμ μ¬λ¬ κ° μ°κ²°**</span>νλ λ°©μ

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

### βοΈ Union Types μμ 3

```tsx
// function: login -> success or fail β±
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

## Intersection Types: & β¨

> Union typeκ³Ό λ°λλλ νμ?

- `Intersection type`μ΄λ?
  - μΈν°μΉμ νμ(Intersection Type)μ <span style='color:dodgerblue'>**μ¬λ¬ νμμ λͺ¨λ λ§μ‘±νλ νλμ νμ**</span>μ μλ―Έ
  - λ€μν νμ λ€μ ν λ²μ λ¬Άμ΄μ μ μΈν  μ μλ€.
  - λ¨, μ μΈλ μ¬λ¬ νμ λ€μ λͺ¨λ μ¬μ©ν΄μΌλ§ μλ¬λ°μ νμ§ μλλ€ π

<br />

### βοΈ Intersection Types μμ 

> `&` μ°μ°μλ₯Ό μ΄μ©ν΄ μ¬λ¬ κ°μ νμ μ μλ₯Ό νλλ‘ ν©μΉλ λ°©μ

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
