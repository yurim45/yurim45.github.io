---
title: "💫TS:: enum은 무엇이고 좋은건가? 🤔"
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

## enum은 무엇인고?🤔

> 💡 `enum`: 여러 관련된 상수 값들을 한 곳에 모아서 정리할 수 있도록 하는 타입

JavaScript에서는 enum type이 존재하지 않으므로,
TypeScript에서 저체적으로 제공하는 타입 중 하나.

<br />

### ✔️ enum 예제1

> JavaScript에서, 보통 상수(변하지 않는 수, constant)를 선언할 때에는 변수명을 대문자로 선언하지만,
> TypeScript에서 `enum` 선언할 때에는 첫 글자만 대문자로 선언한다.

```tsx
// JavaScript
const MAX_NUM = 6;
const MAX_STUDENTS_PER_CLASS = 10;

const MONDAY = 0;
const TUESDAY = 1;
const WEDNESDAY = 2;
// JavaScript에서는 관련된 데이터를 묶을 수 있는 타입이 별도 존재하지 않으므로, 아래처럼 Object로 구현.
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

타입스크립트에서 `enum`을 사용하면

- 선택한 값이 숫자 0부터 증가하면서 값을 가지게 되고
  - 예시) `console.log(Days.Monday);`는 0이 출력됨

<br />

- 0이 아닌 1부터 시작하고 싶다면 지정하면 된다
  ![](https://images.velog.io/images/april_5/post/c8a2c93d-24d7-47a0-bda4-7d8d8b1d28ba/image.png)
  - 예시) `console.log(Days.Monday);`는 1이 출력됨

<br />

- 숫자가 아닌 문자열도 지정이 가능하다.
  ![](https://images.velog.io/images/april_5/post/95335c1e-e079-4ae6-82bf-54a862759c13/image.png)
  - 예시) `console.log(Days.Monday);`는 monday이가 출력됨

<br />

### 😱 타입스크립트에서 enum을 사용하지 않는 이유!!!!!!

```tsx
enum Days {
  Monday,
  Tuesday,
  Wednesday,
}

let day: Days = Days.Monday;

day = 10; // enum type이 지정된 변수에 다른 숫자를 할당해도 에러가 나지 않는다 😱
```

---

### ✨ tl;dr

📌 타입스크립트에서 `enum` 타입은 사용하지 않는다. 이유는,

- enum으로 타입이 지정된 변수에 다른 숫자를 할당할 수 있기 때문에 연관되지 않는 숫자도 할당할 수 있다.

따라서 <span style="color:dodgerblue">**타입스크립트에서는 enum 대신 union 타입을 사용**</span>한다.
