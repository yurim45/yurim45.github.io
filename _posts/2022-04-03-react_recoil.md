---
published: true
title: "React를 위한 상태관리 라이브러리 Recoil"
tags:
  - [React]
permalink: /study/react/recoil

navigation: true
toc: true
toc_sticky: true

date: 2022-04-03
last_modified_at: 2022-04-03
---

![](https://media.vlpt.us/images/april_5/post/76c6312a-ae21-4da5-898a-20f39b1487d7/image.png)

![](https://images.velog.io/images/april_5/post/9577451a-7bad-428b-bc0e-1fc038a96513/image.png)

> 페이스북이 만든 상태관리 라이브러리 Recoil

리액트의 상태 관리를 하는 방법은 여러 가지가 있지만,
새로 다뤄야 하는 Recoil에 대해 공부한 내용을 기록한다.

<br />

# 주요 개념

공식문서: Recoil을 사용하면 atoms (공유 상태)에서 selectors (순수 함수)를 거쳐 React 컴포넌트로 내려가는 data-flow graph를 만들 수 있다.
Atoms는 컴포넌트가 구독할 수 있는 상태의 단위다.
Selectors는 atoms 상태값을 동기 또는 비동기 방식을 통해 변환한다.

> redux와 비교해보면, Atoms는 store, Selectors는 action 함수인가? 🤔

## Recoil의 핵심 컨셉

- 오직 React만을 위해 React처럼
- React의 내부 상태만 이용
- 작은 Atom 단위로 관리
- 순수 함수 Selector
- Re-Render 최소화
  - 상태를 변경하는 Atom을 참조하는 컴포넌트만 리렌더링 됨
- 데이터 흐름을 따라서
  - Recoil의 상태들은 상호의존성을 가질 수 있는데,
  - 데이터의 흐름에 따라서 여러 상태들의 연관된 컴포넌트들을 유기적으로 관리할 수 있음

<br />

---

## 시작하기

### ✔️ 설치

`npm install recoil`

### ✔️ RecoilRoot

recoil 상태를 사용하는 컴포넌트는 부모 트리 어딘가에 나타나는 RecoilRoot 가 필요하다.
루트 컴포넌트가 RecoilRoot를 넣기에 가장 좋은 장소다.

```js
import React from "react";
import {
  RecoilRoot,
  atom,
  selector,
  useRecoilState,
  useRecoilValue,
} from "recoil";

function App() {
  return (
    <RecoilRoot>
      <CharacterCounter />
    </RecoilRoot>
  );
}
```

<br />

---

## Atoms

> 상태 정의하기

- Atoms는 상태의 단위이며, 업데이트와 구독이 가능하다.
- `atom`이 업데이트되면 각각의 구독된 컴포넌트는 새로운 값을 반영하여 다시 렌더링 된다.
- atoms는 런타임에서 생성될 수도 있다.
- Atoms는 React의 로컬 컴포넌트의 상태 대신 사용할 수 있다.
- 동일한 `atom`이 여러 컴포넌트에서 사용되는 경우 모든 컴포넌트는 상태를 공유한다.

### ✔️ `atom` 함수를 사용해 생성

> `atom` 함수에 `key`와 `default`로 기본값 설정

- `key`는 고유해야 하며
- `default` 초기값은 비워도 된다

```js
const fontSizeState = atom({
  key: "fontSizeState",
  default: 14,
});

// 또는
const fontState = atom({
  key: "fontState",
  default: {
    idx: 0,
    name: "subTitle",
    size: 18,
    color: "blue",
  },
});
```

<br />

### ✔️ `atom` 호출

> atom을 읽고 쓰려면 `useRecoilState`라는 훅을 사용.
> `useState`와 비슷하지만 <span style='color:dodgerblue'>**상태가 컴포넌트 간에 공유될 수 있다는 차이**</span>가 있다.

```js
import { atom } form 'recoil';

function FontButton() {
  const [fontSize, setFontSize] = useRecoilState(fontSizeState);
  return (
    <button onClick={() => setFontSize((size) => size + 1)} style={{fontSize}}>
      Click to Enlarge
    </button>
  );
}

// 버튼을 클릭하면 버튼의 글꼴 크기가 1만큼 증가하며,
// fontSizeState atom을 사용하는 다른 컴포넌트의 글꼴 크기도 같이 변화한다.
function Text() {
  const [fontSize, setFontSize] = useRecoilState(fontSizeState);
  return <p style={{fontSize}}>This text will increase in size too.</p>;
}
```

<br />

---

## Selectors

> <span style='color:dodgerblue'>**getter**</span>와 <span style='color:dodgerblue'>**setter**</span>를 직접 정의해서 사용할 수 있는 순수함수. `Selector`

![](https://images.velog.io/images/april_5/post/968810e4-b42b-4f26-befa-491d5eef5d2c/image.png)

- atoms나 다른 selectors를 입력으로 받아들이는 순수 함수(pure function).
- <span style='background-color:yellow'>상태를 읽고 쓸 때 데이터를 가공</span>하거나, (ex. 정렬, 필터 등)
- <span style='background-color:yellow'>유효성 검사 등의 부수적인 로직 추가</span> 가능
- selector는 <span style='background-color:yellow'>다른 atom이나 selector를 참조(구독)할 수 있다</span>
  - 구독되면 다른 데이터들에 대해서 의존성을 갖게 되고
  - 구독하고 있는 상태가 외부에서 변경되면 본 selector는 이를 감지하고 재평가 되어서 컴포넌트들도 다시 렌더링된다.

> 컴포넌트의 관점에서 보면 `selectors`와 `atoms`는 <span style='color:dodgerblue'>**동일한 인터페이스를 가지므로 서로 대체할 수 있다.**</span>

<br />

### ✔️ `Selectors` 생성

> Selectors는 `selector`함수를 사용해 정의

```js
const fontSizeLabelState = selector({
  key: "fontSizeLabelState",
  get: ({ get }) => {
    const fontSize = get(fontSizeState);
    const unit = "px";

    return `${fontSize}${unit}`;
  },
});
```

<br />

---

### ✅ 읽기 전용 함수와 쓰기 전용 함수

Recoil에서는 특이하게 읽기 전용 함수와 쓰기 전용 함수를 제공한다.

- `Selectors`는 `useRecoilValue()`를 사용해 읽을 수 있다
  - `useRecoilValue` 읽기 전용 함수 예제

```js
function FontButton() {
  const [fontSize, setFontSize] = useRecoilState(fontSizeState);
  const fontSizeLabel = useRecoilValue(fontSizeLabelState);

  return (
    <>
      <div>Current font size: ${fontSizeLabel}</div>

      <button onClick={setFontSize(fontSize + 1)} style={{ fontSize }}>
        Click to Enlarge
      </button>
    </>
  );
}
```

- `useSetRecoilState` 쓰기 전용 함수 예제
  - reference 학습할 때 좀 더 공부해보자..😅

```js
const setList = useSetRecoilState(productsState);
```

<br />

---

## 상태 초기화

Recoil에서는 reset 함수를 추가로 제공한다.

```js
// ... 생략

const resetProducts = useResetRecoilState(productsState);

useEffect(() => {
  return () => resetProducts(); // 언마운트 될 때 초기화
}, []);
```
