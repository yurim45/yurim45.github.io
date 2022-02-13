---
title: "🚀React:: State🔅 & Props✨ &Event"
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

## ○ State🔅 & Event

> state : 상태
> 화면에 보여줄 컴포넌트의 **UI 정보(상태)**를 지니고 있는 **객체**

<br />

### ● `State` 객체

    - `constructor()` 에 위치. `constructor()`는 페이지가 렌더될 때 초기화되는 값들

```jsx
constructor() {
    super();
    this.state = {
      color: 'red',
    };
  }

<h1 style={{ color: this.state.color }} >Class Component | State</h1>

// this : 해당 컴포넌트
// this.state : 해당 컴포넌트의 state 객체
// this.state.color : state 객체의 특정 key(color)값. 즉 "red"
```

<br />

### ● `setState()`

- `constructor()`에서 선언된 state의 값을 변경할 때 사용

```jsx
import React, { Component } from "react";

class State extends Component {
  constructor() {
    super();
    this.state = {
      color: "red",
    };
  }

  // `handleColor`함수를 호출할 때 state의 값을 변경하겠다 = setState
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

## ○ Props & Event

> props : properties(속성)
> props는 **부모 component로부터 전달 받은 *데이터*를 지니고 있는 객체**

<br />

### ●props 객체

- **Parent.js**
  - 부모 component에서 자식 component로 state값을 전달하기 위한 준비
    - `<Child titleColor={this.state.color}/>` `titleColor`라는 Attribute를 임의로 지정하여 `state` 객체의 `color`값을 전달

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
  - <Child /> 컴포넌트 내부에서 전달 받은 props 데이터를 어떻게 사용할까?
    - `{color : this.props.titleColor}` 전달받은 `props` 객체의 `titleColor`값

```jsx
// Child.js
import React from "react";

class Child extends React.Component {
  render() {
    // console.log(this.props); 부모로 부터 전달받은 props값 확인
    return (
      <div>
        <h1 style={{ color: this.props.titleColor }}>Child Component</h1>
        // this : 해당 컴포넌트 // this.props : 해당 컴포넌트의 props 객체 // this.props.titleColor
        : props 객체의 특정 key(titleColor)값. 즉 "red"
      </div>
    );
  }
}

export default State;
```

<br />

### ● `Props & event`

- 자식에게 전달할 state값과 함수를 선언
  - `state`는 `titleColor`라는 Attribute를 통해 전달
  - `handleColor` 메서드는 `changeColor`라는 Attribute를 통해 전달

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

- 부모에게 전달받은 props를
  - `h1`의 스타일링에서 사용 `style={{color : this.props.titleColor}}`
  - `button`의 `onClick` 이벤트 발생시 함수 호출 `onClick= this.props.changeColor}`

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

✅ 목표!

- state의 개념에 대해 한 문장으로 설명할 수 있다
  - component의 UI 상태값(초기 셋팅값?)을 가지고 있는 **객체**
- 부모 요소의 state 데이터를 자식 요소에서 반영시킬 수 있다
- 이벤트를 통해 state 데이터를 바꿀 수 있다
  - setState()
- props의 개념에 대해 한 문장으로 설명할 수 있다
  - 부모로부터 받은 데이터를 지니고 있는 **객체**
  - props는 읽기 전용
- `부모 state` - `자식의 props` - `자식 component` 어떻게 연결되는지 명확히 이해한다
- props 개념을 활용하여 자식 컴포넌트에서 일어난 이벤트로 부모의 state 값을 바꿀 수 있다

[React_doc](https://ko.reactjs.org/docs/handling-events.html/)
