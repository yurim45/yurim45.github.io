---
title: "๐ ๋คํธ์ํฌ ๊ตฌ์กฐ ์ดํด:: OSI๋ชจ๋ธ์ ์ ์ก ๊ณ์ธต"
tags:
  - [network]
permalink: /network/transport_layer

navigation: true
toc: true
toc_sticky: true

date: 2021-11-19
last_modified_at: 2021-11-19
---

![]()

<span style="color:Teal">**OSI๋ชจ๋ธ**</span>์ 4๊ณ์ธต์ธ <span style="color:Teal">**์ ์ก ๊ณ์ธต**</span>์ ๋ํด ๊ณต๋ถํ๊ธฐ

---

# ๐ ์ ์ก ๊ณ์ธต\_์ ๋ขฐํ  ์ ์๋ ๋ฐ์ดํฐ ์ ์กํ๊ธฐ

### ๐ What I Will Learn

- ์ ์ก ๊ณ์ธต์ ์ญํ ์ ์ดํดํ๋ค
- ์ฐ๊ฒฐํ ํต์ ๊ณผ ๋น์ฐ๊ฒฐํ ํต์ ์ ์ดํดํ๋ค
- TCP๋ฅผ ์ดํดํ๋ค
- UDP๋ฅผ ์ดํดํ๋ค

---

## <span style="background-color:aquamarine">LESSON 23. ์ ์ก ๊ณ์ธต์ ์ญํ </span>

### 1) ์ ์ก ๊ณ์ธต์ ๋ ๊ฐ์ง ์ญํ 

> โ  ๋ฐ์ดํฐ๊ฐ ์ ๋๋ก ๋์ฐฉํ๋์ง ํ์ธ <br />
> โก ์ ์ก๋ ๋ฐ์ดํฐ์ ๋ชฉ์ ์ง๊ฐ ์ด๋ค ์ ํ๋ฆฌ์ผ์ด์์ธ์ง ์๋ณ

OSI๋ชจ๋ธ์ ๋ฌผ๋ฆฌ ๊ณ์ธต, ๋ฐ์ดํฐ ๋งํฌ ๊ณ์ธต, ๋คํธ์ํฌ ๊ณ์ธต์ 3๊ณ์ธต์ด ์์ผ๋ฉด ๋ชฉ์ ์ง์ ๋ฐ์ดํฐ๋ฅผ ๋ณด๋ผ ์ ์๋ค.

๋คํธ์ํฌ ๊ณ์ธต์์ ๋ค๋ฅธ ๋คํธ์ํฌ๋ก ๋ฐ์ดํฐ๋ฅผ ์ ์กํ๋ ค๋ฉด ๋ผ์ฐํฐ๊ฐ ํ์ํ๊ณ , ๋ผ์ฐํฐ์ ๋ผ์ฐํ ๊ธฐ๋ฅ์ ์ฌ์ฉํ์ฌ ์ ์กํ  ์ ์์ง๋ง,

- ๋ผ์ฐํ ์ ๋ณด๊ฐ ์๋ชป๋  ์ ์๊ณ 
- ๋ง์ ๋ผ์ฐํฐ๋ฅผ ๊ฒฝ์ ํ๋ ๋์ค์ ๋ผ์ฐํฐ์ ๋ฌธ์ ๊ฐ ์๊ธฐ๊ฑฐ๋
- ํจํท์ด ์์๋๊ฑฐ๋ ์ ์ค๋๋๋ผ๋

์ด 3๊ณ์ธต์์๋ ์๋ฌด๊ฒ๋ ํ  ์ ์๋๊ฒ ์๋ค

> OSI๋ชจ๋ธ์ ์ ์ก ๊ณ์ธต์ ๋ชฉ์ ์ง์ ์ ๋ขฐํ  ์ ์๋ ๋ฐ์ดํฐ๋ฅผ ์ ๋ฌํ๊ธฐ ์ํด ํ์!!!

![](https://images.velog.io/images/april_5/post/af235b3e-1c1c-4e85-a7ed-3681625c9878/image.png)

์ ์ก ๊ณ์ธต์๋ <span style="color:Teal">**์ค๋ฅ๋ฅผ ์ ๊ฒํ๋ ๊ธฐ๋ฅ**</span>์ด ์์ด์ ์ค๋ฅ๊ฐ ๋ฐ์ํ๋ฉด ๋ฐ์ดํฐ๋ฅผ ์ฌ์ ์กํ๋๋ก ์์ฒญํ๋ค

> ์ฆ, ๋คํธ์ํฌ ๊ณ์ธต์์๋ ๋ฐ์ดํฐ๋ฅผ ์ ๋ฌํ๊ณ 
> <span style="background-color:yellow">**์ ์ก ๊ณ์ธต**์์๋ ๋ฐ์ดํฐ๊ฐ ์ ๋๋ก ๋์ฐฉํ๋์ง ํ์ธ</span>

์ ์ก ๊ณ์ธต์
์ปดํจํฐ๊ฐ ๋ฐ์ดํฐ๋ฅผ ์ ๋ฌ๋ฐ๊ณ  ์ด๋ค ์ ํ๋ฆฌ์ผ์ด์์ ์ ๋ฌํด์ผ ํ๋์ง ํ๋จ ํ ํด๋น ์ ํ๋ฆฌ์ผ์ด์์ ์ ๋ฌํ  ์ ์๋๋ก ํด์ค๋ค

![](https://images.velog.io/images/april_5/post/c579339d-9124-43fe-80c4-4e0f1d5ba2d4/image.png)

<br />

> **- ์ ์ก ๊ณ์ธต์ ๋ ๊ฐ์ง ์ญํ **
> โ  ๋ฐ์ดํฐ๊ฐ ์ ๋๋ก ๋์ฐฉํ๋์ง ํ์ธ <br />
> โก ์ ์ก๋ ๋ฐ์ดํฐ์ ๋ชฉ์ ์ง๊ฐ ์ด๋ค ์ ํ๋ฆฌ์ผ์ด์์ธ์ง ์๋ณ

<br />

### 1) ์ฐ๊ฒฐํ ํต์ ๊ณผ ๋น์ฐ๊ฒฐํ ํต์ 

์ ์ก ๊ณ์ธต์ ํน์ง์ ๊ฐ๋จํ ์์ฝํ๋ฉด <span style="color:Teal">**์ ๋ขฐ์ฑ/์ ํ์ฑ**</span>๊ณผ <span style="color:Teal">**ํจ์จ์ฑ**</span>์ผ๋ก ๊ตฌ๋ถํ  ์ ์๋ค

- **์ ๋ขฐ์ฑ/์ ํ์ฑ**: ๋ฐ์ดํฐ๋ฅผ ๋ชฉ์ ์ง์ ๋ฌธ์ ์์ด ์ ๋ฌํ๋ ๊ฒ
- **ํจ์จ์ฑ**: ๋ฐ์ดํฐ๋ฅผ ๋น ๋ฅด๊ณ  ํจ์จ์ ์ผ๋ก ์ ๋ฌํ๋ ๊ฒ

์ฌ๊ธฐ์
<u>์ ๋ขฐํ  ์ ์๊ณ  ์ ํํ ๋ฐ์ดํฐ๋ฅผ ์ ๋ฌํ๋ ํต์ </u>์ <span style="color:Teal">**์ฐ๊ฒฐํ ํต์ **</span>์ด๋ผ๊ณ  ํ๊ณ ,

> **์ฐ๊ฒฐํ ํต์ **: <span style="color:Teal">**์ ๋ขฐ์ฑ/์ ํ์ฑ**</span>์ด ์ฐ์ ์ธ ํต์ ์ด๋ผ์ ์ฌ๋ฌ ๋ฒ ํ์ธํ๊ณ  ๋ณด๋ด๋, ์๋ํธ๊ณผ ํ์ธํด๊ฐ๋ฉฐ ํต์ ํ๋ ๋ฐฉ์

<u>ํจ์จ์ ์ผ๋ก ๋ฐ์ดํฐ๋ฅผ ์ ๋ฌํ๋ ํต์ </u>์ <span style="color:Teal">**๋น์ฐ๊ฒฐํ ํต์ **</span>์ด๋ผ๊ณ  ํ๋ค

> **๋น์ฐ๊ฒฐํ ํต์ **: <span style="color:Teal">**ํจ์จ์ฑ**</span>์ด ์ฐ์ ์ธ ํต์ ์ด๋ฏ๋ก ํ์ธ ์ ์ฐจ ์์ด ์ผ๋ฐฉ์ ์ผ๋ก ๋ณด๋ด๋, ์๋ํธ์ ํ์ธํ์ง ์๊ณ  ์ผ๋ฐฉ์ ์ผ๋ก ๋ฐ์ดํฐ๋ฅผ ์ ์กํ๋ ๋ฐฉ์ <br /> ์์) ๋์์: _๋ฐ์ดํฐ๊ฐ ๋ฆ๊ฒ ๋์ฐฉํด์ ํ๋ฉด์ด ๋ฒ๋ฒ๊ฑฐ๋ฆฌ๋ ๊ฒ ๋ณด๋ค, ๋ฐ์ดํฐ๊ฐ ์ฝ๊ฐ ์ ์ค๋๋๋ผ๋ ์ํํ๊ฒ ๋ณด๋ ๊ฒ์ด ์ข์ผ๋๊น!_

![](https://images.velog.io/images/april_5/post/2bade79f-eacd-4100-b01a-bc9111317e3a/OSI%20%E1%84%8C%E1%85%A5%E1%86%AB%E1%84%89%E1%85%A9%E1%86%BC%20%E1%84%80%E1%85%A8%E1%84%8E%E1%85%B3%E1%86%BC.jpeg)

์ ์ก ๊ณ์ธต์ ์ฐ๊ฒฐํ ํต์  ํ๋กํ ์ฝ์๋ <span style="background-color:yellow">TCP</span>๊ฐ ์ฌ์ฉ๋๊ณ , ๋น์ฐ๊ฒฐํ ํต์  ํ๋กํ ์ฝ์๋ <span style="background-color:yellow">UDP</span>๊ฐ ์ฌ์ฉ๋๋ค

<br />

---

## <span style="background-color:aquamarine">LESSON 24. TCP์ ๊ตฌ์กฐ</span>

### 1) TCP(Transmission Control Protocol, ์ ์ก ์ ์ด ํ๋กํ ์ฝ)๋?

**TCP**: ์ ์ก ๊ณ์ธต์์ <u>์ ๋ขฐํ  ์ ์๋ ์ ํํ ํต์ ์ ์ ๊ณต</u>ํ๋, <span style="color:Teal">**์ ๋ขฐ์ฑ/์ ํ์ฑ**</span>์ด ์ฐ์ ์ธ **์ฐ๊ฒฐํ ํต์  ํ๋กํ ์ฝ**์ธ <span style="color:Teal">**TCP**</span>

![](https://images.velog.io/images/april_5/post/72461312-7b0f-4d05-a8ab-89c55da1f793/image.png)

- **์ธ๊ทธ๋จผํธ(segment)**: TCP ํค๋๊ฐ ๋ถ์ ๋ฐ์ดํฐ

- **TCP ํค๋**: TCP๋ก ์ ์กํ  ๋ ๋ถํ๋ ํค๋. <u>๋ชฉ์ ์ง๊น์ง ๋ฐ์ดํฐ๋ฅผ ์ ๋๋ก ์ ์กํ๊ธฐ ์ํด ํ์ํ ์ ๋ณด</u>๊ฐ ์๋ค

![](https://images.velog.io/images/april_5/post/5441b02c-56f9-49c3-9f77-dd0cb1b72939/image.png)

๋ฐ์ดํฐ๋ฅผ ์ ์กํ๊ธฐ ์ ์ <span style="background-color:yellow">์ฐ๊ฒฐ(connection)</span>์ด๋ผ๋ <span style="color:Teal">**๊ฐ์์ ๋์  ํต์ ๋ก**</span> ํ๋ณด ์์์ ํด์ผํ๋๋ฐ, ์ด ์ฐ๊ฒฐ์ ํ๋ฆฝํ ํ ๋ฐ์ดํฐ๋ฅผ ์ ์กํ  ์ ์๋ค

> **์ฐ๊ฒฐ(connection)**: TCP ํต์ ์์ ์ ๋ณด๋ฅผ ์ ๋ฌํ๊ธฐ ์ํด ์ฌ์ฉ๋๋ ๊ฐ์ฅ์ ํต์ ๋ก๋ก, ์ฐ๊ฒฐ์ ํ๋ฆฝํ๊ณ  ๋ฐ์ดํฐ๋ฅผ ์ ์กํ๋ค

TCP ํค๋์๋ <span style="color:Teal">**์ฝ๋ ๋นํธ**</span>๋ผ๋ ๋ถ๋ถ์ด ์๋๋ฐ, ์ฝ๋ ๋นํธ๋ TCP ํค๋์ <u>์ฐ๊ฒฐ ์ ์ด ์ ๋ณด๊ฐ ๊ธฐ๋ก๋๋ ๊ณณ</u>์ด๋ค

์ด๊ธฐ๊ฐ์ <span style="color:Teal">**0**</span>์ด๊ณ , ์ฐ๊ฒฐ์ ํ๋ฆฝํ๋ ค๋ฉด <span style="color:Teal">**SYN(์ฐ๊ฒฐ ์์ฒญ)**</span>๊ณผ <span style="color:Teal">**ACK(ํ์ธ ์๋ต)**</span>๊ฐ ํ์ํ๋ค

![](https://images.velog.io/images/april_5/post/09a200cf-9d36-449d-a250-fa1bcf5f2387/image.png)

<br />

### 2) 3-way ํธ๋์ฐ์ดํฌ(three-way handshake)๋?

<span style="background-color:yellow">์ฐ๊ฒฐ(connection)</span>์ <span style="color:Teal">**SYN(์ฐ๊ฒฐ ์์ฒญ)**</span>๊ณผ <span style="color:Teal">**ACK(ํ์ธ ์๋ต)**</span>๋ฅผ ์ฌ์ฉํ์ฌ ํ๋ฆฝ ํ  ์ ์๊ณ 
์ ๋ขฐํ  ์ ์๋ ์ฐ๊ฒฐ์ ํ๋ ค๋ฉด ๋ฐ์ดํฐ๋ฅผ ์ ์กํ๊ธฐ ์ ์ ํจํท ๊ตํ์ ์ธ ๋ฒ(three-way handshake) ํ์ธ ํ๋ค

> <span style="color:Teal">**3-WAY ํธ๋์ฐ์ดํฌ(three-way handshake)**</span>: ๋ฐ์ดํฐ๋ฅผ ๋ณด๋ด๊ธฐ ์ ์ ์ฐ๊ฒฐ์ ํ๋ฆฝํ๊ธฐ ์ํด ํจํท ์์ฒญ์ ์ธ๋ฒ ๊ตํํ๋ ๊ฒ์ ์๋ฏธ. <br /> **ํธ๋์ฐ์ดํฌ**๋ ์ฌ๋๋ค์ด ์๋๋ฐฉ์ ํ์ธํ๊ณ  ์์๋ฅผ ํ๋ ๊ฒ์ฒ๋ผ <u>๋ฐ์ดํฐ ํต์ ์์๋ ํ์คํ๊ฒ ๋ฐ์ดํฐ๊ฐ ์ ์ก๋์๋์ง ํ์ธํ๋ฉด์ ์ด๋ฃจ์ด์ง๋ ํต์  ์๋จ</u>์ด๋ค.

![](https://images.velog.io/images/april_5/post/4c4f039f-64a0-4088-91f2-2caa4aa64adf/3-way%20%E1%84%92%E1%85%A2%E1%86%AB%E1%84%83%E1%85%B3%E1%84%89%E1%85%A8%E1%84%8B%E1%85%B5%E1%84%8F%E1%85%B3.jpeg)

โ  ํต์ ์ ํ๋ ค๋ฉด ์๋ฒ์๊ฒ ํ๊ฐ๋ฅผ ๋ฐ์์ผ ํ๋ฏ๋ก, ๋จผ์  ํด๋ผ์ด์ธํธ์์ ์๋ฒ๋ก ์ฐ๊ฒฐ ํ๋ฆฝ ํ๊ฐ๋ฅผ ๋ฐ๊ธฐ ์ํ ์์ฒญ(SYN)์ ๋ณด๋ธ๋ค. <br />
โก ์๋ฒ๋ ํด๋ผ์ด์ธํธ๊ฐ ๋ณด๋ธ ์์ฒญ์ ๋ฐ์ ํ์ ํ๊ฐํ๋ค๋ ์๋ต์ ํ์ ํ๊ธฐ ์ํด ์ฐ๊ฒฐ ํ๋ฆฝ ์๋ต(ACK)์ ๋ณด๋ธ๋ค. ๋์์ ์๋ฒ๋ ํด๋ผ์ด์ธํธ์๊ฒ ๋ฐ์ดํฐ ์ ์ก ํ๊ฐ๋ฅผ ๋ฐ๊ธฐ ์ํด ์ฐ๊ฒฐ ํ๋ฆฝ ์์ฒญ(SYN)๋ฅผ ๋ณด๋ธ๋ค. <br />
โข ์๋ฒ์ ์์ฒญ์ ๋ฐ์ ํด๋ผ์ด์ธํธ๋ ์๋ฒ๋ก ํ๊ฐํ๋ค๋ ์๋ต์ผ๋ก ์ฐ๊ฒฐ ํ๋ฆฝ ์๋ต(ACK)๋ฅผ ๋ณด๋ธ๋ค.

<br /><br />

๋ฐ์ดํฐ๋ฅผ ์ ์กํ  ๋๋ฟ๋ง ์๋๋ผ ์ ์กํ ํ์๋ <u>์ฐ๊ฒฐ์ ๋๊ธฐ ์ํ ์์ฒญ</u>์ ๊ตํํด์ผ ํ๋ค.
์ฐ๊ฒฐ์ ๋์ ๋๋ <span style="color:Teal">**FIN(์ฐ๊ฒฐ ์ข๋ฃ)**</span>๊ณผ <span style="color:Teal">**ACK(ํ์ธ ์๋ต)**</span>๋ฅผ ์ฌ์ฉํ๋ค

![](https://images.velog.io/images/april_5/post/3cfa9f72-7464-44d0-a44b-4d88ea13f5e6/image.png)

โ  ์ปดํจํฐ 1์์ ์ปดํจํฐ 2๋ก ์ฐ๊ฒฐ ์ข๋ฃ ์์ฒญ(FIN)์ ๋ณด๋ธ๋ค. <br />
โก ์ปดํจํฐ 2์์ ์ปดํจํฐ 1๋ก ์ฐ๊ฒฐ ์ข๋ฃ ์๋ต(ACK)๋ฅผ ๋ฐํํ๋ค. <br />
โข ๋ํ ์ปดํจํฐ 2์์๋ ์ปดํจํฐ 1๋ก ์ฐ๊ฒฐ ์ข๋ฃ ์์ฒญ(FIN)์ ๋ณด๋ธ๋ค. <br />
โฃ ์ปดํจํฐ 1์์ ์ปดํจํฐ 2๋ก ์ฐ๊ฒฐ ์ข๋ฃ ์๋ต(ACK)์ ๋ฐํํ๋ค. <br />

<br />

---

## <span style="background-color:aquamarine">LESSON 25. ์ผ๋ จ๋ฒํธ์ ํ์ธ ์๋ต ๋ฒํธ์ ๊ตฌ์กฐ</span>

### 1) ์ผ๋ จ๋ฒํธ์ ํ์ธ ์๋ต ๋ฒํธ๋?

3-way ํธ๋์ฐ์ดํฌ๊ฐ ๋๋๊ณ  <u>์ค์  ๋ฐ์ดํฐ๋ฅผ ๋ณด๋ด๊ฑฐ๋ ์๋๋ฐฉ์ด ๋ฐ์ ๋</u>๋
**TCP ํค๋**์ <span style="color:Teal">**์ผ๋ จ ๋ฒํธ(sequence number)**</span>์ <span style="color:Teal">**ํ์ธ ์๋ต ๋ฒํธ(acknowledgement number)**</span>๋ฅผ ์ฌ์ฉํ๋ค.

![](https://images.velog.io/images/april_5/post/eaf3003a-5bc8-4353-88bf-3b3b95a8c961/image.png)

<span style="color:Teal">**TCP**</span>๋ ๋ฐ์ดํฐ๋ฅผ ๋ถํ ํด์ ๋ณด๋ด๋๋ฐ

- <span style="color:Teal">**์ผ๋ จ๋ฒํธ**</span>๋ ์ก์  ์ธก์์ **์์  ์ธก์** <u>_์ด ๋ฐ์ดํฐ๊ฐ ๋ช ๋ฒ์งธ ๋ฐ์ดํฐ์ธ์ง_</u> ์๋ ค ์ฃผ๋ ์ญํ ์ ํ๋ค.

  - ์ ์ก๋ ๋ฐ์ดํฐ์ ์ผ๋ จ๋ฒํธ๋ฅผ ๋ถ์ฌํ๋ฉด ์์ ์๋ ์๋ ๋ฐ์ดํฐ์ ๋ช ๋ฒ์งธ ๋ฐ์ดํฐ๋ฅผ ๋ฐ์๋์ง ์ ์ ์๋ค.

- <span style="color:Teal">**ํ์ธ ์๋ต ๋ฒํธ**</span>๋ ์์  ์ธก์ด <u>_๋ช ๋ฒ์งธ ๋ฐ์ดํฐ๋ฅผ ์์ ํ๋์ง_</u> **์ก์  ์ธก์** ์๋ ค์ฃผ๋ ์ญํ ์ ํ๋ค.
  - ๊ทธ๋์ ์ด ๋ฒํธ๋ ๋ค์ ๋ฒํธ์ ๋ฐ์ดํฐ๋ฅผ ์์ฒญํ๋๋ฐ๋ ์ฌ์ฉํ๋ค.

<br />

๋ฐ์ดํฐ๊ฐ ํญ์ ์ฌ๋ฐ๋ฅด๊ฒ ์ ๋ฌ๋๋ ๊ฒ์ ์๋๋ฏ๋ก
<u>์ผ๋ จ๋ฒํธ์ ํ์ธ ์๋ต ๋ฒํธ๋ฅผ ์ฌ์ฉํด์ ๋ฐ์ดํฐ๊ฐ ์์๋๊ฑฐ๋ ์ ์ค๋ ๊ฒฝ์ฐ์ ๋ฐ์ดํฐ๋ฅผ ์ฌ์ ์ก</u>ํ๊ฒ ๋์ด์๋ค. ์ด๊ฒ์ <span style="color:Teal">**์ฌ์ ์ก ์ ์ด**</span>๋ผ๊ณ  ํ๋ค.

<br />

### 1) ์๋์ฐ ํฌ๊ธฐ๋?

> **์๋์ฐ ํฌ๊ธฐ**: ๋ฒํผ(์๋๋ฐฉ์๊ฒ ์์ธ ์ธ๊ทธ๋จผํธ๋ฅผ ์ผ์์ ์ผ๋ก ๋ณด๊ดํ๋ ์ฅ์) ์ฉ๋์ ํฌ๊ธฐ

**TCP์ ํน์ง**์ <span style="color:Teal">**์ธ๊ทธ๋จผํธ(๋ฐ์ดํฐ)**</span> <u>ํ๋๋ฅผ ๋ณด๋ผ ๋๋ง๋ค ํ์ธ ์๋ต์ ํ ๋ฒ ๋ฐํ</u>ํ๋ ํต์ ์ธ๋ฐ, ํ ๋ฒ ๋ณด๋ผ ๋๋ง๋ค ํ ๋ฒ ์๋ต์ ๋ฐํํ๋ ๋ฐฉ์์ด์ด์ <u>ํจ์จ์ด ๋ฎ๋ค</u>

ํ์ง๋ง, ๋งค๋ฒ ํ์ธ ์๋ต์ ๊ธฐ๋ค๋ฆฌ๋ ๋์  <u>์ธ๊ทธ๋จผํธ๋ฅผ ์ฐ์ํด์ ๋ณด๋ด๊ณ  ๋ ๋ค์์ ํ์ธ ์๋ต์ ๋ฐํํ๋ฉด ํจ์จ์ด ๋์์ง</u>์ง๋ง ์๋๋ฐฉ์๋ ์ธ๊ทธ๋จผํธ๊ฐ ์ ์  ์์ด๊ฒ ๋๋ค.
์๋๋ฐฉ์๊ฒ ์์ธ ์ธ๊ทธ๋จผํธ๋ <span style="color:Teal">**๋ฒํผ(buffer)**</span>๋ผ๋ ์ฅ์์ ์ผ์์ ์ผ๋ก ๋ณด๊ดํ๋ค.

- ๋ฒํผ(buffer) ๋๋ถ์ ์ธ๊ทธ๋จผํธ๋ฅผ ์ฐ์ํด์ ๋ณด๋ด๋ ์์  ์ธก์ ๋์ํ  ์ ์๊ณ  ํจ์จ๋ ๋์์ง๋ค
- ํ์ง๋ง ์์  ์ธก์ ๋๋์ผ๋ก ๋ฐ์ดํฐ๊ฐ ์ ์ก๋๋ฉด ๋ณด๊ดํ์ง ๋ชปํ๊ณ  ๋์ณ ๋ฒ๋ฆฌ๋ ๊ฒฝ์ฐ๋ฅผ <span style="color:Teal">**์ค๋ฒํ๋ก(overflow)**</span>๋ผ๊ณ  ํ๋ค.

์ค๋ฒํ๋ก๊ฐ ๋ฐ์ํ์ง ์๋๋ก <span style="color:Teal">**๋ฒํผ์ ํ๊ณ ํฌ๊ธฐ**</span>๋ฅผ ์๊ณ  ์์ด์ผ ํ๋ค. ๊ทธ๊ฒ์ด **TCP ํค๋**์ <span style="color:Teal">**์๋์ฐ ํฌ๊ธฐ(window size)**</span> ๊ฐ์ ํด๋นํ๋ค.

![](https://images.velog.io/images/april_5/post/8cf4d509-af79-49fb-bac5-d85e7c705b1d/image.png)

> **์๋์ฐ ํฌ๊ธฐ**: <span style="color:Teal">**์ผ๋ง๋ ๋ง์ ์ฉ๋์ ๋ฐ์ดํฐ๋ฅผ ์ ์ฅํด ๋ ์ ์๋์ง**</span>๋ฅผ ๋ํ๋ธ๋ค. ์ฆ, ํ์ธ ์๋ต์ ์ผ์ผ์ด ํ์ง ์๊ณ  ์ฐ์ํด์ ์ก์์ ํ  ์ ์๋ ๋ฐ์ดํฐ ํฌ๊ธฐ๋ค.

<br />

---

## <span style="background-color:aquamarine">LESSON 26. ํฌํธ ๋ฒํธ(port number)์ ๊ตฌ์กฐ</span>

### 1) ํฌํธ ๋ฒํธ(port number)๋?

> **ํฌํธ ๋ฒํธ**: ์ด๋ค ์ ํ๋ฆฌ์ผ์ด์์ธ์ง ๊ตฌ๋ถํ๋ ์ญํ 

![](https://images.velog.io/images/april_5/post/4ed21bea-2be9-4c64-8ae1-c2a42dcc0ab6/image.png)

์ ์ก ๊ณ์ธต์ ์ญํ  ์ค ์ ์ก๋ ๋ฐ์ดํฐ์ ๋ชฉ์ ์ง๊ฐ ์ด๋ค ์ ํ๋ฆฌ์ผ์ด์(์น ๋ธ๋ผ์ฐ์ ๋ ๋ฉ์ผ ํ๋ก๊ทธ๋จ ๋ฑ)์ธ์ง ๊ตฌ๋ถํ๋ ์ญํ ์ ํ๊ธฐ ์ํด์ 
**TCP ํค๋**์ <span style="color:Teal">**์ถ๋ฐ์ง ํฌํธ ์ฃผ์**</span>(source port number)์ <span style="color:Teal">**๋ชฉ์ ์ง ํฌํธ ์ฃผ์**</span>(destination port number)๊ฐ ํ์ํ๋ค. TCP ํค๋์ ํฌํธ ๋ฒํธ๊ฐ ์๊ธฐ ๋๋ฌธ์ ์ ํ๋ฆฌ์ผ์ด์์ ๊ตฌ๋ถํ  ์ ์๊ฒ ๋๋ค.

ํฌํธ ๋ฒํธ๋ `0 ~ 65535๋ฒ` ๊น์ง ์ฌ์ฉํ  ์ ์๊ณ , ํฌ๊ฒ ์ธ ์ข๋ฅ๋ก ๊ตฌ๋ถ๋๋ค.

| ํฌํธ ์ข๋ฅ                        | ๋ฒ์              | ์ค๋ช                                                                                                                   |
| -------------------------------- | ----------------- | ---------------------------------------------------------------------------------------------------------------------- |
| ์ ์๋ ค์ง ํฌํธ (well-known port) | 0๋ฒ ~ 1023๋ฒ      | ์ฃผ์ ํ๋กํ ์ฝ์ด ์ฌ์ฉํ๋๋ก ์์ฝ๋์ด ์์ <br /> ์ผ๋ฐ์ ์ผ๋ก ์๋ฒ ์ธก ์ ํ๋ฆฌ์ผ์ด์์์ ์ฌ์ฉ                               |
| ๋ฑ๋ก๋ ํฌํธ (registered port)    | 1024๋ฒ ~ 49151๋ฒ  | - 1024๋ฒ: ์์ฝ๋์ด ์์ง๋ง ์ฌ์ฉ๋์ง๋ ์๋ ํฌํธ <br /> - 1025 ์ด์: ๋๋ค ํฌํธ๋ผ๊ณ  ํ๊ณ  ํด๋ผ์ด์ธํธ ์ธก์ ์ก์  ํฌํธ๋ก ์ฌ์ฉ |
| ๋์  ํฌํธ (dynamic port)         | 49152๋ฒ ~ 65535๋ฒ |

![](https://images.velog.io/images/april_5/post/95114df5-0776-41ec-93f1-fec0a936a0c5/image.png)

| ์ ํ๋ฆฌ์ผ์ด์ | ํฌํธ ๋ฒํธ |
| ------------ | --------- |
| SSH          | 22        |
| SMTP         | 25        |
| DNS          | 53        |
| HTTP         | 80        |
| POP3         | 110       |
| HTTPS        | 443       |

์ด์ฒ๋ผ ๋์ํ๋ ์ ํ๋ฆฌ์ผ์ด์์ ๊ฐ๊ฐ ํฌํธ ๋ฒํธ๊ฐ ์์ด์ ๋ค๋ฅธ ์ ํ๋ฆฌ์ผ์ด์๊ณผ ์๋ก ๊ตฌ๋ถ๋๋ค.
<u>๋ฐ์ดํฐ๋ฅผ ์ ์กํ  ๋๋ ์๋๋ฐฉ์ **IP ์ฃผ์**๊ฐ ํ์</u>ํ์ง๋ง,
<u>์ด๋ค ์ ํ๋ฆฌ์ผ์ด์์ด ์ฌ์ฉ๋๊ณ  ์๋์ง ๊ตฌ๋ถํ๋ ค๋ฉด **TCP๋ ํฌํธ ๋ฒํธ**</u>๊ฐ ํ์ํ๋ค.

<br />

---

## <span style="background-color:aquamarine">LESSON 27. UDP(User Datagram Protocol)์ ๊ตฌ์กฐ</span>

### 1) UDP(User Datagram Protocol)๋?

> **UDP**: ์ฌ์ฉ์ ๋ค์ด์ด๊ทธ๋จ ํ๋กํ ์ฝ. ์ ์ก ๊ณ์ธต์์ ๋ฐ์ดํฐ๋ฅผ ํจ์จ์ ์ด๊ณ  ๋น ๋ฅด๊ฒ ๋ณด๋ผ ๋ ์ฌ์ฉ๋๋ ํ๋กํ ์ฝ

UDP๋ <span style="color:Teal">**๋น์ฐ๊ฒฐํ ํต์ **</span>์ด๋ผ์ ๋ฐ์ดํฐ๋ฅผ ์ ์กํ  ๋ TCP์ฒ๋ผ ์๊ฐ์ด ๊ฑธ๋ฆฌ๋ ํ์ธ ์์์ ์ผ์ผ์ด ํ์ง ์๋๋ค.

UDP๋ TCP์ ๋ฌ๋ฆฌ <span style="color:Teal">**ํจ์จ์ฑ</span>์ ์ค์ํ๊ฒ ์ฌ๊ธฐ๋ ํ๋กํ ์ฝ** ์ด๋ผ TCP์ ๊ฐ์ ์ ๋ขฐ์ฑ๊ณผ ์ ํ์ฑ์ ์๊ตฌํ๊ฒ ๋๋ฉด ํจ์จ์ด ๋จ์ด์ง๋ค.

**UDP์ ์ฅ์ **์ <u>๋ฐ์ดํฐ๋ฅผ ํจ์จ์ ์ผ๋ก ๋น ๋ฅด๊ฒ ๋ณด๋ด๋ ๊ฒ</u>์ด๋ผ์ ์คํธ๋ฆฌ๋ฐ ๋ฐฉ์์ผ๋ก ์ ์กํ๋ ๋์์ ์๋น์ค์ ๊ฐ์ ๊ณณ์ ์ฌ์ฉ๋๋ค.

- ๋์์์ TCP ๋ฐ์ดํฐ ํต์ ์ผ๋ก ์ ์กํ๋ฉด ์์ ์ ํ์ธํ๋๋ฐ ์๊ฐ์ด ๋๋ฌด ์ค๋ ๊ฑธ๋ ค์ ๋์์์ ์ํ ํ๊ฒ ๋ณผ ์ ์๋ค. ๊ทธ๋์ ๋์์ ๊ฐ์ ๊ฑด ๋๊ฐ ๋น ๋ฅธ UDP๋ฅผ ์ฌ์ฉํ๋ค.

<br />

### 2) UDP ํค๋๋?

UDP ์์๋ <span style="color:Teal">**UDP ํค๋**</span>๊ฐ ๋ถ์ ๋ฐ์ดํฐ๋ฅผ <span style="color:Teal">**UDP ๋ฐ์ดํฐ ๊ทธ๋จ**</span>์ด๋ผ๊ณ  ํ๋ค.

![](https://images.velog.io/images/april_5/post/4b991034-4eb5-4da1-ad5c-f827fc1276c8/image.png)

- TCP์ UDP ์ฐจ์ด

![](https://images.velog.io/images/april_5/post/287837cf-4eb8-49ba-a71d-daa59c24a3e7/image.png)

- TCP๋ ๋ฒ๊ฑฐ๋กญ๊ฒ ์ฌ๋ฌ ๋ฒ ํ์ธ ์๋ต์ ๋ณด๋ด๋ฉด์ ์ ์กํ์ง๋ง,
- UDP๋ ํจ์จ์ฑ๊ณผ ๋น ๋ฅธ ์๋๊ฐ ์ค์ํด์ ์๋๋ฐฉ์ ํ์ธํ์ง ์๊ณ  ์ฐ์ํด๋ ๋ฐ์ดํฐ๋ฅผ ๋ณด๋ธ๋ค.
  - ๋ํ UDP๋ฅผ ์ฌ์ฉํ๋ฉด <u>๋์ ์๋ ์ปดํจํฐ๋ ๋คํธ์ํฌ ์ฅ๋น์ ๋ฐ์ดํฐ๋ฅผ ์ผ๊ด๋ก ๋ณด๋ผ ์ ์๋ค</u>. ์ด๊ฒ์ <span style="color:Teal">**๋ธ๋ก๋์บ์คํธ**</span>๋ผ๊ณ  ํ๋ค.

![](https://images.velog.io/images/april_5/post/4aafe7bb-8937-468f-aa02-46fe083d4347/image.png)

<br /><br />

---

### :: ์ฉ์ด ์ ๋ฆฌ๐ก

- `์ ์ก ๊ณ์ธต(transport layer, ํธ๋์คํฌํธ ๊ณ์ธต)`: ์ ๋ขฐํ  ์ ์๋ ๋ฐ์ดํฐ๋ฅผ ์์ฐจ์ ์ผ๋ก ์ ๋ฌํ๋ ์ญํ ์ ํ๋ฏ๋ก ์์ ๊ณ์ธต๋ค์ด ๋ฐ์ดํฐ ์ ๋ฌ์ ์ ํจ์ฑ์ด๋ ํจ์จ์ฑ์ ์ ๊ฒฝ ์ฐ์ง ์๋๋ก ํ๋ค. ๋ฐ์ดํฐ๊ฐ ์ค๋ณต๋๊ฑฐ๋ ๋๋ฝ๋์ง ์๊ณ  ์ค๋ฅ ์์ด ์์์ ๋ง๊ฒ ์ ์ก๋๋๋ก ๊ด๋ฆฌํ๋ค.

- `์ฐ๊ฒฐํ(connection-oriented)`: ๋ฐ์ดํฐ๋ฅผ ๊ตํํ๊ธฐ ์ ์ ์ฐ๊ฒฐ์ ๋งบ๊ณ  ๋ฐ์ดํฐ๋ฅผ ๊ตํํ๋ ๋์ ๊ณ์ ์ฐ๊ฒฐ์ ๊ด๋ฆฌํ๋ ํ๋กํ ์ฝ์ ํ ํํ๋ค.

- `๋น์ฐ๊ฒฐํ(connectionless)`: ์ฐ๊ฒฐ(connection)์ ๋ํ ์ด๊ธฐํ ๊ณผ์ ์ด ์๋ ํต์ ์ด๋ค.

- `TCP(Transmission Control Protocol, ์ ์ก ์ ์ด ํ๋กํ ์ฝ)`: ์ ์ก ๊ณ์ธต์ ํ๋กํ ์ฝ์ ์ฐ๊ฒฐํ(connection-oriented) ํต์  ๋ฐฉ์์ด๋ฉฐ ์ ๋ขฐํ  ์ ์๋ ๋ฐ์ดํฐ ์ ์ก์ ๋ณด์ฅํ๋ค.

- `๋์ญํญ(bandwidth)`: ์ ํด์ง ์๊ฐ ๋์ ์ ์ก๋  ์ ์๋ ๋ฐ์ดํฐ์ ์(์ฃผ๋ก ์๋๋ฅผ ์๋ฏธํ๋ค)์ ๋งํ๋ค. ๋์ญํญ์ ์ ํ์ ์ด๋ค.

- `UDP(User Datagram Protocol)`: ์ ๋ณด๋ฅผ ์๋ก ์ฃผ๊ณ ๋ฐ์ ๋ ๋ณด๋ด๋ ์ชฝ์์ ์ผ๋ฐฉ์ ์ผ๋ก ๋ฐ์ดํฐ๋ฅผ ์ ๋ฌํ๋ ํต์  ํ๋กํ ์ฝ์ด๋ค. ์ฐ๊ฒฐ์ ๋งบ์ ํ์๊ฐ ์๊ณ  ์ ๋ณด๋ฅผ ๋ณด๋ด๊ฑฐ๋ ๋ฐ๋๋ค๋ ์ ํธ๋ ํ์ํ์ง ์๋ค.

- `3-way ํธ๋์ฐ์ดํธ(three-way handshake)`: TCP ํต์ ์์ ์ฌ์ฉํ๋ ์ ๋ขฐ์ฑ์ ์ ๊ณตํ๊ธฐ ์ํ ํต์  ๋ฐฉ์์ด๋ค. ์ปดํจํฐ ๊ฐ์ ์ฐ๊ฒฐ์ ๋งบ๊ธฐ ์ํ ์ด๊ธฐํ ๊ณผ์ ์ผ๋ก ์ธ ๋จ๊ณ๋ก ๋์ด ์์ด์ three-way๋ผ๊ณ  ๋ถ๋ฅธ๋ค.

- `์ ์๋ ค์ง ํฌํธ(well-known ports)`: ํน์  ์ ํ๋ฆฌ์ผ์ด์์ด ์ฌ์ฉํ  ์ ์๋๋ก ์์ฝ๋์ด ์๋ ํฌํธ๋ก 1~1023๋ฒ ํฌํธ๋ฅผ ๋งํ๋ค.

- `๋ธ๋ก๋์บ์คํธ(broadcast)`: ๋คํธ์ํฌ์ ๋ชจ๋  ์ปดํจํฐ์ ์ฅ๋น์ ๊ฐ์ ํจํท์ ์ผ๊ด ์ ์กํ๋ ๋ฐฉ์์ด๋ค.

- `์ผ๋ จ๋ฒํธ(sequence number)`: TCP์์๋ ๋ฐ์ดํฐ๋ฅผ ๋ณด๋ผ ๋๋ง๋ค ๊ฐ ๋ฐ์ดํฐ์ ๊ณ ์ ํ ๋ฒํธ๋ฅผ ๋ถ์ฌํด์ ์ ์ก์ ์๋ํ๋ค. ์ด ๋ฒํธ๋ฅผ ์ด์ฉํ์ฌ TCP ํจํท์ ์์๋ฅผ ์ ์ดํ  ์ ์๋ค.

- `ํฌํธ ๋ฒํธ(port number)`: ์ปดํจํฐ๊ฐ ๋ฐ์ดํฐ ํต์ ์ ํ  ๋ ํตํ๊ณ ์ ํ๋ ๋คํธ์ํฌ ์๋น์ค๋ ํน์  ํ๋ก์ธ์ค๋ฅผ ์๋ณํ๋ ๋ธ๋ฆฌ ๋จ์๋ค. ํฌํธ ๋ฒํธ๋ 0~65535๋ฒ์ ์ฌ์ฉํ  ์ ์๋ค. 0~1023๋ฒ์ ์ ์๋ ค์ง ํฌํธ(well-known ports)๋ก ํน์  ์ ํ๋ฆฌ์ผ์ด์์ด ์ฌ์ฉํ  ์ ์๋๋ก ์์ฝ๋ ๋ฒํธ๋ค.
