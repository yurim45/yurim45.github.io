---
title: "๐React:: React Router"
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

> ํ์ด์ง๊ฐ ํ ๊ฐ์ธ ์ดํ๋ฆฌ์ผ์ด์.

- _react๋ ํ๋์ htmlํ์ผ์ ๋ ๋๋งํ๋ ๋ฐฉ์์ผ๋ก ๊ตฌํ๋จ_
- ํ๋์ htmlํ์ผ์ ์ฌ๋ฌ ๊ฐ์ ํ์ด์ง๋ฅผ ๋ณด์ฌ์ฃผ๋ ๋ฐฉ๋ฒ์ด `Routing`

<br />

## โ Routing

> ๋ค๋ฅธ ๊ฒฝ๋ก(url ์ฃผ์)์ ๋ฐ๋ผ ๋ค๋ฅธ View(ํ๋ฉด)์ ๋ณด์ฌ์ฃผ๋ ๊ฒ

- react ์์ฒด์๋ ์ด๋ฐ ๊ธฐ๋ฅ์ด ๋ด์ฅ๋์ด ์์ง ์์ **๋ณ๋๋ก ์ค์น**ํด์ผ ํ๋ค
  - `react`๊ฐ `framework`๊ฐ ์๋ `library`๋ก ๋ถ๋ฅ๋๋ ์ด์ 
  - `React-router` react์ routing ๊ธฐ๋ฅ์ ์ํด ๊ฐ์ฅ ๋ง์ด ์ฌ์ฉ๋๋ library

<br />

### โ React-router

#### ๐ react-router ์ค์น

- 'npm install react-router-dom --save'
  - `--save` package.jsonํ์ผ์ dependencies์ ์ถ๊ฐ๋๋๋ก ํ๋ ๋ช๋ น์ด

<br />

#### ๐ Routes component ๊ตฌํ

- Routes.js๋ฅผ ๋ง๋ค์ด์ ์ฐ๊ฒฐํด์ผ ํ๋ component๋ฅผ `<Router>` ์๋์ ์์น์ํค๊ธฐ
  - `<Router>` ์๋์ ์์น ์ํจ๋ค๋ ๋ง์, `<Router>`๊ธฐ๋ฅ์ ์ถ๊ฐํ๊ฒ ๋ค๋ผ๋ ๋ป

```jsx
import React from "react";
import { BrowserRouter as Router, Switch, Route } from "react-router-dom";

// import Component๋ช from 'file ๊ฒฝ๋ก';
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

#### ๐ index.js

`ReactDOM.render(<Routes />, document.getElementById('root'));`

<br />

#### ๐ Route ์ด๋

- `<Link>` ํ๋ก์ ํธ ํ์ผ ๋ด, ์กฐ๊ฑด์์ด ์ด๋ํ  ๋ ์ฌ์ฉ
  - `<Link to="/signup">ํ์๊ฐ์</Link>`
- `withRouterHOC` ์กฐ๊ฑด์ด ํ์ํ ๊ฒฝ์ฐ ์ฌ์ฉ

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
          ๋ก๊ทธ์ธ
        </button>
      </div>
    );
  }
}

export default withRouter(Login);
```

<br />

---

## โจ [react-router-dom v6](https://reactrouter.com/docs/en/v6/upgrading/v5) ๋ณ๊ฒฝ์ฌํญ

> ์ด๋ ์๊ฐ๋ถํฐ `Switch๋ฅผ react-router-dom ํจํค์ง์์ import ํ  ์ ์๋ค`๋ ์ค๋ฅ๊ฐ ์๊ฒผ๋๋ฐ, ์๊ณ  ๋ณด๋ `react-router-dom v6`์์ `Switch`๊ฐ `Routes`๋ก ๋ฐ๋์๋ค๊ณ  ํ๋ค.

<br />

### โ๏ธ Switch โก๏ธ Routes๋ก ๋ณ๊ฒฝ๋จ

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

### โ๏ธ exact ์ต์ ์ญ์ 

- path ๋ฅผ ๊ธฐ์กด์ `path="/Web/:id"` ์์ `path=":id"` ๋ก, ์๋๊ฒฝ๋ก๋ก ์ง์ 
- ์ด ์ธ์๋, `path="."`, `path=".."` ๋ฑ์ผ๋ก ์๋๊ฒฝ๋ก๋ฅผ ํํ

```jsx
// categores ๋ก ์์๋๋ ๋ชจ๋  ๋ผ์ฐํ ๋งค์นญ
<Route path='categories/*' />
```

<br />

### โ๏ธ route ์์ ์ปดํฌ๋ํธ ๋ ๋๋ง

```jsx
// v5 ๋ฒ์  ์ฌ์ฉ ์์
<Route exact path="/" component={Login} />
  )}
/>

// v6 ๋ฒ์  ์ฌ์ฉ ์์
<Route path="/" component={<Login />} />
```

<br />

### โ๏ธ useHistory โก๏ธ useNavigate hook ๋ณ๊ฒฝ

```jsx
// v5
const history = useHistory();

history.push('/home');
history.replace('/home');

// v6
const navigate = useNavigate();

navigate('/home');
navigate('/home', {replace: true});

// v6 ์์์ ์์ผ๋ก, ๋ค๋ก ๊ฐ๊ธฐ ์ฌ์ฉ๋ฐฉ๋ฒ ๋ณํ
<button onClick={() => navigate(-2)}>Go 2 pages back</button>
<button onClick={() => navigate(-1)}>Go back</button>
<button onClick={() => navigate(1)}>Go forward</button>
<button onClick={() => navigate(2)}>Go 2 pages forward</button>
```

<br />

### โ๏ธ v6 ์ค์ฒฉ ๋ผ์ฐํ

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

### โ๏ธ ์ฝ๋๋ก ํ์ธํ๊ธฐ

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

โ ๋ชฉํ!

- SPA์ ๊ฐ๋์ ๋ํด ์ดํดํ๊ณ 
- `router`๊ฐ ๋ฌด์์ด๊ณ  ์ ์จ์ผ ํ๋์ง,
- `router` ์ฌ์ฉ ๋ฐฉ๋ฒ์ ๋ํด ์ตํ์
