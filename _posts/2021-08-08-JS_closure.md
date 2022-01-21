---
title: "🐯CoreJS:: 클로저"
tags:
  - [Javascript]
permalink: /study/JS/closure

navigation: true
toc: true
toc_sticky: true

date: 2021-08-08
last_modified_at: 2021-08-08
---

![](https://images.velog.io/images/april_5/post/6367da33-0b15-4bb2-814d-4cebfec6c8fe/%E1%84%8F%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A9%E1%84%8C%E1%85%A5.png)

`주니어 개발자의 개인 공부 과정을 기록합니다.`

클로저(Closure)는 (자바스크립트 고유 개념이 아닌) 함수형 프로그래밍 언어에서 등장하는 특성 중 하나이다.

하지만 클로저는 객체지향과 함수형 모두를 아우르는 매우 중요한 개념이고,

자바스크립트를 이용한 고난이도의 테크닉을 구사하는데 필수적인 개념으로 활용된다.

---

# 클로저(Closure)란?

클로저(closure)는 <span style="color:dodgerblue">**내부함수가 외부함수의 맥락(context)에 접근할 수 있는 것**</span>을 가르킨다.

> 즉, 클로저는 **외부함수의 컨텍스트에 접근할 수 있는 내부함수**를 뜻한다.

### :: 내부함수

<span style="color:dodgerblue">**함수 안에 선언된 또 다른 함수**</span>. 즉 아래 코드의 `inner()`를 가리킨다.

```jsx
const outer = () => {
  let a = 1;
  const inner = () => {
    return ++a;
  };
  return inner;
};

const outer2 = outer();
console.log(outer2()); // 2
console.log(outer2()); // 3
```

함수의 실행 컨텍스트가 종료된 후에도 `LexicalEnvironment`가 **가비지 컬렉터의 수집 대상에서 제외되는 경우**는,
지역변수를 참조하는 내부함수가 외부로 전달된 경우가 유일하다.

가비지 컬렉터는 어떤 값을 참조하는 변수가 하나라도 있다면
그 값은 수집 대상에서 제외시킨다.

이런 현상으로 다시 클로저를 정의하면,

> **클로저**란? 어떤 함수 A에서 선언한 변수 a를 참조하는 내부함수 B를 외부로 전달할 경우, A의 실행 컨텍스트가 종료된 이후에도 변수 a가 사라지지 않는 현상을 말한다

내부함수를 외부로 전달하는 방법에는 함수를 `return`하는 경우뿐 아니라, 콜백으로 전달하는 경우도 포함된다.

<br />

---

## 클로저와 메모리 관리

클로저는 그 본질이 메모리를 계속 차지하는 개념이므로 <span style="color:dodgerblue">**더 이상 사용하지 않게 된 클로저는 메모리를 차지하지 않도록 관리**</span>해주어야 한다.

관리 방법은 참조 카운트를 0으로 만들면 가비지 컬렉터가 수거할 텐데, 참조 카운트를 0으로 만드는 방법은

**식별자에** 참조형이 아닌 **기본형 데이터(보통 `null` 또는 `undefined`)를 할당**하면 된다.

```jsx
const outer = () => {
  let a = 1;
  const inner = () => {
    return ++a;
    inner = null; // inner 식별자의 함수 참조를 끊음
  };
  return inner;
};

console.log(outer());
console.log(outer());
outer = null; // outer 식별자의 inner 함수 참조를 끊음
```

---

### ✨ tl;dr

- 클로저란 어떤 함수에서 선언한 변수를 참조하는 내부함수를 외부로 전달할 경우, 함수의 실행 컨텍스트가 종료된 후에도 해당 변수가 사라지지 않는 현상이다.

- 내부함수를 외부로 전달하는 방법에는 함수를 `return`하는 경우뿐 아니라, 콜백으로 전달하는 경우도 포함된다.

- 클로저는 그 본질이 메모리를 계속 차지하는 개념이므로 더 이상 사용하지 않게 된 클로저는 메모리를 차지하지 않도록 관리해야 한다.
