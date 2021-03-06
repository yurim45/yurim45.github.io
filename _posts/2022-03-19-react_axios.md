---
title: "๐React:: Axios ์ฌ์ฉ๋ฒ "
tags:
  - [React]
permalink: /study/react/axios

navigation: true
toc: true
toc_sticky: true

date: 2022-03-19
last_modified_at: 2022-03-19
---

![](https://images.velog.io/images/april_5/post/46afd137-f1c1-47a3-948b-39ea3e783060/image.png)

# `Axios`๋?

<span style="color:#7C4791">**axios**</span>๋, ๋ธ๋ผ์ฐ์ , Node.js๋ฅผ ์ํ Promise API๋ฅผ ํ์ฉํ๋ HTTP ๋น๋๊ธฐ ํต์  ๋ผ์ด๋ธ๋ฌ๋ฆฌ

> ๋ฐฑ์๋์ ํ๋ก ํธ์๋๋ **ํต์ ์ ์ฝ๊ฒ ํ๊ธฐ ์ํด** ์ฌ์ฉ๋๋ ๋ผ์ด๋ธ๋ฌ๋ฆฌ

<br />

## `axios` ํน์ง

- ์ด์ ํ๊ฒฝ์ ๋ฐ๋ผ ๋ธ๋ผ์ฐ์ ์ XMLHttpRequest ๊ฐ์ฒด ๋๋ Node.js์ http api ์ฌ์ฉ
- Promise(ES6) API ์ฌ์ฉ
- ์์ฒญ๊ณผ ์๋ต ๋ฐ์ดํฐ์ ๋ณํ
- HTTP ์์ฒญ ์ทจ์
- HTTP ์์ฒญ๊ณผ ์๋ต์ JSON ํํ๋ก ์๋ ๋ณ๊ฒฝ

> **HTTP(HyperText Transfer Protocol)**๋?
> HTML๊ณผ ๊ฐ์ ํ์ดํผ๋ฏธ๋์ด ๋ฌธ์๋ฅผ ์ ์กํ๊ธฐ์ํ ์ ํ๋ฆฌ์ผ์ด์ ๋ ์ด์ด ํ๋กํ ์ฝ. ํต์  ๊ท์ฝ.

<br />

---

# `axios` ์ฌ์ฉ๋ฒ

`axios`์ `Request method`๋

- **GET** : axios.get(url[, config])
- **POST** : axios.post(url, data[, config])
- **PUT** : axios.put(url, data[, config])
- **DELETE** : axios.delete(url[, config])

`axios`์์ `Request Method`๋ฅผ ์ฌ์ฉํ๊ธฐ ์ํด์๋ `axios`์ `.`์ ๋ถํ๋ฉฐ ์๋ฌธ์๋ก `Req` Method๋ฅผ ๋ฃ์ด์ฃผ๋ฉด ๋๋ค.

๊ทธ๋ฆฌ๊ณ  ํด๋น ๋ฉ์๋์ ํ๋ผ๋ฏธํฐ์๋ API์ ์ฃผ์๋ฅผ ๋ฃ๋๋ค.

<br />

---

## :: `axios`์ ๊ธฐ๋ณธ์ ์ธ ์ฌ์ฉ๋ฒ

์ผ๋ฐ์ ์ผ๋ก `axios`์ **4๊ฐ์ง ๊ธฐ๋ณธ ๋ฉ์๋**๋ฅผ ์ฌ์ฉํ๊ธฐ ์ํด ์ง์ ํด์ผํ  ๊ฒ๋ค์ด ์๋ค.

**4๊ฐ์ง ๊ธฐ๋ณธ Params**

- **Method**
- **Url**
- **Data** (optional)
- **Params** (optional)

์ด 4๊ฐ์ง ๋ฐฉ๋ฒ์ axios์ ์๋ ค์ค์ผ ํ๋ค.

```js
axios({
  method: "get",
  url: "url",
  responseType: "type",
}).then(function (response) {
  // response Action
});
```

<br />

๋ง์ฝ POST ๋ฉ์๋์์ data๋ฅผ ์ ์กํ๊ธฐ ์ํด์๋ url ๋ฐ์ data Object๋ฅผ ์ถ๊ฐํ๋ฉด ๋๋ค.

<br />

---

## :: `axios`์ <span style="color:dodgerblue">**๋จ์ถ**</span> ์ฌ์ฉ๋ฒ

4๊ฐ์ง ๊ธฐ๋ณธ ํ๋ผ๋ฏธํฐ๋ฅผ ์๋ตํ๊ฑฐ๋ ๊ฐ๊ฒฐํ๊ฒ ์ฌ์ฉํ  ์ ์๋ค

<br />

### `axios.get()`

`axios.get()`์ ์ฌ์ฉํ๋ 2๊ฐ์ง ์ํฉ์ด ์๋๋ฐ
2๊ฐ์ง ์ํฉ์ ๋ฐ๋ผ `params: {}` ๊ฐ์ฒด๊ฐ ์กด์ฌํ ์ง ์ํ ์ง๊ฐ ๊ฒฐ์ ๋๋ค.

- <span style="color:dodgerblue">**๋จ์ ๋ฐ์ดํฐ(ํ์ด์ง ์์ฒญ, ์ง์ ๋ ์์ฒญ) ์์ฒญ**</span>์ ์ํํ  ๊ฒฝ์ฐ

```js
// callback ์ ์ฌ์ฉํ  ๋,
axios
  .get("url")
  .then((response) => {
    // response
  })
  .catch((error) => {
    // ์ค๋ฅ๋ฐ์์ ์คํ
  })
  .then(() => {
    // ํญ์ ์คํ
  });

// async await ํจ์๋ฅผ ์ฌ์ฉํ  ๋,
try {
  const data = await axios.get("url");
} catch {
  // ์ค๋ฅ ๋ฐ์์ ์คํ
}
```

<br />

- **ํ๋ผ๋ฏธํฐ ๋ฐ์ดํฐ๋ฅผ ํฌํจ**์ํค๋ ๊ฒฝ์ฐ (์ฌ์ฉ์ ๋ฒํธ์ ๋ฐ๋ฅธ ์กฐํ)

```js
axios.get("url", {
        params: {
          	id: 123
        }
    })
    .then(response => {
         // response
    }).catch(error => {
        // ์ค๋ฅ๋ฐ์์ ์คํ
    }).then(() => {
        // ํญ์ ์คํ
    });


// async await ํจ์๋ฅผ ์ฌ์ฉํ  ๋,
try {
	const data = await axios.get("url",
         params: {
			id: 123
		 }
    );
} catch {
	// ์ค๋ฅ ๋ฐ์์ ์คํ
}
```

<br />

### `axios.post()`

`post` ๋ฉ์๋์๋ ์ผ๋ฐ์ ์ผ๋ก ๋ฐ์ดํฐ๋ฅผ **Message Body์ ํฌํจ**์์ผ ๋ณด๋ธ๋ค.
`get` ๋ฉ์๋์์ `params`๋ฅผ ์ฌ์ฉํ ๊ฒฝ์ฐ์ ๋น์ทํ๊ฒ ์ํ๋๋ค.

```js
axios
  .post("url", {
    username: "",
    password: "",
  })
  .then((response) => {
    // response
  })
  .catch((error) => {
    // ์ค๋ฅ๋ฐ์์ ์คํ
  })
  .then(() => {
    // ํญ์ ์คํ
  });

// async await ํจ์๋ฅผ ์ฌ์ฉํ  ๋,
try {
  const data = await axios.post("url");
} catch {
  // ์ค๋ฅ ๋ฐ์์ ์คํ
}
```

<br />

### `axios.put()`

`put` ๋ฉ์๋๋ ์๋ฒ ๋ด๋ถ์ ์ผ๋ก `get` โ `post` ๊ณผ์ ์ ๊ฑฐ์น๊ธฐ ๋๋ฌธ์ `post` ๋ฉ์๋์ ๋น์ทํ ํํ์ด๋ค.

```js
axios
  .put("url", {
    username: "",
    password: "",
  })
  .then((response) => {
    // response
  })
  .catch((error) => {
    // ์ค๋ฅ๋ฐ์์ ์คํ
  })
  .then(() => {
    // ํญ์ ์คํ
  });

// async await ํจ์๋ฅผ ์ฌ์ฉํ  ๋,
try {
  const data = await axios.put("url", {
    username: "",
    password: "",
  });
} catch {
  // ์ค๋ฅ ๋ฐ์์ ์คํ
}
```

<br />

### `axios.delete()`

`delete` ๋ฉ์๋์๋ ์ผ๋ฐ์ ์ผ๋ก `body`๊ฐ ๋น์ด์๋ค.
๊ทธ๋์ ํํ๋ `get`๊ณผ ๋น์ทํ ํํ๋ฅผ ๋์ง๋ง **ํ ๋ฒ `delete` ๋ฉ์๋๊ฐ ์๋ฒ์ ๋ค์ด๊ฐ๊ฒ ๋๋ค๋ฉด ์๋ฒ ๋ด์์ ์ญ์  process๋ฅผ ์งํ**ํ๊ฒ ๋๋ค.

```js
axios
  .delete("/user?ID=12345")
  .then((response) => {
    // handle success
    console.log(response);
  })
  .catch((error) => {
    // handle error
    console.log(error);
  })
  .then(() => {
    // always executed
  });

// async await ํจ์๋ฅผ ์ฌ์ฉํ  ๋,
try {
  const data = await axios.delete("url");
} catch {
  // ์ค๋ฅ ๋ฐ์์ ์คํ
}
```

<br />

**๋ง์ ๋ฐ์ดํฐ๋ฅผ ์์ฒญํ  ๊ฒฝ์ฐ**
ํ์ง๋ง `query`๋ `params`๊ฐ ๋ง์์ ธ์ ํค๋์ ๋ง์ ์ ๋ณด๋ฅผ ๋ด์ ์ ์์ ๋๋ **๋ ๋ฒ์งธ ์ธ์์ `data`๋ฅผ ์ถ๊ฐ**ํด์ค ์ ์๋ค.

```js
axios
  .delete("/user?ID=12345", {
    data: {
      post_id: 1,
      comment_id: 5,
      username: "april",
    },
  })
  .then((response) => {
    // handle success
    console.log(response);
  })
  .catch((error) => {
    // handle error
    console.log(error);
  })
  .then(() => {
    // always executed
  });

// async await ํจ์๋ฅผ ์ฌ์ฉํ  ๋,
try {
  const data = await axios.delete("url");
} catch {
  // ์ค๋ฅ ๋ฐ์์ ์คํ
}
```

<br />

---

## :: React์์ `axios` ์ฌ์ฉ

๋ณดํต ํ๋ก์ ํธ์์๋

- `API์ ์คํ`, `์๋ฒ์ ์ฃผ์`, `credentials ์ค์ `์ ๋ด๋นํ๋ `API.js` ๋ผ๋ ํ์ผ์ ๋ง๋ค๊ณ 
- `axios` ์ `๊ธฐ๋ณธ ์ค์ `์ ๋ํด์ ์ง์ ํด์ฃผ๊ณ 
- ๊ฐ๊ฐ์ ์๋น์ค์์ ๊ฐ์ ธ๊ฐ ์ฌ์ฉํ๋ ํํ๋ก ๊ตฌํ.

### `axios` ์ ์ธ์คํด์ค ์์ฑ/async await ํต์ 

๋จผ์  `axios` ์ ์ธ์คํด์ค๋ฅผ ์์ฑํด์ API๋ผ๋ ๋ณ์์ ๋ด๊ณ  API๋ฅผ ๋ฐํ์ํจ๋ค.

```js
// API.js
// axios ์ ์ธ์คํด์ค๋ฅผ ์์ฑ
import axios from "axios";

const API = axios.create({
  BASE_URL: "",
  headers: {
    "Content-Type": "application/json",
  },
  withCredentials: true,
});

export default API;
```

<br />

๊ฐ๊ฐ ํ์ผ์์๋ async await ์ผ๋ก ์ฝ๋ฐฑ์ ์ฒ๋ฆฌํ์ฌ ํต์ ํ๋ค.

```js
import API from "../utils/API";

export const login = async (code) => {
  const { data } = await API.post("url", JSON.stringify(code));
  return data;
};
```

<br />

Error Handling์ ์ํ try-catch๋ฌธ ์ฌ์ฉ

```js
import API from "../utils/API";

export const refresh = async () => {
  try {
    const { data } = await API.get("url");
    return data;
  } catch {
    // Error Handling
  }
};
```

<br />

[React axios](https://wonit.tistory.com/305)
