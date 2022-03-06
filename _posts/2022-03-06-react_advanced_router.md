---
title: "🚀React:: 🌈React Advanced Router⭐️"
tags:
  - [React]
permalink: /study/react/advanced_router

navigation: true
toc: true
toc_sticky: true

date: 2022-03-06
last_modified_at: 2022-03-06
---

![](https://images.velog.io/images/april_5/post/707c8c3b-7893-4776-890a-bd897bb78728/React.png)

✅ **목표!**

- `Path Parameter`와 `Query Parameter`의 차이점에 대해 설명할 수 있다
- `history`, `location`, `match `객체의 용도가 무엇인지 설명할 수 있다
- `URL` 에서 동적인 부분을 변수로 처리할 수 있고, 이를 통해 동적 라우팅 기능을 구현할 수 있다
- `offset` 과 `limit` 개념을 사용하여 페이지네이션 기능을 구현할 수 있다

<br />
<br />

---

# ⭐️Routing

> - `route` + `-ing` : 경로(route)를 찾아가는 행위

- 즉 **라우팅 이란, 다른 경로(url 주소)에 따라 다른 View(화면)를 보여주는 것.** [React Router](https://velog.io/@april_5/TIL17-React-Router)

<br />

### ● 정적 라우팅

> 정해진 경우(정적, static)에 대해서만 경로를 표현

```jsx
"/"         => <App />
"/users"    => <Users />
"/products" => <Products />
```

<br />

---

# ✨동적 라우팅

> 동적인 경로를 처리할 수 있는 방법으로 `Path Parameter` 와 `Query Parameter`가 있다

## ○Dynamic Routing & Path Parameter

> 라우트 경로 끝에 들어가는 **각기 다른 id 값들을 저장하는 매개 변수**를 Path Parameter 라고 한다

```jsx
localhost: 3000 / product / 2;
localhost: 3000 / product / 45;
localhost: 3000 / product / 125;
```

<br />

- Path Parameter 는 Routes 컴포넌트에서 다음과 같이 정의된다

```jsx
<Router>
  <Switch>
    <Route exact path='/product/:id' component={productDetail} />
  </Switch>
</Router>
```

<br />

- `:` 는 Path Parameter 가 올 것임을 의미.
- `id` 는 해당 Path Parameter 의 이름을 의미.
- 변수 명을 짓듯이, 임의의 이름을 지정해줄 수 있다. ex) `:productId`

<br />

### ● history, match, location 객체

> `Routes.js` 의 **`Route` 컴포넌트의 `component` 프로퍼티에 직접 연결되어 있는 하위 컴포넌트**는 `history`, `location`, `match` 3가지 객체를 props 를 통해 제공 받는다.

- `history` 객체는 페이지 이동을 위한 여러 메서드들을 담고 있다. (ex, `push`)
- `location` 객체는 현재 url 경로에 관한 정보를 담는다.
- `match` 객체는 Path Parameter 에 관한 정보를 담는다.

<br />

### 📌 참고!! withRouter HOC🎈

- Route 에 연결되어 있지 않기 때문에, history, location, match 객체를 제공받지 못한다
- 하지만, 연결 되어있지 않은 컴포넌트에서도 세가지 객체를 사용하고 싶을 때엔 `withRouter HOC` 가 그 기능을 제공한다. -`withRouter` 는 함수이다.
- 인자로 컴포넌트를 받고, **_해당 컴포넌트에 3가지 객체를 추가한 컴포넌트를 반환한다._**💡

<br />

---

## ○ Pagination & Query Parameter

### ● Query Parameter

> 쿼리 스트링이란 말 그대로 해당 엔드포인트에 대해 질의문(query)를 보내는 요청을 뜻한다

쿼리스트링을 이용한 페이지 네이션 기능 또한 동적 라우팅 기능과 크게 다르지 않는데, 두 기능의 구현 순서를 비교해보면!

<br />

### :: 동적 라우팅

1. 리스트 페이지에서 카드를 클릭.
2. url 이동. 이때, 카드의 고유한 id 값이 url 에 포함된다.
3. 이동한 페이지에서, url 에 담겨있는 id 값을 `match` 객체를 이용하여 가져온다.
4. 가져온 id 값을 이용하여 데이터를 요청한다.

<br />

### :: 페이지네이션

1. 리스트 페이지에서 버튼을 클릭.
2. url 이동. 이때 url 에는 각 버튼에 **해당하는 쿼리스트링이 포함된다.**
3. 이동한 페이지에서, url 에 담겨있는 쿼리스트링을 **`location` 객체를 이용하여** 가져온다.
4. 가져온 쿼리스트링을 이용하여 데이터를 요청한다.

<br />

---

## 실제 프로젝트에서 적용 예시

```jsx
fetch(`${GET_CATEGORY_API}/categories?size=10&page=${num}`)
  .then((response) => response.json())
  .then((productsdata) => {
    this.setState({
      productsData: productsdata.message,
      num: num + 1,
    });
  });
```

<br />
