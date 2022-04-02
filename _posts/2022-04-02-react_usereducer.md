---
published: true
title: "🚀React Hooks:: useReducer_ 컴포넌트의 상태값을 리덕스처럼 관리하기"
tags:
  - [React]
permalink: /study/react/usereducer

navigation: true
toc: true
toc_sticky: true

date: 2022-04-02
last_modified_at: 2022-04-02
---

![](https://media.vlpt.us/images/april_5/post/8a53b9e6-d323-4bc2-9886-78f6fe797e78/image.png)

컴포넌트의 상태값을 리덕스처럼 관리하기: `useReducer`

<br />

## `useReducer` 란?

`useReducer`를 사용하면 컴포넌트의 상태값을 리덕스의 리듀서처럼 관리할 수 있다.

<br />

## `useReducer` 사용 예시

```jsx
import React, { useReducer } from "react";

const INITIAL_STATE = { name: "yr", age: 0 }; // (1)

const reducer = (state, action) => {
  switch (
    action.type // (2)
  ) {
    case "setName":
      return { ...state, name: action.name };
    case "setAge":
      return { ...state, age: action.age };
    default:
      return state;
  }
};

const Profile = () => {
  // (3)
  const [state, dispatch] = useReducer(reducer, INITIAL_STATE);

  return (
    <div>
      <p>{`name is ${state.name}`}</p>
      <p>{`age is ${state.age}`}</p>
      <input
        type='text'
        value={state.name}
        onChange={(
          e // (4)
        ) => dispatch({ type: "setName", name: e.currentTarger.value })}
      />
      <input
        type='text'
        value={state.age}
        onChange={(
          e // (4)
        ) => dispatch({ type: "setAge", age: e.currentTarger.value })}
      />
    </div>
  );
};
```

<br />

### (1) 초기값 선언

- 초기값 선언

<br />

### (2) 리듀서 함수 작성

- state, action 의 값을 받아서
- action.type 에 따라 처리해야 할 로직을 구현
  - 로직 구현 시 state 값이 어떻게 변경되어야 하는지 작성

<br />

### (3) useReducer 선언

- `useReducer` 를 선언할 때엔 매개변수로 두 개의 인자를 받는데,
- (2)에서 작성한 **리듀서 함수**와 (1)의 **초기 상태값**을 입력

<br />

### (4) 상태값을 변경하는 dispatch 함수 사용

- state 값을 변경할 때엔 리덕스의 `dispatch` 함수와 같은 방식으로 사용하여 처리

<br />
<br />

---

## 트리의 깊은 곳으로 이벤트 처리 함수 전달하기

보통 상위 컴포넌트에서 다수의 상태값을 관리한다.
이때 <u>**자식 컴포넌트로부터 발생한 이벤트에서 상위 컴포넌트의 상태값을 변경해야 하는 경우**</u>가 많은데, 이를 위해 상위 컴포넌트에서 트리의 깊은 곳까지 이벤트 처리 함수를 전달한다.
이 작업은 번거롭고, 코드의 가독성이 떨어진다.... 🥲🥲

### ✔️ useReducer 와 Context API 사용하여 구현

> useReducer 와 Context API 사용하면 쉽게 구현할 수 있다

- `useReducer`: 상태값 관리
- `Context API`: `Provider`로 전달

```jsx
// ...
export const ProfileDispatch = React.createContext(null); // (1)
// ...

const Profile = () => {
  const [state, dispatch] = useReducer(reducer, INITIAL_STATE);

  return (
    <div>
      // ...
      <ProfileDispatch.Provider value={dispatch}>
        {" "}
        // (2)
        <SomeComponent />
      </ProfileDispatch.Provider>
    </div>
  );
};
```

<br />

### (1) `Context 객체` 생성

- `dispatch` 를 전달하는 `Context 객체` 생성

<br />

### (2) `Provider` 를 통해 전달

- `Provider` 를 통해 `dispatch` 를 전달

<br />
<br />
