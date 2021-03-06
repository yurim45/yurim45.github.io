---
title: "๐React:: State๐ & Propsโจ &Event"
tags:
  - [React]
permalink: /study/react/state_props

navigation: true
toc: true
toc_sticky: true

date: 2022-02-13
last_modified_at: 2022-02-13
---

![](https://images.velog.io/images/april_5/post/707c8c3b-7893-4776-890a-bd897bb78728/React.png)

## โ State๐ & Event

> state : ์ํ
> ํ๋ฉด์ ๋ณด์ฌ์ค ์ปดํฌ๋ํธ์ **UI ์ ๋ณด(์ํ)**๋ฅผ ์ง๋๊ณ  ์๋ย **๊ฐ์ฒด**

<br />

### โ `State` ๊ฐ์ฒด

    - `constructor()` ์ ์์น. `constructor()`๋ ํ์ด์ง๊ฐ ๋ ๋๋  ๋ ์ด๊ธฐํ๋๋ ๊ฐ๋ค

```jsx
constructor() {
    super();
    this.state = {
      color: 'red',
    };
  }

<h1 style={{ color: this.state.color }} >Class Component | State</h1>

// this : ํด๋น ์ปดํฌ๋ํธ
// this.state : ํด๋น ์ปดํฌ๋ํธ์ state ๊ฐ์ฒด
// this.state.color : state ๊ฐ์ฒด์ ํน์  key(color)๊ฐ. ์ฆ "red"
```

<br />

### โ `setState()`

- `constructor()`์์ ์ ์ธ๋ state์ ๊ฐ์ ๋ณ๊ฒฝํ  ๋ ์ฌ์ฉ

```jsx
import React, { Component } from "react";

class State extends Component {
  constructor() {
    super();
    this.state = {
      color: "red",
    };
  }

  // `handleColor`ํจ์๋ฅผ ํธ์ถํ  ๋ state์ ๊ฐ์ ๋ณ๊ฒฝํ๊ฒ ๋ค = setState
  handleColor = () => {
    this.setState({
      color: "blue",
    });
  };

  render() {
    return (
      <div>
        <h1 style={{ color: this.state.color }}>Class Component | State</h1>
        <button onClick={this.handleColor}>Click</button>
      </div>
    );
  }
}

export default State;
```

<br />

---

## โ Props & Event

> props : properties(์์ฑ)
> props๋ **๋ถ๋ชจ component๋ก๋ถํฐ ์ ๋ฌ ๋ฐ์ *๋ฐ์ดํฐ*๋ฅผ ์ง๋๊ณ  ์๋ ๊ฐ์ฒด**

<br />

### โprops ๊ฐ์ฒด

- **Parent.js**
  - ๋ถ๋ชจ component์์ ์์ component๋ก state๊ฐ์ ์ ๋ฌํ๊ธฐ ์ํ ์ค๋น
    - `<Child titleColor={this.state.color}/>` `titleColor`๋ผ๋ Attribute๋ฅผ ์์๋ก ์ง์ ํ์ฌ `state` ๊ฐ์ฒด์ `color`๊ฐ์ ์ ๋ฌ

```jsx
// Parent.js
import React from "react";
import Child from "../pages/Children/Children";

class Parent extends React.Component {
  constructor() {
    super();
    this.state = {
      color: "red",
    };
  }

  render() {
    return (
      <div>
        <h1>Parent Component</h1>
        <Child titleColor={this.state.color} />
      </div>
    );
  }
}

export default State;
```

<br />

- **Child.js**
  - <Child /> ์ปดํฌ๋ํธ ๋ด๋ถ์์ ์ ๋ฌ ๋ฐ์ props ๋ฐ์ดํฐ๋ฅผ ์ด๋ป๊ฒ ์ฌ์ฉํ ๊น?
    - `{color : this.props.titleColor}` ์ ๋ฌ๋ฐ์ `props` ๊ฐ์ฒด์ `titleColor`๊ฐ

```jsx
// Child.js
import React from "react";

class Child extends React.Component {
  render() {
    // console.log(this.props); ๋ถ๋ชจ๋ก ๋ถํฐ ์ ๋ฌ๋ฐ์ props๊ฐ ํ์ธ
    return (
      <div>
        <h1 style={{ color: this.props.titleColor }}>Child Component</h1>
        // this : ํด๋น ์ปดํฌ๋ํธ // this.props : ํด๋น ์ปดํฌ๋ํธ์ props ๊ฐ์ฒด // this.props.titleColor
        : props ๊ฐ์ฒด์ ํน์  key(titleColor)๊ฐ. ์ฆ "red"
      </div>
    );
  }
}

export default State;
```

<br />

### โ `Props & event`

- ์์์๊ฒ ์ ๋ฌํ  state๊ฐ๊ณผ ํจ์๋ฅผ ์ ์ธ
  - `state`๋ `titleColor`๋ผ๋ Attribute๋ฅผ ํตํด ์ ๋ฌ
  - `handleColor` ๋ฉ์๋๋ `changeColor`๋ผ๋ Attribute๋ฅผ ํตํด ์ ๋ฌ

```jsx
// Parent.js
import React from "react";
import Child from "../pages/Children/Children";

class Parent extends React.Component {
  constructor() {
    super();
    this.state = {
      color: "red",
    };
  }

  handleColor = () => {
    this.setState({
      color: "blue",
    });
  };

  render() {
    return (
      <div>
        <h1>Parent Component</h1>
        <Child titleColor={this.state.color} changeColor={this.handleColor} />
      </div>
    );
  }
}

export default State;
```

<br />

- ๋ถ๋ชจ์๊ฒ ์ ๋ฌ๋ฐ์ props๋ฅผ
  - `h1`์ ์คํ์ผ๋ง์์ ์ฌ์ฉ `style={{color : this.props.titleColor}}`
  - `button`์ `onClick` ์ด๋ฒคํธ ๋ฐ์์ ํจ์ ํธ์ถ `onClick= this.props.changeColor}`

```jsx
// Child.js
import React from 'react';

class Child extends React.Component {
  render() {
    // console.log(this.props);

    return (
      <div>
        <h1 style={{color : this.props.titleColor}}>Child Component</h1>
		<button onClick= this.props.changeColor}>Click</button>
      </div>
    );
  }
}

export default State;
```

<br />

---

โ ๋ชฉํ!

- state์ ๊ฐ๋์ ๋ํด ํ ๋ฌธ์ฅ์ผ๋ก ์ค๋ชํ  ์ ์๋ค
  - component์ UI ์ํ๊ฐ(์ด๊ธฐ ์ํ๊ฐ?)์ ๊ฐ์ง๊ณ  ์๋ **๊ฐ์ฒด**
- ๋ถ๋ชจ ์์์ state ๋ฐ์ดํฐ๋ฅผ ์์ ์์์์ ๋ฐ์์ํฌ ์ ์๋ค
- ์ด๋ฒคํธ๋ฅผ ํตํด state ๋ฐ์ดํฐ๋ฅผ ๋ฐ๊ฟ ์ ์๋ค
  - setState()
- props์ ๊ฐ๋์ ๋ํด ํ ๋ฌธ์ฅ์ผ๋ก ์ค๋ชํ  ์ ์๋ค
  - ๋ถ๋ชจ๋ก๋ถํฐ ๋ฐ์ ๋ฐ์ดํฐ๋ฅผ ์ง๋๊ณ  ์๋ **๊ฐ์ฒด**
  - props๋ ์ฝ๊ธฐ ์ ์ฉ
- `๋ถ๋ชจ state` - `์์์ props` - `์์ component` ์ด๋ป๊ฒ ์ฐ๊ฒฐ๋๋์ง ๋ชํํ ์ดํดํ๋ค
- props ๊ฐ๋์ ํ์ฉํ์ฌ ์์ ์ปดํฌ๋ํธ์์ ์ผ์ด๋ ์ด๋ฒคํธ๋ก ๋ถ๋ชจ์ state ๊ฐ์ ๋ฐ๊ฟ ์ ์๋ค

[React_doc](https://ko.reactjs.org/docs/handling-events.html/)
