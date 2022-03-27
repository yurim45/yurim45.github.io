---
published: true
title: "🚀React Hooks:: useCallback()과 useMemo(), React.memo"
tags:
  - [React]
permalink: /study/react/hooks

navigation: true
toc: true
toc_sticky: true

date: 2022-03-26
last_modified_at: 2022-03-26
---

![](https://images.velog.io/images/april_5/post/6ed47d67-0a2b-4fa3-8f65-e952e9ff7a7d/image.png)

<br />

`useMemo()`와 `useCallback()` 정리하기

> **특정 결과값**을 재사용할 때 사용하는 `useMemo()`, <br />**특정 함수**를 새로 만들지 않고 재사용하고 싶을 때`useCallback()`

<br /><br />

## ✔️ 특정 함수 재사용 `useCallback()`

- 한번 만든 <span style="background-color:yellow">**함수를 필요할 때만**</span> 새로 만들고 재사용하는 것
- 컴포넌트에서 `props`가 바뀌지 않으면 `Virtual DOM`에 새로 렌더링하는 것 조차 하지 않고 컴포넌트의 결과물을 재사용 하는 최적화 작업을 할건데, 이럴 경우 함수를 재사용하는 것은 필수

- 주의할 점은, 함수 안에서 사용하는 `state` 혹은 `props` 가 있다면 꼭, `deps` 배열안에 포함시켜야 된다는 것
  - 그렇지 않다면, 함수 내에서 해당 값들을 참조할 때 가장 최신의 값을 참조할 것이라고 보장할 수 없다;;
  - `props`로 받아온 함수가 있다면, 이 함수도 deps` 배열에 추가해야 함!

<br />

### :: 코드 예시

- a와 b의 값이 변할 때에만 `doSomething` 함수를 재사용하기

```jsx
// 적용후
const memoizedCallback = useCallback(() => {
  doSomething(a, b);
}, [a, b]);
```

<br /><br />

---

## ✔️ 특정 결과값 재사용 `useMemo()`

- <span style="background-color:yellow">**성능 최적화**</span>를 위하여 연산된 값을 useMemo라는 Hook을 사용하여 재사용할 때 사용
- useMemo는 의존성이 변경되었을 때에만 [메모이제이션](https://ko.wikipedia.org/wiki/%EB%A9%94%EB%AA%A8%EC%9D%B4%EC%A0%9C%EC%9D%B4%EC%85%98)된 값만 다시 계산한다
- useMemo로 전달된 함수는 렌더링 중에 실행!!!!
- 의존성 배열이 없을 경우 렌더링 할 때 마다 새로운 값을 계산하니 주의!

> **메모이제이션(memorization)**: 이전에 계산 한 값을 재사용한다는 의미를 가진다

<br />

### :: 코드 예시

- a와 b의 값이 변할 때만 `computeExpensiveValue` 함수를 실행한 결과를 `memoizedValue` 담기!

```jsx
// 적용후
const memoizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);
```

<br /><br />

---

## ✔️ React.memo를 사용한 컴포넌트 리렌더링 방지

- 컴포넌트의 props 가 바뀌지 않았다면,
- 리렌더링을 방지하여 컴포넌트의 리렌더링 성능 최적화를 해줄 수 있는 `React.memo` 함수
- 컴포넌트에서 리렌더링이 필요한 상황에서만 리렌더링을 하도록 설정할 수 있다

<br />

### :: 코드 예시

- a와 b의 값이 변할 때만 `computeExpensiveValue` 함수를 실행한 결과를 `memoizedValue` 담기!

```jsx
// 적용후
import React from 'react';

const User = (props) => {
  return (
   ///
  );
};

export default React.memo(User);
```

<br /><br />
