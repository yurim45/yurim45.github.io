---
published: true
title: "πReact Hooks:: useReducer_ μ»΄ν¬λνΈμ μνκ°μ λ¦¬λμ€μ²λΌ κ΄λ¦¬νκΈ°"
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

μ»΄ν¬λνΈμ μνκ°μ λ¦¬λμ€μ²λΌ κ΄λ¦¬νκΈ°: `useReducer`

<br />

## `useReducer` λ?

`useReducer`λ₯Ό μ¬μ©νλ©΄ μ»΄ν¬λνΈμ μνκ°μ λ¦¬λμ€μ λ¦¬λμμ²λΌ κ΄λ¦¬ν  μ μλ€.

<br />

## `useReducer` μ¬μ© μμ

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

### (1) μ΄κΈ°κ° μ μΈ

- μ΄κΈ°κ° μ μΈ

<br />

### (2) λ¦¬λμ ν¨μ μμ±

- state, action μ κ°μ λ°μμ
- action.type μ λ°λΌ μ²λ¦¬ν΄μΌ ν  λ‘μ§μ κ΅¬ν
  - λ‘μ§ κ΅¬ν μ state κ°μ΄ μ΄λ»κ² λ³κ²½λμ΄μΌ νλμ§ μμ±

<br />

### (3) useReducer μ μΈ

- `useReducer` λ₯Ό μ μΈν  λμ λ§€κ°λ³μλ‘ λ κ°μ μΈμλ₯Ό λ°λλ°,
- (2)μμ μμ±ν **λ¦¬λμ ν¨μ**μ (1)μ **μ΄κΈ° μνκ°**μ μλ ₯

<br />

### (4) μνκ°μ λ³κ²½νλ dispatch ν¨μ μ¬μ©

- state κ°μ λ³κ²½ν  λμ λ¦¬λμ€μ `dispatch` ν¨μμ κ°μ λ°©μμΌλ‘ μ¬μ©νμ¬ μ²λ¦¬

<br />
<br />

---

## νΈλ¦¬μ κΉμ κ³³μΌλ‘ μ΄λ²€νΈ μ²λ¦¬ ν¨μ μ λ¬νκΈ°

λ³΄ν΅ μμ μ»΄ν¬λνΈμμ λ€μμ μνκ°μ κ΄λ¦¬νλ€.
μ΄λ <u>**μμ μ»΄ν¬λνΈλ‘λΆν° λ°μν μ΄λ²€νΈμμ μμ μ»΄ν¬λνΈμ μνκ°μ λ³κ²½ν΄μΌ νλ κ²½μ°**</u>κ° λ§μλ°, μ΄λ₯Ό μν΄ μμ μ»΄ν¬λνΈμμ νΈλ¦¬μ κΉμ κ³³κΉμ§ μ΄λ²€νΈ μ²λ¦¬ ν¨μλ₯Ό μ λ¬νλ€.
μ΄ μμμ λ²κ±°λ‘­κ³ , μ½λμ κ°λμ±μ΄ λ¨μ΄μ§λ€.... π₯²π₯²

### βοΈ useReducer μ Context API μ¬μ©νμ¬ κ΅¬ν

> useReducer μ Context API μ¬μ©νλ©΄ μ½κ² κ΅¬νν  μ μλ€

- `useReducer`: μνκ° κ΄λ¦¬
- `Context API`: `Provider`λ‘ μ λ¬

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

### (1) `Context κ°μ²΄` μμ±

- `dispatch` λ₯Ό μ λ¬νλ `Context κ°μ²΄` μμ±

<br />

### (2) `Provider` λ₯Ό ν΅ν΄ μ λ¬

- `Provider` λ₯Ό ν΅ν΄ `dispatch` λ₯Ό μ λ¬

<br />
<br />
