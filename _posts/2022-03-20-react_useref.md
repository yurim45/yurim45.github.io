---
published: true
title: "๐React Hooks:: useRef() "
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

## โ๏ธ [React ๊ณต์๋ฌธ์](https://ko.reactjs.org/docs/hooks-reference.html#useref)์์ ์ค๋ชํ๋ `useRef`

- `useRef`๋ `.current` ํ๋กํผํฐ๋ก ์ ๋ฌ๋ ์ธ์(initialValue)๋ก, ์ด๊ธฐํ๋ ๋ณ๊ฒฝ ๊ฐ๋ฅํ `ref` ๊ฐ์ฒด๋ฅผ ๋ฐํ.
- ๋ณธ์ง์ ์ผ๋ก useRef๋ .current ํ๋กํผํฐ์ ๋ณ๊ฒฝ ๊ฐ๋ฅํ ๊ฐ์ ๋ด๊ณ  ์๋ โ์์โ๋ก์, ๊ฐ์ฒด์ด๋ค.
  - `useRef()`๋ ์์ ์๋ฐ์คํฌ๋ฆฝํธ ๊ฐ์ฒด๋ฅผ ์์ฑ `{current: ...}`
- useRef๋ ๋งค๋ฒ ๋ ๋๋ง์ ํ  ๋ ๋์ผํ `ref` ๊ฐ์ฒด๋ฅผ ์ ๊ณต.
- useRef๋ ๋ด์ฉ์ด ๋ณ๊ฒฝ๋  ๋ ์๋ ค์ฃผ์ง ์์ผ๋ฉฐ, `.current` ํ๋กํผํฐ๋ฅผ ๋ณํํ๋ ๊ฒ์ด **๋ฆฌ๋ ๋๋ง์ ๋ฐ์์ํค์ง๋ ์๋๋ค.**

<br />

---

## โ๏ธ ์ ๋ฆฌํ๋ฉด `useRef`๋

- `ref`๊ฐ์ฒด๋ฅผ ๋ง๋ค์ด ๋ด๋ `hook`์ด๋ฉฐ
- `ref`๋ `render` ๋ฉ์๋์์ ์์ฑ๋ DOM node๋ React Element์ ์ ๊ทผํ  ์ ์๋๋ก ํ๋ค.
- `ref`๋ ๋ณ๊ฒฝ ๊ฐ๋ฅํ ๊ฐ์ ๋ด๊ณ  ์๋ ๊ฐ์ฒด์ด๊ณ 
- ์ด๋ `ref` ๊ฐ์ฒด ์์ ๊ฐ์ React์ ์๋ช์ฃผ๊ธฐ์์ ๋๋ฆฝ์ ์ด๊ธฐ ๋๋ฌธ์`re-render`์ ์๊ด์์ด ๊ฐ์ด ์ ์ง๋๋ค
- ๊ฐ์ด ๋ณ๊ฒฝ๋๋๋ผ๋ `render` ๋์ง ์๊ณ , `render` ๋๋๋ผ๋ ๊ฐ์ด ์ ์ง๋๋ ํน์ง์ ๊ฐ์ง๋ค

<br />

### `useRef` ์ฌ์ฉ ์ฌ๋ก

1. ํน์  DOM์ ์ ๊ทผํด์ผ ํ  ๋

- ํน์  ์๋ฆฌ๋จผํธ์ ํฌ๊ธฐ๋ฅผ ๊ฐ์ ธ์ค๊ธฐ
- ์คํฌ๋กค๋ฐ ์์น ๊ฐ์ ธ์ค๊ธฐ ๋๋ ์ค์ 
- ์ธํ๋ฐ์ค ํฌ์ปค์ค ์ค์  ๋ฑ

2. ๋ค์ ๋ ๋๋ง ๋์ด๋ ๋์ผํ ์ฐธ์กฐ๊ฐ์ ์ ์งํ  ๋

- ์ผ๋ฐ ๋ณ์๋ ์ฌ ์ ์ธ๋๊ธฐ ๋๋ฌธ์ ์ด๊ธฐํ๊ฐ ์ผ์ด๋๊ณ 
- state ๋ํ ๊ฐ์ด ๋ณ๊ฒฝ๋๋ฏ๋ก

3. setInterval, setTimeout clear ํ  ๋ ๋ฑ

<br />

### :: ์ฝ๋ ์์

2. ๋ค์ ๋ ๋๋ง ๋์ด๋ ๋์ผํ ์ฐธ์กฐ๊ฐ์ ์ ์งํ  ๋

- state๊ฐ ๋ณํ๋๋ผ๋ render์ ์๊ด์์ด ์ ์ง๋๋ฏ๋ก, state๊ฐ ๋ฐ๋์ด๋ `ref`์์ ๊ฐ์ `0`์ด ์ ์ง

```jsx
import React, { useEffect, useState, useRef } from 'react';

const Example = () =>{
  const [count, setCount] = useState(0);
  const countRef = useRef(count);

   useEffect(() => {
  	countRef.current = count;
   },[count])  // (1) ์ฒซ ๋ฒ์งธ useEffect

   useEffect(() => {
     return () => {
       console.log("unmount ์ ์ถ๋ ฅ", countRef.current);
     };
   }, []);     // (2) ๋ ๋ฒ์งธ useEffect

  return (
      <>
      	<h1>{count}</h1>
      	<button onClick={()=>setCount(c=>c+1)}>+<button/>
      </>
}
```

<br />

---

!! ์ฐธ๊ณ  ์๋ฃ

- [[React] useRef 200% ํ์ฉํ๊ธฐ](https://velog.io/@juno7803/React-useRef-200-%ED%99%9C%EC%9A%A9%ED%95%98%EA%B8%B0)
- [useRef() ํจ์](https://xiubindev.tistory.com/98)
