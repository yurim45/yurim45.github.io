---
published: true
title: "🚀React Hooks:: useContext()로 상태 관리하기"
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

`Consumer` 컴포넌트 없이 `Context` 사용하기

# Context API

- 상위 컴포넌트에서 하위 컴포넌트로 데이터를 전달할 때 props가 사용되는데, 가까운 거리에 있는 몇 개의 하위 컴포넌트로 전달할 때는 props로도 충분하지만,
- 많은 수의 하위 컴포넌트로 전달할 때는 기계적으로 props를 전달해야 하는 코드를 작성해야 하는 상황이 발생한다.

> 이럴 때 `Context API` 를 사용하면 컴포넌트의 중첩 구조가 복잡한 상황에서도 **비교적 쉽게 데이터를 전달**할 수 있다

<br />

## Context API 생성하고 사용하기

`Context API`를 사용하면 중간 컴포넌트가 개입하지 않고도 props를 전달할 수 있다.

```jsx
import React, { useContext } from "react";

const Main = () => {
  const [user, setUser] = useState({ userName: "yrKim", userID: "april5" });
  const UserContext = createContext(user); // (1)

  return (
    <UserContext.Provider value={user}>
      {" "}
      // (2)
      <MyPage /> // 하위에 <Profile />가 있음
    </UserContext.Provider>
  );
};

const Profile = () => {
  const user = useContext(UserContext); // (3)
  return (
    <div>
      <p>{`${user.userName}님 안녕하세요:)`}</p>
    </div>
  );
};
```

<br />

(1) `Context API` 생성 `createContext('초기값')`

(2) `Provider`로 감싸서 데이터 전달하기.
`value`전달할 때 새로운 객체가 만들어지지 않도록 해야 불필요한 렌더링을 방지할 수 있다.

(3) 전달받은 데이터 사용. `useContext`를 사용하여 전달 받은 값을 가져올 수 있다.

<br />

---

## 하위 컴포넌트에서 Context 데이터 수정하기

`Context API`로 전달받은 데이터를 하위 컴포넌트에서 수정할 수 있다.

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
        <MyPage /> // 하위에 <Profile />가 있음
      </UserContext.Provider>
    </SetUserContext.Provider>
  );
};

const Profile = () => {
  const user = useContext(UserContext);
  const setUser = useContext(SetUserContext); // (3)
  return (
    <div>
      <p>{`${user.userName}님 안녕하세요:)`}</p>
      <button onClick={() => setUser(/* 변경 로직 */)}></button>
    </div>
  );
};
```

<br />

(1) 생성 `createContext(() => {})`

(2) `Provider`로 감싸서 데이터 전달하기.

(3) 전달받은 함수 사용. `useContext`를 사용하여 전달 받은 함수를 가져올 수 있다.

<br />

---

## Context API 사용 시 주의할 점

### ✔️ 불필요한 렌더링이 발생하지 않도록 하기

- **데이터 전체를 상태값으로 관리하기**
  - 전달하는 `value`에 새로운 객체가 만들어지지 않도록 해야 불필요한 렌더링을 방지할 수 있다

<br />

### ✔️ `Provider`를 찾지 못하는 경우 대응

- 간혹 `Consumer` 컴포넌트와 `Provider` 컴포넌트를 적절한 위치에서 사용하지 않으면 Context API 데이터가 전달되지 않는다.
- `Consumer` 컴포넌트가 `Provider` 컴포넌트를 찾지 못하는 경우가 발생하는데, 그럴 경우를 대비해서 **초기값을 셋팅**해두자.

<br />
<br />
