---
title: "๐ ๋คํธ์ํฌ ๊ตฌ์กฐ ์ดํด:: OSI๋ชจ๋ธ์ ๋ฐ์ดํฐ ๋งํฌ ๊ณ์ธต"
tags:
  - [network]
permalink: /network/data_link_layer

navigation: true
toc: true
toc_sticky: true

date: 2021-10-30
last_modified_at: 2021-10-30
---

![]()

`๊ฐ์ธ ๊ณต๋ถ ๊ณผ์ ์ ๊ธฐ๋กํฉ๋๋ค.`

<span style="color:Teal">**OSI๋ชจ๋ธ**</span>์ 2๊ณ์ธต์ธ <span style="color:Teal">**๋ฐ์ดํฐ ๋งํฌ ๊ณ์ธต**</span>์ ๋ํด ๊ณต๋ถํ๊ธฐ

---

# ๐ ๋ฐ์ดํฐ ๋งํฌ ๊ณ์ธต:: ๋์์ ๋ฐ์ดํฐ ์ ์กํ๊ธฐ

### ๐ What I Will Learn

- ์ด๋๋ท(Ethernet)์ ์ดํดํ๋ค
- CSMA/CD๋ฐฉ์์ ์ดํดํ๋ค
- MAC ์ฃผ์๋ฅผ ์ดํดํ๋ค
- ์ค์์น๋ฅผ ์ดํดํ๋ค
- ์ถฉ๋ ๋๋ฉ์ธ์ ์ดํดํ๋ค
- ์ด๋๋ท ํ์ค์ ์ดํดํ๋ค

---

## <span style="background-color:aquamarine">LESSON 12. ๋ฐ์ดํฐ ๋งํฌ ๊ณ์ธต์ ์ญํ ๊ณผ ์ด๋๋ท</span>

๋์์๋ ๋ฐ์ดํฐ๋ฅผ ์ฃผ๊ณ ๋ฐ๋ ๊ท์น์ผ๋ก `์ด๋๋ท`์ ์ฌ์ฉ. ๊ทธ๋ผ **์ด๋๋ท(Ethernet)**์ด๋?

### 1) ์ด๋๋ท(Ethernet)์ด๋?

๋์์ ๋ฐ์ดํฐ๋ฅผ ์ฃผ๊ณ  ๋ฐ์ผ๋ ค๋ฉด, ๋ ๋ฒ์งธ ๊ณ์ธต์ธ <span style="color:Teal">**๋ฐ์ดํฐ ๋งํฌ ๊ณ์ธต**</span>์ ๊ธฐ์ ์ด ํ์.

![](https://images.velog.io/images/april_5/post/670938b8-0dd4-4530-b253-0df00b4f3c03/image.png)

> **๋ฐ์ดํฐ ๋งํฌ ๊ณ์ธต**: ๋คํธ์ํฌ ์ฅ๋น ๊ฐ์ ์ ํธ๋ฅผ ์ฃผ๊ณ ๋ฐ๋ ๊ท์น์ ์ ํ๋ ๊ณ์ธต.

๋์์ ๋ฐ์ดํฐ๋ฅผ ์ ์์ ์ผ๋ก ์ฃผ๊ณ ๋ฐ๊ธฐ ์ํด ํ์ํ ๊ณ์ธต์ด๋ค. ๊ทธ ๊ท์น๋ค ์ค ๊ฐ์ฅ ๋ง์ด ์ฌ์ฉ๋๋ ๊ท์น์ด **์ด๋๋ท(Ethernet)**

> **์ด๋๋ท(Ethernet)**: ๋์์ ์ ์ฉ๋๋ ๊ท์น. ํ๋ธ์ ๊ฐ์ ์ฅ๋น์ ์ฐ๊ฒฐ๋ ์ปดํจํฐ์ ๋ฐ์ดํฐ๋ฅผ ์ฃผ๊ณ ๋ฐ์ ๋ ์ฌ์ฉ.
>
> > **ํ๋ธ**: ์ฝํด์ง๊ฑฐ๋ ํํ์ด ๋ญ๊ทธ๋ฌ์ง ์ ๊ธฐ ์ ํธ๋ฅผ ๋ณต์์ํค๊ณ , ํด๋น ์ ๊ธฐ ์ ํธ๋ฅผ ์ ๋ฌ๋ฐ์ ํฌํธ๋ฅผ ์ ์ธํ ๋๋จธ์ง ํฌํธ์ ์ ๋ฌํ๋ ์ญํ ์ ํ๋ค. <br />
> > ๋๋ฏธ ํ๋ธ๋ผ๊ณ ๋ ๋ถ๋ฆฌ๋ ์ด์ ๋, ๋ค์ด์จ ๋ฐ์ดํฐ๋ฅผ ๊ทธ๋๋ก ๋ชจ๋  ํฌํธ์ ๋ณด๋ด๊ธฐ๋ง ํ๊ธฐ ๋๋ฌธ.

ํน์  ์ปดํจํฐ์๋ง ๋ฐ์ดํฐ๋ฅผ ๋ณด๋ด๋๋ฐ, ๊ด๊ณ ์๋ ๋ค๋ฅธ ์ปดํจํฐ๋ค์ด ๊ทธ ๋ฐ์ดํฐ๋ฅผ ๋ฐ์ ๋ณธ๋ค๋ฉด? ๐ฑ๐ฑ๐ฑ๐ฑ๐ฑ๐ฑ๐ฑ๐ฑ๐ฑ๐ฑ๐ฑ
์ด๋ฐ ๊ฒฝ์ฐ๋ฅผ ๋๋นํด์ *๋ค๋ฅธ ์ปดํจํฐ๋ ๋ฐ์ดํฐ๋ฅผ ๋ชป๋ณด๋๋ก ํ๋ ๊ท์น*์ด ์ ํด์ ธ ์๋ค

- ๊ทธ๋์ ๋ณด๋ด๋ ค๋ ๋ฐ์ดํฐ์ **๋ชฉ์ ์ง** ์ ๋ณด๋ฅผ ์ถ๊ฐํด์ ๋ณด๋ด๊ณ ,
- ๋ชฉ์ ์ง ์ด์ธ์ ์ปดํจํฐ๋ ๋ฐ์ดํฐ๋ฅผ ๋ฐ์๋ ๋ฌด์ํ๊ฒ ๋๋ค

๋ค๋ง, ์ปดํจํฐ ์ฌ๋ฌ ๋๊ฐ ๋์์ ๋ฐ์ดํฐ๋ฅผ ๋ณด๋ด๋ฉด ๋ฐ์ดํฐ๋ค์ด ์๋ก ๋ถ๋ชํ ์ ์๋๋ฐ ์ฆ ์ถฉ๋(collision)์ด ์ผ์ด๋  ์ ์๋๋ฐ

![](https://images.velog.io/images/april_5/post/5f2edf3a-b29c-4f58-a2aa-66f8b4e282d6/image.png)

<span style="background-color:yellow">์ด๋๋ท์ ์ฌ๋ฌ ์ปดํจํฐ๊ฐ ๋์์ ๋ฐ์ดํฐ๋ฅผ ์ ์กํด๋ ์ถฉ๋์ด ์ผ์ด๋์ง ์๋ ๊ตฌ์กฐ</span>๋ก ๋์ด์๋ค

- ๋ฐ์ดํฐ๊ฐ ๋์์ ์ผ์ด๋ธ์ ์ง๋๊ฐ๋ฉด ์ถฉ๋ํ  ์ ๋ฐ์ ์์ด์ ๋ฐ์ดํฐ๋ฅผ ๋ณด๋ด๋ ์์ ์ ๋ฆ์ถ๊ฒ ๋๋๋ฐ, ์ด๋๋ท์์ ์์ ์ ๋ฆ์ถ๋ ๋ฐฉ๋ฒ์ **CSMA/CD**๋ผ๊ณ  ํ๋ค

<br />

### 2) CSMA/CD์ด๋?

> **CSMA/CD**: Carrier Sense Multiple Access with Collision Detection์ ์ฝ์ด๋ก **๋ฐ์กํ ๊ฐ์ง ๋ค์ค ์ ์ ๋ฐ ์ถฉ๋ ํ์ง**๋ผ๋ ๋ป์ ๊ฐ์ง๋ค

CSMA/CD์์
<span style="color:Teal">**CS**</span>๋ `๋ฐ์ดํฐ๋ฅผ ๋ณด๋ด๋ ค๊ณ  ํ๋ ์ปดํจํฐ๊ฐ ์ผ์ด๋ธ์ ์ ํธ๊ฐ ํ๋ฅด๊ณ  ์๋์ง ์๋์ง๋ฅผ ํ์ธํ๋ค`๋ ๊ท์น
<span style="color:Teal">**MA**</span>๋ `์ผ์ด๋ธ์ ๋ฐ์ดํฐ๊ฐ ํ๋ฅด๊ณ  ์์ง ์๋ค๋ฉด ๋ฐ์ดํฐ๋ฅผ ๋ณด๋ด๋ ์ข๋ค`๋ผ๋ ๊ท์น
<span style="color:Teal">**CD**</span>๋ `์ถฉ๋์ด ๋ฐ์ํ๊ณ  ์๋์ง๋ฅผ ํ์ธํ๋ค`๋ ๊ท์น

์ด๋ฌํ ๊ท์น์ผ๋ก ๋ฐ์ดํฐ๋ฅผ ์ฃผ๊ณ ๋ฐ์ผ๋ฉด ์ถฉ๋์ด ์ผ์ด๋์ง ์๋๋ค

![](https://images.velog.io/images/april_5/post/f1b59d35-c811-44f7-9583-eee7337e63ab/image.png)

<span style="background-color:yellow">ํ์ง๋ง <span style="color:tomato">์ง๊ธ์ ํจ์จ์ด ์ข์ง ์๋ค๋ ์ด์ ๋ก CSMA/CD๋ ๊ฑฐ์ ์ฌ์ฉํ์ง ์๊ณ </span>
**์ค์์น(switch)**๋ผ๋ ๋คํธ์ํฌ ์ฅ๋น๋ฅผ ์ฌ์ฉํ์ฌ ์ถฉ๋์ ๋ง๋๋ค</span>

<br /><br />

---

## <span style="background-color:aquamarine">LESSON 13. MAC(Media Access Control Address) ์ฃผ์์ ๊ตฌ์กฐ</span>

๋ ์นด๋๋ฅผ ์ ์กฐํ  ๋ ์ ํด์ง๋ ๋ฌผ๋ฆฌ์ ์ธ ์ฃผ์์ ๋ํด ์์๋ณด์

### 1) MAC(Media Access Control Address) ์ฃผ์๋?

๋ ์นด๋๋ ๋นํธ์ด(0๊ณผ 1)์ ์ ๊ธฐ๋ก ๋ณํํ๋๋ฐ, ์ด๋ฐ ๋์นด๋์๋

- **MAC(Media Access Control Address) ์ฃผ์**๋ผ๋ ๋ฒํธ๊ฐ ์ ํด์ ธ ์๋ค.
- ์ ์กฐํ  ๋ ์๊ฒจ์ง๊ธฐ ๋๋ฌธ์ ๋ฌผ๋ฆฌ ์ฃผ์๋ผ๊ณ ๋ ๋ถ๋ฅด๋ฉฐ
- **์  ์ธ๊ณ์์ ์ ์ผํ ๋ฒํธ**๋ก ํ ๋น๋์ด ์๋ค

  - ์ค๋ณต๋์ง ์๋๋ก ๊ท์น๊น ๋ชํํ๊ฒ ์ ํด์ ธ ์๊ณ  48๋นํธ ์ซ์๋ก ๊ตฌ์ฑ๋์ด ์๋ค
  - ๊ทธ ์ค ์์ชฝ 24๋นํธ๋ ๋์นด๋๋ฅผ ๋ง๋๋ ์ ์กฐ์ฌ ๋ฒํธ
  - ๋ค์ชฝ 24๋นํธ๋ ์ ์กฐ์ฌ๊ฐ ๋์นด๋์ ๋ถ์ธ ์ผ๋ จ๋ฒํธ

  ![](https://images.velog.io/images/april_5/post/7dc1d245-1009-4936-b1f1-37d57b318a27/image.png)

### 2) MAC ์ฃผ์๋ฅผ ์ฌ์ฉํ ํต์ 

OSI ๋ชจ๋ธ์ด๋ TCP/IP ๋ชจ๋ธ์์๋ ๊ฐ ๊ณ์ธต์ ํค๋๋ฅผ ๋ถ์ธ๋ค

- OSI ๋ชจ๋ธ์ ๋ฐ์ดํฐ ๋งํฌ ๊ณ์ธต์ ํด๋น
- TCP/IP ๋ชจ๋ธ์์๋ ๋คํธ์ํฌ ๊ณ์ธต์ ํด๋น

![](https://images.velog.io/images/april_5/post/b7c1d0c8-c65e-44de-8d5a-c97cbf1b2053/image.png)

์ด ๊ณ์ธต์์ <span style="color:Teal">**์ด๋๋ท ํค๋**</span>์ <span style="color:Teal">**ํธ๋ ์ผ๋ฌ**</span>๋ฅผ ๋ถ์ธ๋ค
๊ทธ๋ฆฌ๊ณ  ์ด๋ ๊ฒ ์ด๋๋ท ํค๋์ ํธ๋ ์ผ๋ฌ๊ฐ ์ถ๊ฐ๋ ๋ฐ์ดํฐ๋ฅผ <span style="color:Teal">**ํ๋ ์**</span>์ด๋ผ๊ณ  ํ๋ค

์ด๋๋ท ํค๋๋ ์ด 14๋ฐ์ดํธ๋ก ๊ตฌ์ฑ๋์ด ์๋ค

- ๋ชฉ์ ์ง์ MAC ์ฃผ์(6๋ฐ์ดํธ)
- ์ถ๋ฐ์ง MAC ์ฃผ์(6๋ฐ์ดํธ)
- ์ ํ(2๋ฐ์ดํธ)

![](https://images.velog.io/images/april_5/post/912a9f25-ce96-41c7-996d-964c3b65a058/image.png)

**์ด๋๋ท ์ ํ(Ethernet type)**์ ์ด๋๋ท์ผ๋ก ์ ์ก๋๋ ์์ ๊ณ์ธต <span style="background-color:yellow">ํ๋กํ ์ฝ์ ์ข๋ฅ๋ฅผ ๋ํ๋ด๋๋ฐ, ์๋ณํ๋ 16์ง์ ๋ฒํธ</span>๊ฐ ๋ค์ด๊ฐ๋ค

| ์ ํ ๋ฒํธ | ํ๋กํ ์ฝ           |
| --------- | ------------------ |
| 0800      | IPv4               |
| 0806      | ARP                |
| 8035      | RARP               |
| 814C      | SNMP over Ethernet |
| 86DD      | IPv6               |

<br />

<span style="color:Teal">**ํธ๋ ์ผ๋ฌ**</span>๋ <span style="color:Teal">**FCS(Frame Check Sequence)**</span>๋ผ๊ณ ๋ ํ๋๋ฐ, ๋ฐ์ดํฐ ์ ์ก ๋์ค์ ์ค๋ฅ๊ฐ ๋ฐ์ํ๋์ง ํ์ธํ๋ ์ฉ๋๋ก ์ฌ์ฉํ๋ค

<br />

๋คํธ์ํฌ๋ฅผ ํตํด ํ๋ ์(์ด๋๋ท ํค๋์ ํธ๋ ์ผ๋ฌ๊ฐ ์ถ๊ฐ๋ ๋ฐ์ดํฐ)์ด ์ ์ก๋๋๋ฐ

- ์ด๋๋ท ํค๋์ ๋ฐ์ดํฐ์ ๋ชฉ์ ์ง์ธ ์ปดํจํฐ ์ฃผ์(<span style="color:Teal">**๋ชฉ์ ์ง MAC ์ฃผ์**</span>)์ ์์ ์ ์ฃผ์(<span style="color:Teal">**์ถ๋ฐ์ง MAC ์ฃผ์**</span>)๋ฅผ ๋ฃ๊ณ  ๋ฐ์ดํฐ๋ฅผ ์ ์ก โ ์ด๋ <span style="background-color:yellow">์บก์ํ</span>๊ฐ ์ผ์ด๋๋ค

> ๐์์ํ๋ฉด!! ๐ก๋ฐ์ดํฐ ๋งํฌ ๊ณ์ธต์์ ๋ฐ์ดํฐ์ ์ด๋๋ท ํค๋์ ํธ๋ ์ผ๋ฌ๋ฅผ ์ถ๊ฐํ์ฌ <span style="color:Teal">**ํ๋ ์**</span>์ ๋ง๋ค๊ณ , ๐ก๋ฌผ๋ฆฌ ๊ณ์ธต์์ ์ด ํ๋ ์ ๋นํธ์ด์ <span style="color:Teal">**์ ๊ธฐ ์ ํธ**</span>๋ก ๋ณํํ์ฌ ๋คํธ์ํฌ๋ฅผ ํตํด ์ ์ก

![](https://images.velog.io/images/april_5/post/7391c047-fd86-4177-a0b3-d79d57496276/image.png)

<br /><br />

---

## <span style="background-color:aquamarine">LESSON 14. ์ค์์น(switch)์ ๊ตฌ์กฐ</span>

์ค์์น(switch)๋ ํ๋ธ์ ๋ฌ๋ฆฌ ๋ฐ์ดํฐ ์ถฉ๋์ด ๋ฐ์ํ์ง ์๋๋ค. ๋คํธ์ํฌ ๊ตฌ์ฑ์์ ๋น ์ง ์ ์๋ ์ค์์น์ ๋ํด ์์๋ณด์.

### 1) MAC(Media Access Control Address) ์ฃผ์ ํ์ด๋ธ๋?

์ค์์น(switch)๋

- <span style="color:Teal">**๋ฐ์ดํฐ ๋งํฌ ๊ณ์ธต**</span>์์ ๋์ํ๊ณ 
- <span style="color:Teal">**๋ ์ด์ด 2 ์ค์์น**</span> ๋๋ <span style="color:Teal">**์ค์์นญ ํ๋ธ**</span>๋ผ๊ณ ๋ ๋ถ๋ฆฐ๋ค
- ์ฅ๋น ์ธํ์ ํ๋ธ์ ๋น์ทํ๋ค

์ค์์น ๋ด๋ถ์๋

- <span style="background-color:yellow">MAC ์ฃผ์ ํ์ด๋ธ(MAC address table)</span> ๋๋ ๋ธ๋ฆฌ์ง ํ์ด๋ธ (bridge table)์ด๋ผ๋ ๊ฒ์ด ์๊ณ 

MAC ์ฃผ์ ํ์ด๋ธ์

- ์ค์์น์ <span style="color:Teal">**ํฌํธ ๋ฒํธ**</span>์ ํด๋น ํฌํธ์ ์ฐ๊ฒฐ ๋์ด ์๋ ์ปดํจํฐ์ <span style="color:Teal">**MAC ์ฃผ์**</span>๊ฐ ๋ฑ๋ก๋๋ ๋ฐ์ดํฐ ๋ฒ ์ด์ค๋ค.

<br />

์ค์์น์ ์ ์์ ์ผฐ์๋

- MAC ์ฃผ์ ํ์ด๋ธ์๋ ์๋ฌด๊ฒ๋ ๋ฑ๋ก๋์ด ์์ง ์๊ณ 
- ์ปดํจํฐ์์ ๋ชฉ์ ์ง MAC ์ฃผ์๊ฐ ์ถ๊ฐ๋ ํ๋ ์์ด ์ ์ก๋๋ฉด MAC ์ฃผ์ ํ์ด๋ธ์ ํ์ธํ๊ณ 
- ์ถ๋ฐ์ง MAC ์ฃผ์๊ฐ ๋ฑ๋ก๋์ด ์์ง ์์ผ๋ฉด MAC ์ฃผ์๋ฅผ ํฌํธ์ ํจ๊ป ๋ฑ๋กํ๋ค

์ด๋ฐ ๊ธฐ๋ฅ์ **MAC ์ฃผ์ ํ์ต ๊ธฐ๋ฅ**์ด๋ผ๊ณ  ํ๊ณ , ๋๋ฏธ ํ๋ธ์๋ ์๋ ๊ธฐ๋ฅ์ด๋ค.

![](https://images.velog.io/images/april_5/post/bad17781-811a-440e-b04e-89baa0fbdffb/image.png)

์ค์์น๊ฐ ์์  ํฌํธ ์ด์ธ์ ๋ชจ๋  ํฌํธ์์ ๋ฐ์ดํฐ๋ฅผ ์ก์ ํ๋ ๊ฒ์ <span style="color:Teal">**ํ๋ฌ๋ฉ(flooding, ํ์)**</span>์ด๋ผ๊ณ  ํ๋ค.

์ค์์น์์ MAC ์ฃผ์๋ฅผ ๊ธฐ์ค์ผ๋ก ๋ชฉ์ ์ง๋ฅผ ์ ํํ๋ ๊ฒ์ <span style="color:Teal">**MAC ์ฃผ์ ํํฐ๋ง**</span>์ด๋ผ๊ณ  ํ๋ค.

<br /><br />

---

## <span style="background-color:aquamarine">LESSON 15. ๋ฐ์ดํฐ๊ฐ ์ผ์ด๋ธ์์ ์ถฉ๋ํ์ง ์๋ ๊ตฌ์กฐ</span>

์ผ์ด๋ธ์ ๋ฐ์ดํฐ๊ฐ ์๋ฌด๋ฆฌ ๋ง์ด ์ ์ก๋์ด๋ ๋ฐ์ดํฐ๊ฐ ์ถฉ๋ํ์ง ์๋ ๊ตฌ์กฐ ์ดํดํ๊ธฐ

### 1) ์ ์ด์ค ํต์ ๊ณผ ๋ฐ์ด์ค ํต์ 

- <span style="color:Teal">**์ ์ด์ค ํต์  ๋ฐฉ์**</span>์ ๋ฐ์ดํฐ์ ์ก์์ ์ ๋์์ ํต์ ํ๋ ๋ฐฉ์. ๋ฐ์ดํฐ๋ฅผ <span style="color:tomato">**๋์์ ์ ์กํด๋ ์ถฉ๋์ด ๋ฐ์ํ์ง ์๋๋ค**</span>

  - ์ปดํจํฐ๋ฅผ ๋ ๋๋ฅผ ๋ ์ผ์ด๋ธ์ ์ง์  ์ฐ๊ฒฐํ ๊ฒฝ์ฐ

![](https://images.velog.io/images/april_5/post/b0c91019-be1e-4e8c-83de-a520dc398281/image.png)

<br />

- <span style="color:Teal">**๋ฐ์ด์ค ํต์  ๋ฐฉ์**</span>์ ํ์  ํ๋๋ก ์ก์ ๊ณผ ์์ ์ ๋ฒ๊ฐ์๊ฐ๋ฉด์ ํต์ ํ๋ ๋ฐฉ์. ๋ฐ์ดํฐ๋ฅผ <span style="color:tomato">**๋์์ ์ ์กํ๋ฉด ์ถฉ๋์ด ๋ฐ์**</span>ํ๋ค.

  - ์ปดํจํฐ ๋ ๋๋ฅผ ํ๋ธ์ ์ฐ๊ฒฐํ ๊ฒฝ์ฐ

![](https://images.velog.io/images/april_5/post/147ec02c-e921-4fec-8c5c-d8dd663d4bf7/image.png)

<br />

- ์ค์์น๋ ์ถฉ๋์ด ์ผ์ด๋์ง ์๋ ๊ตฌ์กฐ๋ก ๋์ด ์๊ธฐ ๋๋ฌธ์ <span style="color:Teal">**์ ์ด์ค ํต์  ๋ฐฉ์**</span>์ผ๋ก๋ ๋ฐ์ดํฐ๋ฅผ ์ฃผ๊ณ  ๋ฐ์ ์ ์๋ค

  - ์ปดํจํฐ ๋ ๋๋ฅผ ์ค์์น์ ์ฐ๊ฒฐํ ๊ฒฝ์ฐ

  ![](https://images.velog.io/images/april_5/post/8f52d451-d7f0-4e92-89b0-29696bb114ee/image.png)

<br />

### 2) ์ถฉ๋ ๋๋ฉ์ธ(collsion domain)์ด๋?

**์ถฉ๋ ๋๋ฉ์ธ(collsion domain)**: ํ๋ธ๋ ๋ฐ์ด์ค ํต์  ๋ฐฉ์์ผ๋ก ๋์์ ๋ฐ์ดํฐ๋ฅผ ์ ์กํ๋ฉด ์ถฉ๋์ด ์ผ์ด๋๋๋ฐ, ์ถฉ๋์ด ๋ฐ์ํ  ๋ ๊ทธ ์ํฅ์ด ๋ฏธ์น๋ ๋ฒ์. ์ถฉ๋ ๋๋ฉ์ธ์ด ๋์์๋ก ๋คํธ์ํฌ๊ฐ ์ง์ฐ๋๋ค.

![](https://images.velog.io/images/april_5/post/dbf24684-d444-4c04-b002-21f0ed031ed4/image.png)

<br /><br />

---

## <span style="background-color:aquamarine">LESSON 16. ์ด๋๋ท์ ์ข๋ฅ์ ํน์ง</span>

์ผ์ด๋ธ์ ๋ฐ์ดํฐ๊ฐ ์๋ฌด๋ฆฌ ๋ง์ด ์ ์ก๋์ด๋ ๋ฐ์ดํฐ๊ฐ ์ถฉ๋ํ์ง ์๋ ๊ตฌ์กฐ ์ดํดํ๊ธฐ

### 1) ์ด๋๋ท ๊ท๊ฒฉ

๋ค์ ํ์ ์ด๋๋ท์ ๋ํ์ ์ธ ๊ท๊ฒฉ์ ์ ๋ฆฌํด๋๋ค.

| ๊ท๊ฒฉ ์ด๋ฆ   | ํต์  ์๋ | ์ผ์ด๋ธ               | ์ผ์ด๋ธ ์ต๋ ๊ธธ์ด | ํ์คํ ์ฐ๋ |
| ----------- | --------- | -------------------- | ---------------- | ----------- |
| 10BASE5     | 10Mbps    | ๋์ถ์ผ์ด๋ธ           | 500m             | 1982๋      |
| 10BASE2     | 10Mbps    | ๋์ถ์ผ์ด๋ธ           | 185m             | 1988๋      |
| 10BASE-T    | 10Mbps    | UTP์ผ์ด๋ธ(Cat3์ด์)  | 100m             | 1990๋      |
| 100BASE5-TX | 100Mbps   | UTP์ผ์ด๋ธ(Cat5์ด์)  | 100m             | 1995๋      |
| 1000BASE-T  | 1000Mbps  | UTP์ผ์ด๋ธ(Cat5์ด์)  | 100m             | 1999๋      |
| 10GBASE-T   | 10Gbps    | UTP์ผ์ด๋ธ(Cat6a์ด์) | 100m             | 2006๋      |

![](https://images.velog.io/images/april_5/post/0d8760e3-7794-4888-9d34-1e02c92a51c6/image.png)

- 10: Mbps ๋จ์์ธ ํต์  ์๋
- BASE: BASEBAND๋ผ๋ ์ ์ก ๋ฐฉ์
- T: ์ผ์ด๋ธ ์ข๋ฅ

<br /><br />

---

### :: ์ฉ์ด ์ ๋ฆฌ๐ก

- `๋ฐ์ดํฐ ๋งํฌ ๊ณ์ธต(data link layer)`: ๋คํธ์ํฌ ๊ธฐ๊ธฐ ๊ฐ์ ๋ฐ์ดํฐ๋ฅผ ์ ์กํ๊ณ  ๋ฌผ๋ฆฌ ์ฃผ์๋ฅผ ๊ฒฐ์ ํ๋ค.

- `์ด๋๋ท(Ethernet)`: ์ปดํจํฐ ๋คํธ์ํฌ ๊ธฐ์  ์ค ํ๋๋ก ์  ์ธ๊ณ์ ์ฌ๋ฌด์ค์ด๋ ๊ฐ์ ์์ ์ผ๋ฐ์ ์ผ๋ก ์ฌ์ฉ๋๋ ๋์์ ๊ฐ์ฅ ๋ง์ด ํ์ฉ๋๋ ๊ธฐ์  ๊ท๊ฒฉ์ด๋ค.

- `์ถฉ๋(collision)`: ๋ฐ์ดํฐ๋ฅผ ํ ๋ฒ์ ํ๋๋ง ์ ์ก ํ  ์์๋ ์ฑ๋์ ์ ์ก ์ฅ์น ๋ ๊ฐ๊ฐ ๊ฐ์ ์์ ์ ํจํท์ ๋ณด๋ผ ๋ ์ผ์ด๋๋ ๋ฐ์ดํฐ ์ถฉ๋์ ๋งํ๋ค.

- `MAC ์ฃผ์(Medium Access Control address)`: ๋์ ์ฌ์ฉ๋๋ ๋คํธ์ํฌ ๋ชจ๋ธ์ธ ์ด๋๋ท์ ๋ฌผ๋ฆฌ์ ์ธ ์ฃผ์๋ก ์ปดํจํฐ ๋คํธ์ํฌ์์ ๊ฐ๊ฐ์ ๊ธฐ๊ธฐ๋ฅผ ๊ตฌ๋ถํ๊ธฐ ์ํด ์ฌ์ฉํ๋ ์ฃผ์๋ค.

- `์ค์์น(switch, ์ค์์นญ ํ๋ธ)`: ๋์ ๊ตฌ์ฑํ  ๋ ์ฌ์ฉํ๋ ๋จ๋ง๊ธฐ ๊ฐ ์ค์์นญ ๊ธฐ๋ฅ์ด ์๋ ํต์ ๋ง ์ค๊ณ ์ฅ์น๋ค. ์ปดํจํฐ(ํธ์คํธ)์์ ํน์ ํ ๋ค๋ฅธ ๋ค๋ฅธ ๋จ๋ง๊ธฐ๋ก ํจํท์ ๋ณด๋ผ ์ ์๋ ๊ธฐ๋ฅ์ด ์์ด ํต์  ํจ์จ์ด ํฅ์๋๋ค.

- `์ ์ด์ค ํต์  ๋ฐฉ์(full-duplex communication)`: ์ ํ ํ์ ๊ณผ ๊ฐ์ด ์ก์ ๊ณผ ์์ ์ด ์์ชฝ์์ ๋์์ ์ด๋ฃจ์ด์ง๋ ์๋ฐฉํฅ ํต์ ์ด๋ค. ์๋ก ๋ค๋ฅธ ํ์ ์ด๋ ์ฃผํ์๋ฅผ ์ด์ฉํ์ฌ ๋ฐ์ดํฐ ์ ํธ๊ฐ ์ถฉ๋๋๋ ์ํฉ์ ๋ฐฉ์งํ๋ค. ์ค์์นญ ํ๋ธ๋ฅผ ์ฌ์ฉํ๋ฉด ๋ ์นด๋์ ํ๋ธ ๊ฐ์ ๋์ ์ก์์ ์ด ๊ฐ๋ฅํด์ง๋ค.

- `ARP(Address Resolution Protocol, ์ฃผ์ ๋ณํ ํ๋กํ ์ฝ)`: ๋คํธ์ํฌ ๊ณ์ธต ์ฃผ์์ ๋ฐ์ดํฐ ๋งํฌ ๊ณ์ธต ์ฃผ์์ฌ์ด์ ๋ณํ์ ๋ด๋นํ๋ ํ๋กํ ์ฝ์ด๋ค. IP ์ฃผ์๋ฅผ ๋ฌผ๋ฆฌ ์ฃผ์์ธ MAC ์ฃผ์๋ก ๋ณํํ๋ ๋ฐ ์ฌ์ฉํ๋ค.

- `ARP ์บ์(ARP cache)`: ๊ฐ์ฅ ์ต๊ทผ์ ๋ณํํ 'IP ๋ ํ๋์จ์ด ์ฃผ์'๋ฅผ ๋ณด๊ดํ๊ณ  ์๋ ๋จ(RAM)์ ํ ์์ญ์ด๋ค.

- `ARP ์์ฒญ(ARP request)`: IP ์ฃผ์๋ฅผ ๋์นํ  ์ ์๋ ๋ฌผ๋ฆฌ ์ฃผ์์ธ MAC ์ฃผ์๋ฅผ ์ฐพ์๋ด๊ธฐ ์ํด ๋ณด๋ด๋ ๋ธ๋กํธ์บ์คํธ ํจํท ์์ฒญ์ด๋ค.

- `ARP ์๋ต(ARP reply)`: ARP ์์ฒญ(request)์ ๋ํ ์๋ต์ผ๋ก ์์ฒญํ IP ์ฃผ์์ ๋ํ ๋ฌผ๋ฆฌ ์ฃผ์์ธ MAC ์ฃผ์๊ฐ ์ค๋ ค์๋ค.
