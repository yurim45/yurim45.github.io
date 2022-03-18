---
title: "🚀React:: Axios 사용법 "
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

# `Axios`란?

<span style="color:#7C4791">**axios**</span>란, 브라우저, Node.js를 위한 Promise API를 활용하는 HTTP 비동기 통신 라이브러리

> 백엔드와 프론트엔드랑 **통신을 쉽게 하기 위해** 사용되는 라이브러리

<br />

## `axios` 특징

- 운영 환경에 따라 브라우저의 XMLHttpRequest 객체 또는 Node.js의 http api 사용
- Promise(ES6) API 사용
- 요청과 응답 데이터의 변형
- HTTP 요청 취소
- HTTP 요청과 응답을 JSON 형태로 자동 변경

> **HTTP(HyperText Transfer Protocol)**란?
> HTML과 같은 하이퍼미디어 문서를 전송하기위한 애플리케이션 레이어 프로토콜. 통신 규약.

<br />

---

# `axios` 사용법

`axios`의 `Request method`는

- **GET** : axios.get(url[, config])
- **POST** : axios.post(url, data[, config])
- **PUT** : axios.put(url, data[, config])
- **DELETE** : axios.delete(url[, config])

`axios`에서 `Request Method`를 사용하기 위해서는 `axios`에 `.`을 붙히며 소문자로 `Req` Method를 넣어주면 된다.

그리고 해당 메서드의 파라미터에는 API의 주소를 넣는다.

<br />

---

## :: `axios`의 기본적인 사용법

일반적으로 `axios`의 **4가지 기본 메서드**를 사용하기 위해 지정해야할 것들이 있다.

**4가지 기본 Params**

- **Method**
- **Url**
- **Data** (optional)
- **Params** (optional)

이 4가지 방법을 axios에 알려줘야 한다.

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

만약 POST 메서드에서 data를 전송하기 위해서는 url 밑에 data Object를 추가하면 된다.

<br />

---

## :: `axios`의 <span style="color:dodgerblue">**단축**</span> 사용법

4가지 기본 파라미터를 생략하거나 간결하게 사용할 수 있다

<br />

### `axios.get()`

`axios.get()`을 사용하는 2가지 상황이 있는데
2가지 상황에 따라 `params: {}` 객체가 존재할지 안할지가 결정된다.

- <span style="color:dodgerblue">**단순 데이터(페이지 요청, 지정된 요청) 요청**</span>을 수행할 경우

```js
// callback 을 사용할 때,
axios
  .get("url")
  .then((response) => {
    // response
  })
  .catch((error) => {
    // 오류발생시 실행
  })
  .then(() => {
    // 항상 실행
  });

// async await 함수를 사용할 때,
try {
  const data = await axios.get("url");
} catch {
  // 오류 발생시 실행
}
```

<br />

- **파라미터 데이터를 포함**시키는 경우 (사용자 번호에 따른 조회)

```js
axios.get("url", {
        params: {
          	id: 123
        }
    })
    .then(response => {
         // response
    }).catch(error => {
        // 오류발생시 실행
    }).then(() => {
        // 항상 실행
    });


// async await 함수를 사용할 때,
try {
	const data = await axios.get("url",
         params: {
			id: 123
		 }
    );
} catch {
	// 오류 발생시 실행
}
```

<br />

### `axios.post()`

`post` 메서드에는 일반적으로 데이터를 **Message Body에 포함**시켜 보낸다.
`get` 메서드에서 `params`를 사용한 경우와 비슷하게 수행된다.

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
    // 오류발생시 실행
  })
  .then(() => {
    // 항상 실행
  });

// async await 함수를 사용할 때,
try {
  const data = await axios.post("url");
} catch {
  // 오류 발생시 실행
}
```

<br />

### `axios.put()`

`put` 메서드는 서버 내부적으로 `get` ➔ `post` 과정을 거치기 때문에 `post` 메서드와 비슷한 형태이다.

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
    // 오류발생시 실행
  })
  .then(() => {
    // 항상 실행
  });

// async await 함수를 사용할 때,
try {
  const data = await axios.put("url", {
    username: "",
    password: "",
  });
} catch {
  // 오류 발생시 실행
}
```

<br />

### `axios.delete()`

`delete` 메서드에는 일반적으로 `body`가 비어있다.
그래서 형태는 `get`과 비슷한 형태를 띄지만 **한 번 `delete` 메서드가 서버에 들어가게 된다면 서버 내에서 삭제 process를 진행**하게 된다.

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

// async await 함수를 사용할 때,
try {
  const data = await axios.delete("url");
} catch {
  // 오류 발생시 실행
}
```

<br />

**많은 데이터를 요청할 경우**
하지만 `query`나 `params`가 많아져서 헤더에 많은 정보를 담을 수 없을 때는 **두 번째 인자에 `data`를 추가**해줄 수 있다.

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

// async await 함수를 사용할 때,
try {
  const data = await axios.delete("url");
} catch {
  // 오류 발생시 실행
}
```

<br />

---

## :: React에서 `axios` 사용

보통 프로젝트에서는

- `API의 스펙`, `서버의 주소`, `credentials 설정`을 담당하는 `API.js` 라는 파일을 만들고
- `axios` 의 `기본 설정`에 대해서 지정해주고
- 각각의 서비스에서 가져가 사용하는 형태로 구현.

### `axios` 의 인스턴스 생성/async await 통신

먼저 `axios` 의 인스턴스를 생성해서 API라는 변수에 담고 API를 반환시킨다.

```js
// API.js
// axios 의 인스턴스를 생성
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

각각 파일에서는 async await 으로 콜백을 처리하여 통신한다.

```js
import API from "../utils/API";

export const login = async (code) => {
  const { data } = await API.post("url", JSON.stringify(code));
  return data;
};
```

<br />

Error Handling을 위한 try-catch문 사용

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
