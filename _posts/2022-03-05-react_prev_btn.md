---
title: "๐React:: React๋ก Prev/Next Btn ๊ธฐ๋ฅ ๊ตฌํโจ"
tags:
  - [React]
permalink: /study/react/prev_btn

navigation: true
toc: true
toc_sticky: true

date: 2022-03-05
last_modified_at: 2022-03-05
---

![](https://images.velog.io/images/april_5/post/707c8c3b-7893-4776-890a-bd897bb78728/React.png)

๋ฌดํ์คํฌ๋กค ๊ธฐ๋ฅ ๊ตฌํํ๋ฉฐ ๋ฐฐ์ด `documentElement.clientWidth`๋ฅผ ํ์ฉํ์ฌ ๋ง๋  ํ์ด์ง ๋๊ธฐ๊ธฐ ๋ฒํผ!

ํ๋ฉด ์ฌ์ด์ฆ๋ฅผ ๊ตฌํด์์ ๊ฐ ์นด๋์ ๋ฐ์ดํฐ๋ฅผ ๋ช ๊ฐ์ฉ ๊ฐ์ ธ์์ผ ํ๋์ง ๊ณ์ฐ ํ ํ Prev/Next Btn ํด๋ฆญํ  ๋ ๋ง๋ค ํด๋น ๋ฐ์ดํฐ ๊ฐ์ ธ์ค๋ ๋ฐฉ๋ฒ์ผ๋ก ๊ตฌํ.

---

## โ ์์ฑ๋ ์ฝ๋

```jsx
handleNextBtn = (e) => {
  const { giftData, cnt, target } = this.state;
  if (giftData.length <= cnt) {
    this.setState({
      cnt: cnt - target,
    });
    e.preventDefault();
  } else {
    let dataToChange = giftData.slice(cnt, cnt + target);
    this.setState({
      cnt: cnt + target,
      items: dataToChange,
    });
  }
};
```

<br />

#### โ pageSize: ์นด๋๊ฐ ๋ณด์ฌ์ผ ํ  ํ๋ฉด์ ํฌ๊ธฐ ๊ฐ์ ธ์ค๊ธฐ

#### โ target: width๊ฐ 230์ธ ์นด๋๊ฐ ํ๋ฉด์ ๋ช๊ฐ ๋ค์ด๊ฐ ์ ์๋์ง ๊ณ์ฐ

```jsx
pageSize: Math.round(document.documentElement.clientWidth * 0.8),
target: Math.ceil(this.pageSize / 230) - 1,
```

<br />

---

## ๊ฒฐ๊ณผ๋ฌผ

![](https://images.velog.io/images/april_5/post/0a493e6f-9ade-479a-8274-670f585c6387/PrevNextBtn.gif)

์๊ฐ๋ณด๋ค ์๊ฐ์ด ์ค๋๊ฑธ๋ ธ๋ ๊ธฐ๋ฅ์ด๋ค. ์์งํ ๋๋ฌด ์ด๋ ต๋ค๊ณ  ์๊ฐํด์ ํฌ๊ธฐํ  ๋ป ํ๋ ๊ธฐ๋ฅ์ธ๋ฐ, ๋ฉํ ๋๊ป์ ๊ผญ ํ์ผ๋ฉด ์ข๊ฒ ๋คํ์ฌ.. ์ ๋ง ์ธ๋ฉฐ ๊ฒจ์๋จน๊ธฐ๋ก ๊ฒจ์ฐ ๊ตฌํํ ๊ธฐ๋ฅ๐
๋์๋ณด๋ ๊ทธ๋๋ ๋์๊ฒ ๋จ๋ ๊ฒฝํ์ด ๋์๋ค! ๋ฉํ ๋ ๊ฐ์ฌํฉ๋๋คใใใใใใใใ๐๐๐

<br /><br />
