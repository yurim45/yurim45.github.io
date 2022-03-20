---
title: "🚀React:: React Hooks:: useRef() "
tags:
  - [React]
permalink: /study/react/useref

navigation: true
toc: true
toc_sticky: true

date: 2022-03-20
last_modified_at: 2022-03-20
---

![](https://images.velog.io/images/april_5/post/8e5057df-796b-47be-88e5-212cd8bee94e/image.png)

## ✔️ [React 공식문서](https://ko.reactjs.org/docs/hooks-reference.html#useref)에서 설명하는 `useRef`

- `useRef`는 `.current` 프로퍼티로 전달된 인자(initialValue)로, 초기화된 변경 가능한 `ref` 객체를 반환.
- 본질적으로 useRef는 .current 프로퍼티에 변경 가능한 값을 담고 있는 “상자”로서, 객체이다.
  - `useRef()`는 순수 자바스크립트 객체를 생성 `{current: ...}`
- useRef는 매번 렌더링을 할 때 동일한 `ref` 객체를 제공.
- useRef는 내용이 변경될 때 알려주지 않으며, `.current` 프로퍼티를 변형하는 것이 **리렌더링을 발생시키지는 않는다.**

<br />

---

## ✔️ 정리하면 `useRef`는

- `ref`객체를 만들어 내는 `hook`이며
- `ref`는 `render` 메서드에서 생성된 DOM node나 React Element에 접근할 수 있도록 한다.
- `ref`는 변경 가능한 값을 담고 있는 객체이고
- 이때 `ref` 객체 안의 값은 React의 생명주기에서 독립적이기 때문에`re-render`와 상관없이 값이 유지된다
- 값이 변경되더라도 `render` 되지 않고, `render` 되더라도 값이 유지되는 특징을 가진다

<br />

### `useRef` 사용 사례

1. 특정 DOM에 접근해야 할 때

- 특정 엘리먼트의 크기를 가져오기
- 스크롤바 위치 가져오기 또는 설정
- 인풋박스 포커스 설정 등

2. 다시 렌더링 되어도 동일한 참조값을 유지할 때

- 일반 변수는 재 선언되기 때문에 초기화가 일어나고
- state 또한 값이 변경되므로

3. setInterval, setTimeout clear 할 때 등

<br />

### :: 코드 예시

2. 다시 렌더링 되어도 동일한 참조값을 유지할 때

- state가 변하더라도 render에 상관없이 유지되므로, state가 바뀌어도 `ref`안의 값은 `0`이 유지

```jsx
import React, { useEffect, useState, useRef } from 'react';

const Example = () =>{
  const [count, setCount] = useState(0);
  const countRef = useRef(count);

   useEffect(() => {
  	countRef.current = count;
   },[count])  // (1) 첫 번째 useEffect

   useEffect(() => {
     return () => {
       console.log("unmount 시 출력", countRef.current);
     };
   }, []);     // (2) 두 번째 useEffect

  return (
      <>
      	<h1>{count}</h1>
      	<button onClick={()=>setCount(c=>c+1)}>+<button/>
      </>
}
```

<br />

---

!! 참고 자료

- [[React] useRef 200% 활용하기](https://velog.io/@juno7803/React-useRef-200-%ED%99%9C%EC%9A%A9%ED%95%98%EA%B8%B0)
- [useRef() 함수](https://xiubindev.tistory.com/98)
