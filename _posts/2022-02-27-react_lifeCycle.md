---
title: "๐React:: React Lifecycle & ์กฐ๊ฑด๋ถ ๋ ๋๋ง"
tags:
  - [React]
permalink: /study/react/life_cycle

navigation: true
toc: true
toc_sticky: true

date: 2022-02-27
last_modified_at: 2022-02-27
---

![](https://images.velog.io/images/april_5/post/707c8c3b-7893-4776-890a-bd897bb78728/React.png)

๋ถ๋ชจ ์ปดํฌ๋ํธ์ ์์ ์ปดํฌ๋ํธ์ <span style="color:blue">Lifecycle</span>์ ๋ํด ์์๋ณด๊ณ  <span style="color:red">๊ด๋ จ๋ ์๋ฌ๋ฅผ ํด๊ฒฐ</span>ํ๋ ๋ฐฉ๋ฒ ์๊ธฐ!!
`์๊ธฐ ์ ์ ํ๋ ์ธ์๐ ๋ฐ๋ก ์ ์ฉํ๋ ์กฐ๊ฑด๋ถ ๋ ๋๋ง!!`

---

# Lifecycle์ด๋?

> React ์ปดํฌ๋ํธ ์์ state์ ์๋ช์ฃผ๊ธฐ

![](https://images.velog.io/images/april_5/post/a74e85b6-7ef7-415f-928b-f8357d6f8563/image.png)

<br />

---

## โ Lifecycle ๊ธฐ๋ณธ ์์

1. constructor
2. render
3. componentDidMount
4. (fetch ์๋ฃ)
5. render
6. (setState)
7. componentDidUpdate (setState ๋์๊ธฐ ๋๋ฌธ์ ์ปดํฌ๋ํธ ์๋ฐ์ดํธ ๋ฐ์)
8. componentWillUnmount
   ![](https://images.velog.io/images/april_5/post/af4002d6-40ea-4d10-8722-62e31c47d41b/image.png)

<br />

---

## โ ๋ถ๋ชจ - ์์ Lifecycle

- ๋ถ๋ชจ API์์ ๋ฐ์ ๋ฐ์ดํฐ๋ฅผ ์์์๊ฒ props๋ก ์ ๋ฌํ์ฌ ์์ ๋ด๋ถ์์ ๋ฐ์ดํฐ์ ์ ๊ทผํ์ฌ ์ฌ์ฉํ๋ ๊ฒฝ์ฐ
  ![](https://images.velog.io/images/april_5/post/f4de1ee8-53ae-4963-ace4-09d952c931cf/image.png)

<br />

---

# AND์ฐ์ฐ์(&&) ์ฌ์ฉํ ์กฐ๊ฑด๋ถ ๋ ๋๋ง!

![](https://images.velog.io/images/april_5/post/6365ede1-9a26-419a-8cc6-d8eb992c8c78/image.png)
<span style="color:red">Cannot read property 'map' of undefined</span> ๐คฌ๐คฌ๐คฌ๐คฌ๐คฌ

Mockup ๋ฐ์ดํฐ๋ฅผ ๊ตฌ์ฑํ์ฌ importํ๊ฑฐ๋ ํ๋ก์ ํธ๊ฐ ์์๋๊ณ  ๋ฐฑ์๋ API๋ฅผ ๋ถ์ด๊ธฐ ์์ํ๋ฉด์ ๋ฐ์ํ๋ ์๋ฌ ์ค ํ๋. ๋ฐ์ดํฐ๊ฐ ์๋๋ฐ map์ ๋๋ ธ์ผ๋ ์๋ฌ๊ฐ ๋ฐ์ํ  ์ ๋ฐ์.... ๐ญ
์ํ๊ฐ์ ์์ ์ ๊ดํ ๋ฌธ์ ๋ผ๋ฉด React์ Lifecycle๊ณผ ์ฐ๊ด์ด ์๊ณ , ์ด ๋ ์กฐ๊ฑด๋ถ ๋ ๋๋ง ์ฒ๋ฆฌ๋ฅผ ํด ์ฃผ์ด ์๋ฌ๋ฅผ ํด๊ฒฐํ๋ค.

์๋๋ 1์ฐจ ํ๋ก์ ํธ์์ ์ค์  ์ ์ฉํ <span style="color:blue">์กฐ๊ฑด๋ถ ๋ ๋๋ง</span> ์ฝ๋!

![](https://images.velog.io/images/april_5/post/c5b59358-f30a-4f7a-b47d-ee024375b3f2/image.png)
`1์ฐจ ํ๋ก์ ํธ๋ฅผ ์งํํ๋ฉด์ ์ข์ข ๋ฐ์ํ๋ ์๋ฌ ์ค ํ๋..๐`

<br />

---

## โ AND์ฐ์ฐ์(&&) ์ฌ์ฉ ์ ์ฃผ์ํ  ์ !

- ๋ณ์๊ฐ ์ซ์ ํ์์ธ ๊ฒฝ์ฐ `0`์ `false` ์ด๋ค.
- ๋ณ์๊ฐ ๋ฌธ์์ด ํ์์ธ ๊ฒฝ์ฐ ๋น ๋ฌธ์์ด`โโ`๋ `false`์ด๋ค.

<br />

---

์ฐธ๊ณ  ์๋ฃ

- [React | Lifecycle](https://velog.io/@joonsikyang/React-Project-Lifecycle)
- [๊ณต์๋ฌธ์ | State and Lifecycle](https://ko.reactjs.org/docs/state-and-lifecycle.html)
