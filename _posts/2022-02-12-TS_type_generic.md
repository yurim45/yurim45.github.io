---
title: "💫TS:: 드디어! <T>제네릭(Generics)💫"
tags:
  - [Typescript]
permalink: /study/TS/generic

navigation: true
toc: true
toc_sticky: true

date: 2022-02-12
last_modified_at: 2022-02-12
---

![](https://images.velog.io/images/april_5/post/3e7eaeea-e9c5-4886-8c4a-fad46fc21452/%E1%84%8C%E1%85%A6%E1%84%82%E1%85%A6%E1%84%85%E1%85%B5%E1%86%A8.png)

> 💡 <span style='color:royalblue'>**유연**</span>하고! <span style='color:royalblue'>**타입이 보장**</span>되고, <span style='color:royalblue'>**재사용성**</span>이 높은 <span style='color:fuchsia'>**제네릭(Generics)!!**</span>

## [제네릭](https://www.typescriptlang.org/ko/docs/handbook/2/generics.html)이란?

> 선언 시점이 아니라 <span style='color:royalblue'>**생성 시점에 타입을 명시**</span>하여 하나의 타입만이 아닌 <span style='color:fuchsia'>**다양한 타입을 사용할 수 있도록**</span> 하는 기법

- Generic이란 데이터의 타입을 일반화한다(generalize)한다는 의미
- <span style='color:royalblue'>**타입 정보가 동적으로 결정되는 타입**</span>
  - 같은 규칙을 여러 타입에 적용할 수 있기 때문에
  - 타입 코드를 작성할 때 발생할 수 있는 <span style='color:royalblue'>**중복 코드를 제거**</span>할 수 있다
- `C#`과 `Java` 같은 언어에서, **재사용성이 높은 컴포넌트를 만들 때 자주 활용**하는 제네릭(Generics)!!!
  - 즉, **단일 타입이 아닌 다양한 타입에서 작동**하는 컴포넌트를 작성할 수 있다.
- 제네릭을 통해 **여러 타입의 컴포넌트**나 **자신만의 타입**을 사용할 수 있다.

<br />

---

## [제네릭 기본 문법](https://joshua1988.github.io/ts/guide/generics.html#%EC%A0%9C%EB%84%A4%EB%A6%AD%EC%9D%98-%ED%95%9C-%EC%A4%84-%EC%A0%95%EC%9D%98%EC%99%80-%EC%98%88%EC%8B%9C)

### ✔️ 기본 코드

```ts
// text라는 파라미터에 값을 넘겨 받아 text를 반환하는 함수
const getText = (text) => {
  return text;
};

// 파라미터에 어떤 값을 넘겨주더라도 그대로 반환된다.
getText("april"); // 'april'
getText(20); // 10
getText(true); // true
```

<br />

### ✔️ 제네릭 코드

```ts
// 제네릭 기본 문법이 적용된 함수
const getText = <T>(text: T): T => {
  return text;
};

// 함수를 호출할 때, 함수 안에서 사용할 타입을 넘겨줄 수 있다
getText<string>("april"); // 'april'
getText<number>(20); // 10
getText<boolean>(true); // true
```

<br />

### ✔️ 두 개 이상의 제네릭 사용한 코드

```ts
// 두 개의 제네릭이 적용된 함수
const getUserInfo = <T, K>(name: T, age: K): [T, K] => {
  return [name, age];
};

// 함수를 호출할 때, 함수 안에서 사용할 타입을 넘겨줄 수 있다
getUserInfo("april", 20);
```

<br />

---

## 제네릭을 사용하는 이유? 🤔

파라미터의 타입이 여러 종류일 때 `any`를 사용하게 되는데,
`any` 타입은 타입 검사를 하지 않기 때문에 문제가 생길 수 있다

### 제네릭을 사용하지 않은 코드

```ts
const getText = (text: any): any => {
  return text;
};
```

<br />

### 제네릭 적용 코드

먼저 함수의 이름 바로 뒤에 `<T>` 라는 코드를 추가하고 함수의 인자와 반환 값에 모두 `T` 라는 타입을 추가하면,
함수를 호출할 때 넘긴 타입에 대해 타입스크립트가 추정할 수 있게 된다.

> 💡 따라서, 함수의 입력 값에 대한 타입과 출력 값에 대한 타입이 동일한지 검증할 수 있게 된다.

```ts
const getText = <T>(text: T): T => {
  return text;
};
```

<br />

---

## 제네릭 예제 코드

> 배열을 생성하는 함수로 익히는, 제네릭 예제 코드

### ✔️ 제네릭 사용 전

숫자 배열을 생성하는 함수와 문자 배열을 생성하는 함수 😳
중복된 코드가 많다... 😬😮‍💨

```ts
const makeNumberArray = (defaultValue: number, size: number): number[] => {
  const arr: number[] = [];
  for (let i = 0; i < size; i++) {
    arr.push(defaultValue);
  }
  return arr;
};

const makeStringArray = (defaultValue: string, size: number): string[] => {
  const arr: string[] = [];
  for (let i = 0; i < size; i++) {
    arr.push(defaultValue);
  }
  return arr;
};

const arr1 = makeNumberArray(1, 10);
const arr2 = makeStringArray("empty", 10);
```

<br />

### ✔️ 제네릭으로 코드 리펙토링 하기

```ts
const makeArray = <T>(defaultValue: T, size: number): T[] => {
  const arr: T[] = [];
  for (let i = 0; i < size; i++) {
    arr.push(defaultValue);
  }
  return arr;
};

const arr1 = makeArray<number>(1, 10);
const arr2 = makeArray<string>("empty", 5);

// makeArray 함수의 첫 번째 파라미터를 알면 타입 T도 알 수 있기 때문에,
// 호출 시 타입 T의 정보를 명시적으로 전달하지 않아도 된다.
const arr3 = makeArray(1, 10);
const arr4 = makeArray(1, 10);
```

<br />

---

## `extends` 키워드로 제네릭 타입 제한하기

<span style='color:royalblue'>**리액트**</span>와 같은 라이브러리의 API는 <span style='color:royalblue'>**입력 가능한 값의 범위를 제한**</span>한다.
예를 들어, <span style='color:royalblue'>**리액트의 속성값 전체는 객체 타입만 허용**</span>된다.
이를 위해 <u><span style='color:fuchsia'>타입스크립트의 제네릭은 **타입의 종류를 제한**할 수 있는 기능을 제공</span></u>한다.

<br />

### ✔️ 예제 코드

```ts
// 제네릭 T 타입을 number | string에 할당 가능한 타입으로 제한
const identity = <T extends number>(p1: T): T => {
  return p1;
};

identity(1);
identity("a");
identity([]); // 타입 에러
```

<br />

### ✔️ 예제 코드

```ts
// 제네릭 T 타입을 number | string에 할당 가능한 타입으로 제한
const identity = <T extends number>(p1: T): T => {
  return p1;
};

identity(1);
identity("a");
identity([]); // 타입 에러
```

<br />

### ✔️ 예제 코드2

```ts
interface IPerson {
  name: string;
  age: number;
}

interface IKorean extends IPerson {
  liveInSeoul: boolean;
}

// 제네릭 T는 IPerson에 할당 가능한 타입이어야 한다
// 제네릭 K는 IPerson의 속성 이름이어야 한다.
// 참고로 keyof는 인터페이스의 모든 속성 이름을 유니온 타입으로 만들어 준다.
const swapProperty = <T extends IPerson, K extends keyof IPerson>(
  p1: T,
  p2: T,
  name: K
): void => {
  const temp = p1[name];
  p1[name] = p2[name];
  p2[name] = temp;
};

const p1: IKorean = {
  name: "april",
  age: 20,
  liveInSeoul: true,
};

const p2: IKorean = {
  name: "yrkim",
  age: 20,
  liveInSeoul: true,
};

swapProperty(p1, p2, "age"); // p1, p2는 IPerson에 할당 가능하기 때문에 타입에러가 발생하지 않는다
```

<br />
