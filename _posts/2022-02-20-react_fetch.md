---
title: "🚀React:: fetch() 함수 사용법"
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

4주차에 mock data 활용하여 react westagram을 구현하기 위해 공부하던 중
`fetch() 함수 사용법`에 대해 더 공부하고자 찾아보고 정리한 내용 기록해본다.

# ✨mock data

## ● mock data란? mock data가 필요한 이유

- UI를 구현하다 보면 API가 나오기 전에 페이지가 먼저 나오는 경우가 많은데,
- 이 때 프론트엔드 개발자는 API가 나오기만을 기다리는게 아닌 mock data 즉, 가짜 데이터? 샘플 데이터를 만들어서
- 내가 만든 화면에서 데이터가 어떻게 나타나는지를 미리 테스트하며 개발을 진행한다
- mock data를 잘 만들어 둔다면, 백엔드와 실제 연결할 때도 수월하게 작업할 수 있을 뿐만 아니라
- 자료의 형태가 구체적으로 특정되기 때문에 소통에도 도움이 된다

<br />

---

## ● mock data를 관리하는 두 가지 방법

#### 1. `.js` 파일로 데이터를 분리하는 방법

- `.js` 파일은 어떤 데이터인지 알 수 있게 명명한다
- **배열 데이터**를 **변수에 담고** 필요한 component에 `import`해서 사용
- `.js` 파일은 데이터를 `import` 하는 component 바로 옆으로 접근하기 쉬운 곳에 생성한다

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

#### 2. ⭐`.json` 파일로 데이터를 분리하는 방법⭐

- 두 번째는 실제 API에서 보내주는 데이터 형식에 맞게 `.json` 파일에 데이터를 담아 `fetch` 함수를 사용해 데이터를 받아오는 방법
- **위치** `public` 폴더 > `data` 폴더 > `.json`
- 해당 데이터는 `http://localhost:3000/data/파일명.json` 에서 확인 가능

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

# 🌈 fetch() 함수

- 백엔드로부터 데이터를 받아오려면 API를 호출하고 데이터를 응답받는다
- 이 때 자바스크립트 `Web API fetch()` 함수를 쓰거나 `axios library`를 사용한다
- API든 library든 어느것을 사용해도 괜찮지만, **중요한 것은**
  > - **http 통신의 요청과 응답에 대한 이해**와 ✨
  > - **promise 개념**에 대한 공부가 더 중요하다✨

<br />

---

## ● fetch() 함수 기본

<br />

### ○ 화살표 함수 선언

```jsx
fetch("api 주소")
  .then((res) => res.json())
  .then((res) => {
    // data를 응답 받은 후의 로직
  });
```

<br />

### ○ ES5의 함수 선언

```jsx
fetch("api 주소")
  .then(function (res) {
    return res.json();
  })
  .then(function (res) {
    // data를 응답 받은 후의 로직
  });
```

<br />

---

## ● fetch() 함수 - method가 `GET`인 경우

- fetch() 함수에서 default method는 GET 이다

<br />

#### ✔️ API 명세

```jsx
설명: 유저 정보를 가져온다.
base url: https://api.google.com
endpoint: /user/3
method: get
응답형태:
    {
        "success": boolean,
        "user": {
            "name": string,
            "batch": number
        }
    }
```

<br />

#### ✔️ API호출

```jsx
fetch('https://api.google.com/user/3')
  .then(res => res.json())
  .then(res => {
    if (res.success) {
        console.log(`${res.user.name}` 님 환영합니다);
    }
  });
```

<br />

#### ✔️ 예시

```jsx
import React, { Component } from 'react';

class User extends Component {
  componentDidMount() {
    // user id가 props를 통해 넘어온다고 가정
    const { userId } = this.props;

    fetch(`https://api.google.com/user/${userId}`)
      .then(res => res.json())
      .then(res => {
        if (res.success) {
            console.log(`${res.user.name}` 님 환영합니다);
        }
      });
  }
}
```

<br />

---

## ● fetch() 함수 - method가 `POST`인 경우

- POST인 경우에는 fetch() 함수에 method 정보를 인자로 넘겨주어야 한다

<br />

#### ✔️ API 명세

```jsx
설명: 유저를 저장한다.
base url: https://api.google.com
endpoint: /user
method: post
요청 body:
    {
        "name": string,
        "batch": number
    }

응답 body:
    {
        "success": boolean
    }
```

<br />

#### ✔️ API호출

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
      alert("저장 완료");
    }
  });
```

<br />

1. 두 번째 인자에 method와 body를 보내주어야 한다
2. method는 post
3. body는 JSON형태로 보내기 위해 `JSON.stringfy()` 함수에 객체를 인자로 전달하여 **JSON형태로 변환**했다.

<br />

### ○fetch() 함수 - method가 GET인데 parameter를 전달해야 하는 경우

- `path` 말고 `query string`으로 넘겨줘야 할 수도 있다

<br />

#### ✔️ API 명세

```jsx
설명: 유저 정보를 가져온다.
base url: https://api.google.com
endpoint: /user
method: get
query string: ?id=아이디
응답형태:
    {
        "success": boolean,
        "user": {
            "name": string,
            "batch": number
        }
    }
```

<br />

#### ✔️ API호출

```jsx
fetch('https://api.google.com/user?id=3')
  .then(res => res.json())
  .then(res => {
    if (res.success) {
        console.log(`${res.user.name}` 님 환영합니다);
    }
  });
```

<br />

---

## ● res.json()의 의미

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

실제 작성한 코드로 첫번째 `.then'의 `res`와 두번째 `.then'의 `data`를 `console.log`에서 확인해보았다

![](<https://images.velog.io/images/april_5/post/7349caa3-e6fc-469f-a334-c699cb38e35a/res.json().JPG>)

- 첫번째 `.then'의 `res`

  - http 통신 요청과 응답에서 응답의 정보를 담고 있는 객체 `Response Object`
  - 실제 데이터는 보이지 않기 때문에
  - 응답으로 받는 JSON 데이터를 사용하기 위해서는 Response Object 의 json 함수를 호출하고, return 해야한다

- 두번째 `.then'의 `data`
  - 첫번째 `.then` 함수에서 응답 body의 데이터를 받을 수 있다

<br />

### ○ 백앤드에서 응답 body를 안 주는 경우

- `res.status` 응답 코드로 확인하면 된다
  - 200 정상
  - 403 백엔드 찾자??

<br />

---

현재까지 `react`로 작업하고 `mock data`로 테스트까지 해본 **westagram project**
아직 갈 길이 멀지만~ 나름 뿌듯??ㅋㅋ 일희일비 중...😅
![](https://images.velog.io/images/april_5/post/42bfe202-f70d-4bf0-b941-aee06a5f0c84/react-westagram-mockdata.gif)

---

[예리님의 블로그](https://yeri-kim.github.io/posts/fetch/)

<br /><br />
