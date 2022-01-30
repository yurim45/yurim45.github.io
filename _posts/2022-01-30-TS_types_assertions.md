---
title: "💫TS:: 건방진 녀석 Type Assertion!"
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

TypeScript의 타입 표명은 프로그래머가 컴파일러에게
<i>"내가 너보다 타입에 더 잘 알고 있고, 나의 주장에 대해 의심하지 마라"</i>
고 하는 것과 같다

> `Type Assertion`: 타입을 강요해야 하는 경우에 사용?? 단, 지양하는 것이 좋다. 💩

<br />

### ✔️ Type Assertion 예제1

```tsx
function jsStrFunc(): any {
  return "hello";
}
const result = jsStrFunc();
console.log((result as string).length); // (1)
console.log((<string>result).length);
```

(1) `result as string`: result는 string이야!! string임을 확인하기 때문에 string method를 사용할 수 있다

![](https://images.velog.io/images/april_5/post/93dca28a-a421-4aaf-9d72-604346b2c066/image.png)

<br />

### ✔️ Type Assertion를 지양해야 하는이유! 예제2

```tsx
function jsStrFunc(): any {
  return 2; // (2) 😱아래에서 문자열임에도 숫자를 지정할 경우에도 에러는 발생하지 않는다;;
}
const result = jsStrFunc();
console.log((result as string).length); // (3)
console.log((<string>result).length); // 위의 as와 같은 문법
```

(3) 😱😱 `as`를 붙혀 타입을 장담했기 때문에 컴파일 에러는 발생하지 않는다;; 다만 실행할 경우 `undefined`가 출력된다.

<br />

### ✔️ Type Assertion 예제3: Type Assertion을 지양해야 하는 이유!! 😱

```tsx
const wrong: any = 5;
console.log((wrong as Array<number>).push(1)); // 😱
```

![](https://images.velog.io/images/april_5/post/4e447eb5-babc-4ffe-9433-5a5bf9601387/image.png)

> 애플리케이션이 죽어버렸어!!! 😱😱😱😱😱😱

<br />

### ✔️ Type Assertion 예제4: `!`를 붙히면 확신해

```tsx
function findNumbers(): number[] | undefined {
  return undefined;
}
const numbers = findNumbers()!;
numbers.push(2); // 😱 numbers는 number[]일수도 있고,
// undefined 일수도 있기 때문에
// push()를 사용할 경우 에러 발생.
```

> 📌 <span style="color:tomato">**`!`를 붙히면 확신해**</span>를 표현.
> 즉, numbers는 배열임을 확신하므로 push를 사용할 수 있어!
> 참고로 `as`는 <span style="color:tomato">**장담해!**</span>를 표현.

<br />

### ✔️ Type Assertion [예제5](https://www.typescriptlang.org/docs/handbook/2/everyday-types.html#type-assertions)

```tsx
const myCanvas = document.getElementById("main_canvas") as HTMLCanvasElement;

const button = document.querySelector("class")!;
```

<br />
