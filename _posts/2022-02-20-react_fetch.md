---
title: "๐React:: fetch() ํจ์ ์ฌ์ฉ๋ฒ"
tags:
  - [React]
permalink: /study/react/fetch

navigation: true
toc: true
toc_sticky: true

date: 2022-02-20
last_modified_at: 2022-02-20
---

![](https://images.velog.io/images/april_5/post/707c8c3b-7893-4776-890a-bd897bb78728/React.png)

4์ฃผ์ฐจ์ mock data ํ์ฉํ์ฌ react westagram์ ๊ตฌํํ๊ธฐ ์ํด ๊ณต๋ถํ๋ ์ค
`fetch() ํจ์ ์ฌ์ฉ๋ฒ`์ ๋ํด ๋ ๊ณต๋ถํ๊ณ ์ ์ฐพ์๋ณด๊ณ  ์ ๋ฆฌํ ๋ด์ฉ ๊ธฐ๋กํด๋ณธ๋ค.

# โจmock data

## โ mock data๋? mock data๊ฐ ํ์ํ ์ด์ 

- UI๋ฅผ ๊ตฌํํ๋ค ๋ณด๋ฉด API๊ฐ ๋์ค๊ธฐ ์ ์ ํ์ด์ง๊ฐ ๋จผ์  ๋์ค๋ ๊ฒฝ์ฐ๊ฐ ๋ง์๋ฐ,
- ์ด ๋ ํ๋ก ํธ์๋ ๊ฐ๋ฐ์๋ API๊ฐ ๋์ค๊ธฐ๋ง์ ๊ธฐ๋ค๋ฆฌ๋๊ฒ ์๋ mock data ์ฆ, ๊ฐ์ง ๋ฐ์ดํฐ? ์ํ ๋ฐ์ดํฐ๋ฅผ ๋ง๋ค์ด์
- ๋ด๊ฐ ๋ง๋  ํ๋ฉด์์ ๋ฐ์ดํฐ๊ฐ ์ด๋ป๊ฒ ๋ํ๋๋์ง๋ฅผ ๋ฏธ๋ฆฌ ํ์คํธํ๋ฉฐ ๊ฐ๋ฐ์ ์งํํ๋ค
- mock data๋ฅผ ์ ๋ง๋ค์ด ๋๋ค๋ฉด, ๋ฐฑ์๋์ ์ค์  ์ฐ๊ฒฐํ  ๋๋ ์์ํ๊ฒ ์์ํ  ์ ์์ ๋ฟ๋ง ์๋๋ผ
- ์๋ฃ์ ํํ๊ฐ ๊ตฌ์ฒด์ ์ผ๋ก ํน์ ๋๊ธฐ ๋๋ฌธ์ ์ํต์๋ ๋์์ด ๋๋ค

<br />

---

## โ mock data๋ฅผ ๊ด๋ฆฌํ๋ ๋ ๊ฐ์ง ๋ฐฉ๋ฒ

#### 1. `.js` ํ์ผ๋ก ๋ฐ์ดํฐ๋ฅผ ๋ถ๋ฆฌํ๋ ๋ฐฉ๋ฒ

- `.js` ํ์ผ์ ์ด๋ค ๋ฐ์ดํฐ์ธ์ง ์ ์ ์๊ฒ ๋ช๋ชํ๋ค
- **๋ฐฐ์ด ๋ฐ์ดํฐ**๋ฅผ **๋ณ์์ ๋ด๊ณ ** ํ์ํ component์ `import`ํด์ ์ฌ์ฉ
- `.js` ํ์ผ์ ๋ฐ์ดํฐ๋ฅผ `import` ํ๋ component ๋ฐ๋ก ์์ผ๋ก ์ ๊ทผํ๊ธฐ ์ฌ์ด ๊ณณ์ ์์ฑํ๋ค

```jsx
const COMMENT = [
  {
    id: 1,
    userName: "wecode",
    content: "Welcome to world best coding bootcamp!",
    isLiked: true,
  },
  {
    id: 2,
    userName: "yurim45",
    content: "Hi there.",
    isLiked: false,
  },
  {
    id: 3,
    userName: "april_5",
    content: "Hey.",
    isLiked: false,
  },
];

export default COMMENT;
```

<br />

#### 2. โญ`.json` ํ์ผ๋ก ๋ฐ์ดํฐ๋ฅผ ๋ถ๋ฆฌํ๋ ๋ฐฉ๋ฒโญ

- ๋ ๋ฒ์งธ๋ ์ค์  API์์ ๋ณด๋ด์ฃผ๋ ๋ฐ์ดํฐ ํ์์ ๋ง๊ฒ `.json` ํ์ผ์ ๋ฐ์ดํฐ๋ฅผ ๋ด์ `fetch` ํจ์๋ฅผ ์ฌ์ฉํด ๋ฐ์ดํฐ๋ฅผ ๋ฐ์์ค๋ ๋ฐฉ๋ฒ
- **์์น** `public` ํด๋ > `data` ํด๋ > `.json`
- ํด๋น ๋ฐ์ดํฐ๋ `http://localhost:3000/data/ํ์ผ๋ช.json` ์์ ํ์ธ ๊ฐ๋ฅ

```jsx
[
  {
    id: 1,
    userName: "wecode",
    content: "Welcome to world best coding bootcamp!",
    isLiked: true,
  },
  {
    id: 2,
    userName: "yurim45",
    content: "Hi there.",
    isLiked: false,
  },
  {
    id: 3,
    userName: "april_5",
    content: "Hey.",
    isLiked: false,
  },
];
```

<br />

---

# ๐ fetch() ํจ์

- ๋ฐฑ์๋๋ก๋ถํฐ ๋ฐ์ดํฐ๋ฅผ ๋ฐ์์ค๋ ค๋ฉด API๋ฅผ ํธ์ถํ๊ณ  ๋ฐ์ดํฐ๋ฅผ ์๋ต๋ฐ๋๋ค
- ์ด ๋ ์๋ฐ์คํฌ๋ฆฝํธ `Web API fetch()` ํจ์๋ฅผ ์ฐ๊ฑฐ๋ `axios library`๋ฅผ ์ฌ์ฉํ๋ค
- API๋  library๋  ์ด๋๊ฒ์ ์ฌ์ฉํด๋ ๊ด์ฐฎ์ง๋ง, **์ค์ํ ๊ฒ์**
  > - **http ํต์ ์ ์์ฒญ๊ณผ ์๋ต์ ๋ํ ์ดํด**์ โจ
  > - **promise ๊ฐ๋**์ ๋ํ ๊ณต๋ถ๊ฐ ๋ ์ค์ํ๋คโจ

<br />

---

## โ fetch() ํจ์ ๊ธฐ๋ณธ

<br />

### โ ํ์ดํ ํจ์ ์ ์ธ

```jsx
fetch("api ์ฃผ์")
  .then((res) => res.json())
  .then((res) => {
    // data๋ฅผ ์๋ต ๋ฐ์ ํ์ ๋ก์ง
  });
```

<br />

### โ ES5์ ํจ์ ์ ์ธ

```jsx
fetch("api ์ฃผ์")
  .then(function (res) {
    return res.json();
  })
  .then(function (res) {
    // data๋ฅผ ์๋ต ๋ฐ์ ํ์ ๋ก์ง
  });
```

<br />

---

## โ fetch() ํจ์ - method๊ฐ `GET`์ธ ๊ฒฝ์ฐ

- fetch() ํจ์์์ default method๋ GET ์ด๋ค

<br />

#### โ๏ธ API ๋ช์ธ

```jsx
์ค๋ช: ์ ์  ์ ๋ณด๋ฅผ ๊ฐ์ ธ์จ๋ค.
base url: https://api.google.com
endpoint: /user/3
method: get
์๋ตํํ:
    {
        "success": boolean,
        "user": {
            "name": string,
            "batch": number
        }
    }
```

<br />

#### โ๏ธ APIํธ์ถ

```jsx
fetch('https://api.google.com/user/3')
  .then(res => res.json())
  .then(res => {
    if (res.success) {
        console.log(`${res.user.name}` ๋ ํ์ํฉ๋๋ค);
    }
  });
```

<br />

#### โ๏ธ ์์

```jsx
import React, { Component } from 'react';

class User extends Component {
  componentDidMount() {
    // user id๊ฐ props๋ฅผ ํตํด ๋์ด์จ๋ค๊ณ  ๊ฐ์ 
    const { userId } = this.props;

    fetch(`https://api.google.com/user/${userId}`)
      .then(res => res.json())
      .then(res => {
        if (res.success) {
            console.log(`${res.user.name}` ๋ ํ์ํฉ๋๋ค);
        }
      });
  }
}
```

<br />

---

## โ fetch() ํจ์ - method๊ฐ `POST`์ธ ๊ฒฝ์ฐ

- POST์ธ ๊ฒฝ์ฐ์๋ fetch() ํจ์์ method ์ ๋ณด๋ฅผ ์ธ์๋ก ๋๊ฒจ์ฃผ์ด์ผ ํ๋ค

<br />

#### โ๏ธ API ๋ช์ธ

```jsx
์ค๋ช: ์ ์ ๋ฅผ ์ ์ฅํ๋ค.
base url: https://api.google.com
endpoint: /user
method: post
์์ฒญ body:
    {
        "name": string,
        "batch": number
    }

์๋ต body:
    {
        "success": boolean
    }
```

<br />

#### โ๏ธ APIํธ์ถ

```jsx
fetch("https://api.google.com/user", {
  method: "post",
  body: JSON.stringify({
    name: "april",
    batch: 1,
  }),
})
  .then((res) => res.json())
  .then((res) => {
    if (res.success) {
      alert("์ ์ฅ ์๋ฃ");
    }
  });
```

<br />

1. ๋ ๋ฒ์งธ ์ธ์์ method์ body๋ฅผ ๋ณด๋ด์ฃผ์ด์ผ ํ๋ค
2. method๋ post
3. body๋ JSONํํ๋ก ๋ณด๋ด๊ธฐ ์ํด `JSON.stringfy()` ํจ์์ ๊ฐ์ฒด๋ฅผ ์ธ์๋ก ์ ๋ฌํ์ฌ **JSONํํ๋ก ๋ณํ**ํ๋ค.

<br />

### โfetch() ํจ์ - method๊ฐ GET์ธ๋ฐ parameter๋ฅผ ์ ๋ฌํด์ผ ํ๋ ๊ฒฝ์ฐ

- `path` ๋ง๊ณ  `query string`์ผ๋ก ๋๊ฒจ์ค์ผ ํ  ์๋ ์๋ค

<br />

#### โ๏ธ API ๋ช์ธ

```jsx
์ค๋ช: ์ ์  ์ ๋ณด๋ฅผ ๊ฐ์ ธ์จ๋ค.
base url: https://api.google.com
endpoint: /user
method: get
query string: ?id=์์ด๋
์๋ตํํ:
    {
        "success": boolean,
        "user": {
            "name": string,
            "batch": number
        }
    }
```

<br />

#### โ๏ธ APIํธ์ถ

```jsx
fetch('https://api.google.com/user?id=3')
  .then(res => res.json())
  .then(res => {
    if (res.success) {
        console.log(`${res.user.name}` ๋ ํ์ํฉ๋๋ค);
    }
  });
```

<br />

---

## โ res.json()์ ์๋ฏธ

```jsx
    fetch('http://localhost:3000/data/feedData.json')
      .then(res => {
        console.log(res);
        return res.json();
      })
      .then(data => {
        console.log(data);
        this.setState({
          feedData: data,
        });
      });
  }
```

<br />

์ค์  ์์ฑํ ์ฝ๋๋ก ์ฒซ๋ฒ์งธ `.then'์ `res`์ ๋๋ฒ์งธ `.then'์ `data`๋ฅผ `console.log`์์ ํ์ธํด๋ณด์๋ค

![](<https://images.velog.io/images/april_5/post/7349caa3-e6fc-469f-a334-c699cb38e35a/res.json().JPG>)

- ์ฒซ๋ฒ์งธ `.then'์ `res`

  - http ํต์  ์์ฒญ๊ณผ ์๋ต์์ ์๋ต์ ์ ๋ณด๋ฅผ ๋ด๊ณ  ์๋ ๊ฐ์ฒด `Response Object`
  - ์ค์  ๋ฐ์ดํฐ๋ ๋ณด์ด์ง ์๊ธฐ ๋๋ฌธ์
  - ์๋ต์ผ๋ก ๋ฐ๋ JSON ๋ฐ์ดํฐ๋ฅผ ์ฌ์ฉํ๊ธฐ ์ํด์๋ Response Object ์ json ํจ์๋ฅผ ํธ์ถํ๊ณ , return ํด์ผํ๋ค

- ๋๋ฒ์งธ `.then'์ `data`
  - ์ฒซ๋ฒ์งธ `.then` ํจ์์์ ์๋ต body์ ๋ฐ์ดํฐ๋ฅผ ๋ฐ์ ์ ์๋ค

<br />

### โ ๋ฐฑ์ค๋์์ ์๋ต body๋ฅผ ์ ์ฃผ๋ ๊ฒฝ์ฐ

- `res.status` ์๋ต ์ฝ๋๋ก ํ์ธํ๋ฉด ๋๋ค
  - 200 ์ ์
  - 403 ๋ฐฑ์๋ ์ฐพ์??

<br />

---

ํ์ฌ๊น์ง `react`๋ก ์์ํ๊ณ  `mock data`๋ก ํ์คํธ๊น์ง ํด๋ณธ **westagram project**
์์ง ๊ฐ ๊ธธ์ด ๋ฉ์ง๋ง~ ๋๋ฆ ๋ฟ๋ฏ??ใใ ์ผํฌ์ผ๋น ์ค...๐
![](https://images.velog.io/images/april_5/post/42bfe202-f70d-4bf0-b941-aee06a5f0c84/react-westagram-mockdata.gif)

---

[์๋ฆฌ๋์ ๋ธ๋ก๊ทธ](https://yeri-kim.github.io/posts/fetch/)

<br /><br />
