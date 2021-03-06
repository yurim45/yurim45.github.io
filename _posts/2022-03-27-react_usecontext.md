---
published: true
title: "πReact Hooks:: useContext()λ‘ μν κ΄λ¦¬νκΈ°"
tags:
  - [React]
permalink: /study/react/usecontext

navigation: true
toc: true
toc_sticky: true

date: 2022-03-27
last_modified_at: 2022-03-27
---

![](https://images.velog.io/images/april_5/post/f602092b-93e9-466e-a3a8-ba5ebdd692b1/image.png)

`Consumer` μ»΄ν¬λνΈ μμ΄ `Context` μ¬μ©νκΈ°

# Context API

- μμ μ»΄ν¬λνΈμμ νμ μ»΄ν¬λνΈλ‘ λ°μ΄ν°λ₯Ό μ λ¬ν  λ propsκ° μ¬μ©λλλ°, κ°κΉμ΄ κ±°λ¦¬μ μλ λͺ κ°μ νμ μ»΄ν¬λνΈλ‘ μ λ¬ν  λλ propsλ‘λ μΆ©λΆνμ§λ§,
- λ§μ μμ νμ μ»΄ν¬λνΈλ‘ μ λ¬ν  λλ κΈ°κ³μ μΌλ‘ propsλ₯Ό μ λ¬ν΄μΌ νλ μ½λλ₯Ό μμ±ν΄μΌ νλ μν©μ΄ λ°μνλ€.

> μ΄λ΄ λ `Context API` λ₯Ό μ¬μ©νλ©΄ μ»΄ν¬λνΈμ μ€μ²© κ΅¬μ‘°κ° λ³΅μ‘ν μν©μμλ **λΉκ΅μ  μ½κ² λ°μ΄ν°λ₯Ό μ λ¬**ν  μ μλ€

<br />

## Context API μμ±νκ³  μ¬μ©νκΈ°

`Context API`λ₯Ό μ¬μ©νλ©΄ μ€κ° μ»΄ν¬λνΈκ° κ°μνμ§ μκ³ λ propsλ₯Ό μ λ¬ν  μ μλ€.

```jsx
import React, { useContext } from "react";

const Main = () => {
  const [user, setUser] = useState({ userName: "yrKim", userID: "april5" });
  const UserContext = createContext(user); // (1)

  return (
    <UserContext.Provider value={user}>
      {" "}
      // (2)
      <MyPage /> // νμμ <Profile />κ° μμ
    </UserContext.Provider>
  );
};

const Profile = () => {
  const user = useContext(UserContext); // (3)
  return (
    <div>
      <p>{`${user.userName}λ μλνμΈμ:)`}</p>
    </div>
  );
};
```

<br />

(1) `Context API` μμ± `createContext('μ΄κΈ°κ°')`

(2) `Provider`λ‘ κ°μΈμ λ°μ΄ν° μ λ¬νκΈ°.
`value`μ λ¬ν  λ μλ‘μ΄ κ°μ²΄κ° λ§λ€μ΄μ§μ§ μλλ‘ ν΄μΌ λΆνμν λ λλ§μ λ°©μ§ν  μ μλ€.

(3) μ λ¬λ°μ λ°μ΄ν° μ¬μ©. `useContext`λ₯Ό μ¬μ©νμ¬ μ λ¬ λ°μ κ°μ κ°μ Έμ¬ μ μλ€.

<br />

---

## νμ μ»΄ν¬λνΈμμ Context λ°μ΄ν° μμ νκΈ°

`Context API`λ‘ μ λ¬λ°μ λ°μ΄ν°λ₯Ό νμ μ»΄ν¬λνΈμμ μμ ν  μ μλ€.

```jsx
import React, { useContext } from "react";

const Main = () => {
  const [user, setUser] = useState({ userName: "yrKim", userID: "april5" });
  const UserContext = createContext(user);
  const SetUserContext = createContext(() => {}); // (1)

  return (
    <SetUserContext.Provider value={setUser}>
      {" "}
      // (2)
      <UserContext.Provider value={user}>
        <MyPage /> // νμμ <Profile />κ° μμ
      </UserContext.Provider>
    </SetUserContext.Provider>
  );
};

const Profile = () => {
  const user = useContext(UserContext);
  const setUser = useContext(SetUserContext); // (3)
  return (
    <div>
      <p>{`${user.userName}λ μλνμΈμ:)`}</p>
      <button onClick={() => setUser(/* λ³κ²½ λ‘μ§ */)}></button>
    </div>
  );
};
```

<br />

(1) μμ± `createContext(() => {})`

(2) `Provider`λ‘ κ°μΈμ λ°μ΄ν° μ λ¬νκΈ°.

(3) μ λ¬λ°μ ν¨μ μ¬μ©. `useContext`λ₯Ό μ¬μ©νμ¬ μ λ¬ λ°μ ν¨μλ₯Ό κ°μ Έμ¬ μ μλ€.

<br />

---

## Context API μ¬μ© μ μ£Όμν  μ 

### βοΈ λΆνμν λ λλ§μ΄ λ°μνμ§ μλλ‘ νκΈ°

- **λ°μ΄ν° μ μ²΄λ₯Ό μνκ°μΌλ‘ κ΄λ¦¬νκΈ°**
  - μ λ¬νλ `value`μ μλ‘μ΄ κ°μ²΄κ° λ§λ€μ΄μ§μ§ μλλ‘ ν΄μΌ λΆνμν λ λλ§μ λ°©μ§ν  μ μλ€

<br />

### βοΈ `Provider`λ₯Ό μ°Ύμ§ λͺ»νλ κ²½μ° λμ

- κ°νΉ `Consumer` μ»΄ν¬λνΈμ `Provider` μ»΄ν¬λνΈλ₯Ό μ μ ν μμΉμμ μ¬μ©νμ§ μμΌλ©΄ Context API λ°μ΄ν°κ° μ λ¬λμ§ μλλ€.
- `Consumer` μ»΄ν¬λνΈκ° `Provider` μ»΄ν¬λνΈλ₯Ό μ°Ύμ§ λͺ»νλ κ²½μ°κ° λ°μνλλ°, κ·Έλ΄ κ²½μ°λ₯Ό λλΉν΄μ **μ΄κΈ°κ°μ μν**ν΄λμ.

<br />
<br />
