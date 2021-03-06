---
title: "๐จ CSS:: FLEXBOX FROGGY๐ธ"
tags:
  - [CSS]
permalink: /study/CSS/flexbox

navigation: true
toc: true
toc_sticky: true

date: 2021-08-19
last_modified_at: 2021-08-19
---

![]()

`์ฃผ๋์ด ๊ฐ๋ฐ์์ ๊ฐ์ธ ๊ณต๋ถ ๊ณผ์ ์ ๊ธฐ๋กํฉ๋๋ค.`

# Flexbox ๋?

> ์ผ๋ช flexbox๋ผ ๋ถ๋ฆฌ๋ Flexible Box module์ flexbox ์ธํฐํ์ด์ค ๋ด์ ์์ดํ ๊ฐ **๊ณต๊ฐ ๋ฐฐ๋ถ**๊ณผ **๊ฐ๋ ฅํ ์ ๋ ฌ ๊ธฐ๋ฅ**์ ์ ๊ณตํ๊ธฐ ์ํ 1์ฐจ์ ๋ ์ด์์ ๋ชจ๋ธ.
> flexbox๋ฅผ 1์ฐจ์์ด๋ผ ์นญํ๋ ๊ฒ์, ๋ ์ด์์์ ๋ค๋ฃฐ ๋ **ํ ๋ฒ์ ํ๋์ ์ฐจ์(ํ์ด๋ ์ด)๋ง์ ๋ค๋ฃฌ๋ค**๋ ๋ป์ด๋ค.

โจ์ฐธ๊ณ โจ **2์ฐจ์ ๋ชจ๋ธ**: ํ๊ณผ ์ด์ ํจ๊ป ์กฐ์ ํ๋ _CSS ๊ทธ๋ฆฌ๋ ๋ ์ด์์_

๐ฉ**์ง์ค!** flexbox๋ฅผ ์ ์ฉํ๋ ค๋ฉด, ์ ์ฉํ๋ ค๋ ์์์ `display: flex;`๋ฅผ ์ ์ฉ์ํจ๋ค

## โ justify-content

- ์์์ **๊ฐ๋ก ์ ๋ ฌ**
- 5๊ฐ์ ๊ฐ์ผ๋ก ๊ฐ๋ก๋ก ์ ๋ ฌ ์ํฌ ์ ์๋ค

  - `flex-start` ์์๋ค์ ์ปจํ์ด๋์ ์ผ์ชฝ์ผ๋ก ์ ๋ ฌ.
  - `flex-end` ์์๋ค์ ์ปจํ์ด๋์ ์ค๋ฅธ์ชฝ์ผ๋ก ์ ๋ ฌ.
  - `center` ์์๋ค์ ์ปจํ์ด๋์ ๊ฐ์ด๋ฐ๋ก ์ ๋ ฌ.
  - `space-between` ์์๋ค ์ฌ์ด์ ๋์ผํ ๊ฐ๊ฒฉ์ ๋๋ค.
  - `space-around` ์์๋ค ์ฃผ์์ ๋์ผํ ๊ฐ๊ฒฉ์ ๋๋ค.

- ์์

```css
#pond {
  display: flex;
  justify-content: flex-end;
}
```

![](https://images.velog.io/images/april_5/post/068d5965-9b1f-4d1d-8f23-bd23ba3efa90/image.png)

<br />

- ์์2

```css
#pond {
  display: flex;
  justify-content: center;
}
```

![](https://images.velog.io/images/april_5/post/03b29aae-eda9-4f4f-99b1-65c9ae40a8eb/image.png)

<br />

- ์์3

```css
#pond {
  display: flex;
  justify-content: space-around;
}
```

![](https://images.velog.io/images/april_5/post/89a75b6c-2e7b-4dc0-a572-268e6a3d227a/image.png)

<br />

- ์์4

```css
#pond {
  display: flex;
  justify-content: space-between;
}
```

![](https://images.velog.io/images/april_5/post/4c88ba68-f557-4f20-96ff-e9f6d4e27fe5/image.png)

<br />

---

## โ align-items

- ์์์ **์ธ๋ก ์ ๋ ฌ**
- 5๊ฐ์ ๊ฐ์ผ๋ก ๊ฐ๋ก๋ก ์ ๋ ฌ ์ํฌ ์ ์๋ค

  - `flex-start` ์์๋ค์ ์ปจํ์ด๋์ ๊ผญ๋๊ธฐ๋ก ์ ๋ ฌ.
  - `flex-end` ์์๋ค์ ์ปจํ์ด๋์ ๋ฐ๋ฅ์ผ๋ก ์ ๋ ฌ.
  - `center` ์์๋ค์ ์ปจํ์ด๋์ ์ธ๋ก์  ์์ ๊ฐ์ด๋ฐ๋ก ์ ๋ ฌ.
  - `baseline` ์์๋ค์ ์ปจํ์ด๋์ ์์ ์์น์ ์ ๋ ฌ.
  - `stretch` ์์๋ค์ ์ปจํ์ด๋์ ๋ง๋๋ก ๋๋ฆฐ๋ค.

- ์์

```css
#pond {
  display: flex;
  align-items: flex-end;
}
```

![](https://images.velog.io/images/april_5/post/0c755544-8579-446e-b516-ba2f2d63e3cf/image.png)

<br />

### โ justify-content+align-items

```css
#pond {
  display: flex;
  align-items: center;
  justify-content: center;
}
```

![](https://images.velog.io/images/april_5/post/b7a9440c-a016-4edf-90de-6f4b4ca2ed32/image.png)

<br />

---

## โ flex-direction

- ์์์ ์ ๋ ฌ ๋ฐฉํฅ์ ์ง์ 
- 4๊ฐ์ ๊ฐ์ผ๋ก ์ง์ ํ  ์ ์๋ค

  - `row` ์์๋ค์ ํ์คํธ์ ๋ฐฉํฅ๊ณผ ๋์ผํ๊ฒ ์ ๋ ฌ.
  - `row-reverse` ์์๋ค์ ํ์คํธ์ ๋ฐ๋ ๋ฐฉํฅ์ผ๋ก ์ ๋ ฌ.
  - `column` ์์๋ค์ ์์์ ์๋๋ก ์ ๋ ฌ.
  - `column-reverse` ์์๋ค์ ์๋์์ ์๋ก ์ ๋ ฌ.

- ์์

```css
#pond {
  display: flex;
  flex-direction: column;
}
```

![](https://images.velog.io/images/april_5/post/8b5ad9ce-55f0-4a76-ac7e-0a917bff30e5/image.png)

<br />

### โ flex-direction+justify-content

#### FROGGY ๋จ๊ณ 10

```css
#pond {
  display: flex;
  flex-direction: row-reverse;
  justify-content: flex-end;
}
```

![](https://images.velog.io/images/april_5/post/9ce10b3f-9212-41bc-b7f5-714a20707975/image.png)

<br />

#### FROGGY ๋จ๊ณ 12

```css
#pond {
  display: flex;
  flex-direction: column-reverse;
  justify-content: space-between;
}
```

![](https://images.velog.io/images/april_5/post/0b369cb2-0d2c-4dbb-bec7-f9c13235de03/image.png)

<br />

#### FROGGY ๋จ๊ณ 13

```css
#pond {
  display: flex;
  flex-direction: row-reverse;
  justify-content: center;
  align-items: flex-end;
}
```

![](https://images.velog.io/images/april_5/post/0bd05c11-ca5e-4906-a9f0-095551bb148a/image.png)

<br />

---

## โ order

- ๊ฐ ์์์ ๊ฐ๋ณ ์์ ์ ์ฉ
- order์ ๊ธฐ๋ณธ ๊ฐ์ 0์ด๋ฉฐ, ์์๋ ์์๋ก ๋ฐ๊ฟ ์ ์๋ค
- ์์

```css
#pond {
  display: flex;
}

.yellow {
  order: 1; /* ๋ธ๋ ๊ฐ๊ตฌ๋ฆฌ์ ์์๋ฅผ ๋ค๋ก ๋ฐ๊พผ๋ค */
}
```

![](https://images.velog.io/images/april_5/post/a1795479-c740-4711-850f-c50c166cd1b7/image.png)

<br />
  
- ์์2

```css
#pond {
  display: flex;
}

.red {
  order: -1;
}
```

![](https://images.velog.io/images/april_5/post/3c676eaa-d851-4a08-b9e3-ceaa73b13ce3/image.png)

<br />

---

## โ align-self

- ๊ฐ๋ณ ์์์ ์ ์ฉํ๋ ์์ฑ
- **align-items(์ธ๋ก ์ ๋ ฌ)**์ ๊ฐ๋ค๋ก ์ง์ ํ๋ค

  - `flex-start` ์์๋ค์ ์ปจํ์ด๋์ ๊ผญ๋๊ธฐ๋ก ์ ๋ ฌ.
  - `flex-end` ์์๋ค์ ์ปจํ์ด๋์ ๋ฐ๋ฅ์ผ๋ก ์ ๋ ฌ.
  - `center` ์์๋ค์ ์ปจํ์ด๋์ ์ธ๋ก์  ์์ ๊ฐ์ด๋ฐ๋ก ์ ๋ ฌ.
  - `baseline` ์์๋ค์ ์ปจํ์ด๋์ ์์ ์์น์ ์ ๋ ฌ.
  - `stretch` ์์๋ค์ ์ปจํ์ด๋์ ๋ง๋๋ก ๋๋ฆฐ๋ค.

- ์์

```css
#pond {
  display: flex;
  align-items: flex-start;
}

.yellow {
  align-self: flex-end;
}
```

![](https://images.velog.io/images/april_5/post/04602147-a876-4f6e-8c7a-90eb8f02e414/image.png)

<br />

### โborder+align-self

#### FROGGY ๋จ๊ณ 17

```css
#pond {
  display: flex;
  align-items: flex-start;
}

.yellow {
  order: 1;
  align-self: flex-end;
}
```

![](https://images.velog.io/images/april_5/post/9590cc4e-35af-4d2c-8149-d85f2606e892/image.png)

<br />

---

## โ flex-wrap

- ์ค ๋ฐ๊ฟ
- 3๊ฐ์ ๊ฐ์ผ๋ก ์ง์ ํ  ์ ์๋ค

  - `nowrap` ๋ชจ๋  ์์๋ค์ ํ ์ค์ ์ ๋ ฌ.
  - `wrap ์์๋ค์ ์ฌ๋ฌ ์ค์ ๊ฑธ์ณ ์ ๋ ฌ.
  - `wrap-reverse ์์๋ค์ ์ฌ๋ฌ ์ค์ ๊ฑธ์ณ ๋ฐ๋๋ก ์ ๋ ฌ.

- ์์

```css
#pond {
  display: flex;
  flex-wrap: wrap;
}
```

![](https://images.velog.io/images/april_5/post/e3d879ee-25de-47f1-bed3-954176015c30/image.png)

<br />

### โbflex-direction+flex-wrap

#### FROGGY ๋จ๊ณ 19

```css
#pond {
  display: flex;
  flex-direction: column;
  flex-wrap: wrap;
}
```

![](https://images.velog.io/images/april_5/post/739eaeb2-10cf-4a38-902f-a6cf67ea6f50/image.png)

<br />

---

## โ flex-flow

- flex-direction+flex-wrap
- ์์

```css
#pond {
  display: flex;
  flex-flow: column wrap;
}
```

![](https://images.velog.io/images/april_5/post/9b122b0b-3222-47db-b1e9-44efae052659/image.png)

<br />

---

## โ align-content

- ์ฌ๋ฌ ์ค ์ฌ์ด์ ๊ฐ๊ฒฉ์ ์ง์ 
- 5๊ฐ์ ๊ฐ์ผ๋ก ์ง์ ํ  ์ ์๋ค
  - `flex-start` ์ฌ๋ฌ ์ค๋ค์ ์ปจํ์ด๋์ ๊ผญ๋๊ธฐ์ ์ ๋ ฌ.
  - `flex-end` ์ฌ๋ฌ ์ค๋ค์ ์ปจํ์ด๋์ ๋ฐ๋ฅ์ ์ ๋ ฌ.
  - `center` ์ฌ๋ฌ ์ค๋ค์ ์ธ๋ก์  ์์ ๊ฐ์ด๋ฐ์ ์ ๋ ฌ.
  - `space-between` ์ฌ๋ฌ ์ค๋ค ์ฌ์ด์ ๋์ผํ ๊ฐ๊ฒฉ์ ๋๋ค.
  - `space-around` ์ฌ๋ฌ ์ค๋ค ์ฃผ์์ ๋์ผํ ๊ฐ๊ฒฉ์ ๋๋ค.
  - `stretch` ์ฌ๋ฌ ์ค๋ค์ ์ปจํ์ด๋์ ๋ง๋๋ก ๋๋ฆฐ๋ค.
- ๐ฉ**์ง์ค!** `align-content`๋ ์ฌ๋ฌ ์ค๋ค ์ฌ์ด์ ๊ฐ๊ฒฉ์ ์ง์ ํ๋ฉฐ, `align-items`๋ ์ปจํ์ด๋ ์์์ ์ด๋ป๊ฒ ๋ชจ๋  ์์๋ค์ด ์ ๋ ฌํ๋์ง๋ฅผ ์ง์ ํ๋ค.
- ํ ์ค๋ง ์๋ ๊ฒฝ์ฐ, `align-conten`t๋ ํจ๊ณผ๋ฅผ ๋ณด์ด์ง ์๋๋ค

- ์์

```css
#pond {
  display: flex;
  flex-wrap: wrap;
  align-content: flex-end;
}
```

![](https://images.velog.io/images/april_5/post/e1b3b1d5-ccd0-4da5-a224-d063dbdc0a34/image.png)

<br />

### โ flex-direction+align-content

#### FROGGY ๋จ๊ณ 23

```css
#pond {
  display: flex;
  flex-wrap: wrap;
  flex-direction: column-reverse;
  align-content: center;
}
```

![](https://images.velog.io/images/april_5/post/fef47509-4121-4224-a190-ee2f9acd2ac7/image.png)

<br />

### โ FROGGY ๋จ๊ณ 24

```css
#pond {
  display: flex;
  flex-flow: column-reverse wrap-reverse;
  justify-content: center;
  align-content: space-between;
}
```

![](https://images.velog.io/images/april_5/post/d0e03349-17a3-4958-b40c-8721b07f1b94/image.png)
