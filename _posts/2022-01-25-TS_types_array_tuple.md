---
title: "💫TS:: ✨ 배열과 튜플, 언제 튜플을 사용해야 할까?"
tags:
  - [Typescript]
permalink: /study/TS/types_array_tuple

navigation: true
toc: true
toc_sticky: true

date: 2022-01-25
last_modified_at: 2022-01-25
---

![](https://images.velog.io/images/april_5/post/fef3266f-5808-4e74-a394-3cc0c8bd35a3/typescript.png)

# ✨`Array`와 `Tuple`

## 🔷 `Array`

<br />

### ✔️ `Array` 예제1

```tsx
let list: number[] = [1, 2, 3];
let list: Array<number> = [1, 2, 3];
```

<br />

### ✔️ `Array` 예제2

```tsx
// Array
const fruits: string[] = ["🍅", "🍌"];
const scroes: Array<number> = [1, 3, 4]; // number[] = [1, 2, 3];

function printArray(fruits: readonly string[]) {
  // readonly 라는 키워드는 말 그대로 읽기 전용
  // object의 불변성을 지키는 것은 매우 중요하므로, readonly가 많이 사용 됨
}
```

<br />

---

## 🔷 `Tuple`

> `Tuple`은 배열은 배열인데 서로 다른 타입을 가질 수 있는 배열

<br />

### ✔️ `Tuple` 예제1

```tsx
// Declare a tuple type
let x: [string, number];

// Initialize it
x = ["hello", 10]; // OK

// Initialize it incorrectly
x = [10, "hello"]; // 💩Error
```

<br />

### ✔️ `Tuple` 예제2

> `Tuple`을 사용하는 곳이라면 `interface`, `type alias`, `class` 등으로 대체해서 사용하는 것을 추천!

- Tuple에 접근할 때엔, index로 접근이 가능한데 이러면 어떤 데이터가 들어있는지 바로 확인이 어려우므로 <span style='color:tomato'>**가독성 ⬇️**</span>
  ➡️ 이런 경우 <span style='color:dodgerblue'>**구조 분해 할당**</span>를 활용하자!

```tsx
let student: [string, number];
student = ["name", 123];
student[0]; // name
student[1]; // 123
const [name, age] = student; // 구조 분해 할당 Destructuring
```

<br />

### ✔️ `Tuple` 예제3 `useState()`

> `useState()`: 첫 번째와 두 번째의 타입이 다르다. 두 번째는 함수형

```tsx
const [num, setNum] = useState(null);
```
