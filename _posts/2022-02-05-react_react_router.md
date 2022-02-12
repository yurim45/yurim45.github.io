---
title: "🚀React:: React Router"
tags:
  - [React]
permalink: /study/react/router

navigation: true
toc: true
toc_sticky: true

date: 2022-02-05
last_modified_at: 2022-02-05
---

![](https://images.velog.io/images/april_5/post/707c8c3b-7893-4776-890a-bd897bb78728/React.png)

# React Router

### SPA (Single Page Application)

> 페이지가 한 개인 어플리케이션.

- _react는 하나의 html파일에 렌더링하는 방식으로 구현됨_
- 하나의 html파일에 여러 개의 페이지를 보여주는 방법이 `Routing`

<br />

## ○ Routing

> 다른 경로(url 주소)에 따라 다른 View(화면)을 보여주는 것

- react 자체에는 이런 기능이 내장되어 있지 않아 **별도로 설치**해야 한다
  - `react`가 `framework`가 아닌 `library`로 분류되는 이유
  - `React-router` react의 routing 기능을 위해 가장 많이 사용되는 library

<br />

### ● React-router

#### 🔘 react-router 설치

- 'npm install react-router-dom --save'
  - `--save` package.json파일의 dependencies에 추가되도록 하는 명령어

<br />

#### 🔘 Routes component 구현

- Routes.js를 만들어서 연결해야 하는 component를 `<Router>` 아래에 위치시키기
  - `<Router>` 아래에 위치 시킨다는 말은, `<Router>`기능을 추가하겠다라는 뜻

```jsx
import React from "react";
import { BrowserRouter as Router, Switch, Route } from "react-router-dom";

// import Component명 from 'file 경로';
import Login from "./pages/Login/Login";
import Signup from "./pages/Signup/Signup";
import Main from "./pages/Main/Main";

class Routes extends React.Component {
  render() {
    return (
      <Router>
        <Switch>
          <Route exact path='/' component={Login} />
          <Route exact path='/signup' component={Signup} />
          <Route exact path='/main' component={Main} />
        </Switch>
      </Router>
    );
  }
}

export default Routes;
```

<br />

#### 🔘 index.js

`ReactDOM.render(<Routes />, document.getElementById('root'));`

<br />

#### 🔘 Route 이동

- `<Link>` 프로젝트 파일 내, 조건없이 이동할 때 사용
  - `<Link to="/signup">회원가입</Link>`
- `withRouterHOC` 조건이 필요한 경우 사용

```jsx
import React from "react";
import { withRouter } from "react-router-dom";

class Login extends React.Component {
  goToMain = () => {
    this.props.history.push("/main");
  };

  render() {
    return (
      <div>
        <button className='loginBtn' onClick={this.goToMain}>
          로그인
        </button>
      </div>
    );
  }
}

export default withRouter(Login);
```

<br />

---

## ✨ [react-router-dom v6](https://reactrouter.com/docs/en/v6/upgrading/v5) 변경사항

> 어느 순간부터 `Switch를 react-router-dom 패키지에서 import 할 수 없다`는 오류가 생겼는데, 알고 보니 `react-router-dom v6`에서 `Switch`가 `Routes`로 바뀌었다고 한다.

<br />

### ✔️ Switch ➡️ Routes로 변경됨

```jsx
// v5
<Switch>
  <Route ... />
</Routes>

// v6
<Routes>
  <Route ... />
</Routes>
```

<br />

### ✔️ exact 옵션 삭제

- path 를 기존의 `path="/Web/:id"` 에서 `path=":id"` 로, 상대경로로 지정
- 이 외에도, `path="."`, `path=".."` 등으로 상대경로를 표현

```jsx
// categores 로 시작되는 모든 라우팅 매칭
<Route path='categories/*' />
```

<br />

### ✔️ route 에서 컴포넌트 렌더링

```jsx
// v5 버전 사용 예시
<Route exact path="/" component={Login} />
  )}
/>

// v6 버전 사용 예시
<Route path="/" component={<Login />} />
```

<br />

### ✔️ useHistory ➡️ useNavigate hook 변경

```jsx
// v5
const history = useHistory();

history.push('/home');
history.replace('/home');

// v6
const navigate = useNavigate();

navigate('/home');
navigate('/home', {replace: true});

// v6 에서의 앞으로, 뒤로 가기 사용방법 변화
<button onClick={() => navigate(-2)}>Go 2 pages back</button>
<button onClick={() => navigate(-1)}>Go back</button>
<button onClick={() => navigate(1)}>Go forward</button>
<button onClick={() => navigate(2)}>Go 2 pages forward</button>
```

<br />

### ✔️ v6 중첩 라우팅

```jsx
import { BrowserRouter, Routes, Route, Link, Outlet } from "react-router-dom";

function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path='/' element={<Home />} />
        <Route path='users' element={<Users />}>
          <Route path='me' element={<OwnUserProfile />} />
          <Route path=':id' element={<UserProfile />} />
        </Route>
      </Routes>
    </BrowserRouter>
  );
}

function Users() {
  return (
    <div>
      <nav>
        <Link to='me'>My Profile</Link>
      </nav>

      <Outlet />
    </div>
  );
}
```

<br />

### ✔️ 코드로 확인하기

```jsx
import React from "react";
import { BrowserRouter as Router, Routes, Route } from "react-router-dom";
import Login from "./pages/Login/Login";
import Signup from "./pages/Signup/Signup";
import Main from "./pages/Main/Main";

class Routes extends React.Component {
  render() {
    return (
      <Router>
        <Routes>
          <Route path='/' component={<Login />} />
          <Route path='/signup' component={<Signup />} />
          <Route path='/main' component={<Main />} />
        </Routes>
      </Router>
    );
  }
}
```

<br />

---

✅ 목표!

- SPA의 개념에 대해 이해하고
- `router`가 무엇이고 왜 써야 하는지,
- `router` 사용 방법에 대해 익히자
