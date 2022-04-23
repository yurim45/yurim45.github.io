---
published: true
title: "React에 type 적용하기"
tags:
  - [React]
permalink: /study/react/typescript

navigation: true
toc: true
toc_sticky: true

date: 2022-04-23
last_modified_at: 2022-04-23
---

![](https://velog.velcdn.com/images/april_5/post/1cb99d0d-db9c-4c05-b565-e337351bbd6a/image.png)

# React Compoenent에서 type 정의하기

<br />

## 이벤트 객체와 이벤트 처리 함수의 타입

> 리액트 컴포넌트에서 <span style='color:dodgerblue'>**이벤트 처리 함수의 타입**</span>을 자주 작성하기 때문에 미리 타입을 만들어 놓고 <span style='color:dodgerblue'>**재사용**</span>하는 게 좋다.

```tsx
import React from 'react';

type EventObject<t = HTMLElement> = React.SyntheticEvent<T>;  // (1)

type EventFunc<T = HTMLElement> (e : EventObject<T> => void)  // (2)
```

(1) 리액트에서 발생하는 대부분의 이벤트 객체는 EventObject 타입으로 정의할 수 있다.
특정 이벤트에 특화된 타입을 원한다면 제네릭 T에 원하는 타입을 입력한다.

(2) 대부분의 이벤트 처리 함수를 EventFunc로 정의할 수 있다.
마찬가지로 원하는 타입을 제네릭 T에 입력할 수 있다. 이 타입응ㄴ 이벤트 처리 함수를 속성 값으로 전달할 떄 유용하게 사용된다.

<br />

---

## 함수형 컴포넌트의 타입 정의하기

```tsx
import React from "react";

interface Props {
  // (1)
  name: string;
  age?: number;
}

export default function MyComponent({ name, age = 23 }) {
  // (2)
  return (
    <div>
      <p>{name}</p>
      <p>{age.substr(0)}</p> /* (3) 타입 에러! */
    </div>
  );
}

const MyComponent: React.FunctionComponent<Props> = function ({
  name,
  age = 23,
}) {
  // (2)
  return (
    <div>
      <p>{name}</p>
      <p>{age.substr(0)}</p> /* (3) 타입 에러! */
    </div>
  );
};
```

(1) 속성값의 타입을 정의.
속성값의 타입 정보는 문서의 역할을 하므로 최상단에서 정의한다.
물음표 기호를 이용해서 선택 속성을 정의할 수 있다

(2) `Props` 타입을 이용해서 속성값의 타입을 입력.
컴포넌트 속성값의 기본값은 자바스크립트 표준 문법을 사용하면 된다.

(3) 타입스크립트는 `age`가 숫자라는 것을 알기 때문에 `substr` 메서드를 호출하면 타입 에러가 발생한다.
`MyComponent`를 사용하는 곳에서는 `name` 속성을 반드시 입력해야 하며, `age` 속성은 입력하지 않아도 된다. 그 외의 속성을 입력하려고 하면 타입 에러가 발생한다.
