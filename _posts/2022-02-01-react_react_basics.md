---
title: "🚀React:: React 시작하기 전,"
tags:
  - [React]
permalink: /study/react/react_basics

navigation: true
toc: true
toc_sticky: true

date: 2022-02-01
last_modified_at: 2022-02-01
---

![](https://images.velog.io/images/april_5/post/707c8c3b-7893-4776-890a-bd897bb78728/React.png)

# React를 시작하기 전에

## ○ React 1 - JSX

### ● JSX란?

- React에서 사용되는 JSX
  `const hi = <p>Hi</p>;`
- javascript도 HTML도 아닌 javascript 확장버전의 문법 _syntax extension for JavaScript_
- JSX는 javascript가 아니기 때문에 `.js`파일에 JSX 문법이 있으면 브라우저는 해석하지 못해 문법 오류가 난다. 이때 바벨을 통해 브라우저가 해석할 수 있도록 컴파일 과정이 필요하다

#### 🔘 JSX element

- HTML문법을 JavaScript 코드 내부에 써주면 그것이 바로 JSX
- 변수에 저장할 수도 있고, 함수의 인자로 넘길 수도 있다

```jsx
const hi = <p>Hi</p>;

const myFavorite = {
  food: <li>샐러드</li>,
  animal: <li>dog</li>,
  hobby: <li>programming</li>,
};
```

<br />

#### 🔘 JSX attribute

- 태그에 attribute(속성)을 주고 싶을 때는 항상 "" 쌍따옴표로 감싸주기
- attribute를 추가하고 싶을 때는 실제 HTML에서 쓰는 attribute name(속성명)과 다를 수 있으니 주의!
  [react 공식문서](https://reactjs.org/docs/dom-elements.html#all-supported-html-attributes/)

```jsx
const hi = <p>Hi</p>;

const myFavorite = {
  food: <li>샐러드</li>,
  animal: <li>dog</li>,
  hobby: <li className='list-item'>programming</li>,
};
```

<br />

#### 🔘 Self-Closing Tag

- JSX에서는 어떤 태그라도 self closing tag가 항상 가능
- `<input>`과 같이 하나의 태그가 요소인 경우에는 `<input />`와 같이 항상 `/`으로 끝내줘야 한다
- `<div />`와 `<div></div>`는 같은 표현

#### 🔘 Nested JSX

**1. (필수) 소괄호로 감싸기**

- 중첩된 요소를 만들려면 () 소괄호로 감싸주기!

```jsx
const good = (
  <>
    {" "}
    //Fragments
    <p>hi</p>
    <p>안녕!</p>
  </>
);
```

<br />

**2. (필수) `Fragments` 항상 하나의 태그로 시작**

- 제일 처음 요소가 sibling이면 안되므로, 무조건 하나의 태그로 감싸져야 한다
  [react_Fragments](https://ko.reactjs.org/docs/fragments.html/)

### ● Rendering

- html 요소(element), 또는 React 요소 등의 코드가 눈으로 볼 수 있도록 그려지는 것을 렌더링(rendering) 이라고 한다
- `ReactDOM.render` 함수를 사용

```jsx
ReactDOM.render(<h1>Hello, world!</h1>, document.getElementById("root"));
```

<br />

---

## ○ React 2 - Component와 Props

### ● Component란?

> component(컴포넌트)란 재사용 가능한 UI 단위

- 컴포넌트는 **독립적**으로, **재사용**가능한 코드로 관리할 수 있다
- 컴포넌트는 함수랑 비슷하다. 함수도 기능이 독립적이고 재사용할 수가 있고 컴포넌트도 `input`을 받아서 `return` 할 수 있다.
- 🚩**집중!** React 컴포넌트에서는 **input을 props**라고 말하고 return은 화면에 보여져야 할 React요소가 return된다

### ● Component 만들기

- component는 `class형`과 `function형`이 있다

#### 🔘 함수로 Welcome 컴포넌트 구현하기

```jsx
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}
```

<br />

#### 🔘 class로 Welcome 컴포넌트 구현하기

- class로 컴포넌트를 만드려면 `React.Component` 를 extend해서 생성
- 컴포넌트를 생성할 때 `render()` 메서드는 **무조건 정의**해야하고, `return`도 해주어야 한다
- `render()` 메서드는 무조건 정의해야한다는 말은, component를 만들 때 필요한 메서드가 원래 더 있다는 뜻. 그런데 **그 중에서 `render()` 만 필수**이다

```jsx
class Welcome extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}</h1>;
  }
}
```

<br />

### ● Component 사용

- function/class 이름으로 사용할 수 있고 태그처럼 `<Welcome />` 으로 작성
- component를 사용할 때엔 원하는 attribute를 추가할 수 있는데 parameter로 해당 attrubute를 받아 사용하는데 이것을 `props`라고 한다
- `props`는 **property의 줄임말**로, `.`(dot)으로 속성명에 접근가능하고, `props.속성명` 으로 속성 값을 가져올 수 있다

```jsx
// 1. Welcome 컴포넌트 정의
// Welcome 컴포넌트를 사용한 측(부모)에서 name이라는 attribute를 부여했고. props.name의 값을 사용
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

// 2. App 컴포넌트 정의
// div로 감싸져있고,
// <Welcome /> 컴포넌트를 세번 사용. name이라는 attribute를 부여했음
function App() {
  return (
    <div>
      <Welcome name='Sara' />
      <Welcome name='Cahal' />
      <Welcome name='Edite' />
    </div>
  );
}

// 3. 화면에 React 요소 그려주기
ReactDOM.render(<App />, document.getElementById("root"));
```

<br />

### ● 더 작은 Component로 분리하기

- 재사용할 가능성이 1이라도 있다면 컴포넌트로 만들어주는 것이 좋다

<br />

---

## ○ React 3-Component의 State

### ● state

> state란?? 말 그대로 컴포넌트의 상태 값
> **state와 props는 둘 다 object** 이고, 화면에 보여줄 정보(상태)를 가지고 있다는 점에서 서로 비슷한 역할을 한다

- props는 컴포넌트를 사용하는 **부모쪽에서 전달해야만** 사용할 수 있고(parameter 처럼)
- state는 **컴포넌트 내**에서 정의하고 사용

```jsx
class Button extends React.Component {
  constructor() {
    super();

    this.state = {
      clicked: false,
    };
  }

  render() {
    return (
      <div
        className='btn'
        // onClick시 this.setState라는 함수를 호출하여 state를 업데이트 한다
        onClick={() => {
          this.setState({ clicked: !this.state.clicked });
        }}
      >
        {this.state.clicked ? "좋아요" : "싫어요"}
      </div>
    );
  }
}

ReactDOM.render(<Button />, document.getElementById("root"));
```

<br />

#### 🔘 `constructor()`

- constructor는 class의 instance가 생성될 때 항상 호출되는 함수(생성자)
- 초기화할 값들을 constructor에서 세팅
- super() 라는 키워드는 꼭 작성필요!!! 그래야 React.Component class에 있는 메서드들(ex. render)을 사용할 수 있다

### ● props와 state

- `this.props.type`이 'like'이면 `like-btn`이라는 클래스 속성이 추가
  [코드보기](https://codepen.io/yeri-kim/pen/axKQMd/)

<br />

---

## ○ React 4 - React 컴포넌트의 Lifecycle

![](https://images.velog.io/images/april_5/post/02e6831f-252c-49b3-82fa-7b7e2eea22db/react-component-lifecycle.png)

- `render`, `componentDidMount`, `componentDidUpdate`, `componentWillUnmount` 등의 함수는 `React.Component` class에서 제공하는 메서드
- 컴포넌트를 만들 때 class로 생성하면 이런 메서드를 사용할 수 있고, 컴포넌트가 lifecycle에 따라 각자의 메서드가 호출된다

![](https://images.velog.io/images/april_5/post/ed68b033-eba4-45ea-9952-173f37eda6aa/react-component-lifecycle2.png)

---

## ○ React 5 - 이벤트 핸들링

### ●React에서는 React element에 `onClick` 이벤트를 추가해서 event handler 함수를 넘겨준다

```jsx
class Button extends React.Component {
  constructor() {
    super();

    this.state = {
      clicked: false,
    };

    this.handleClick = this.handleClick.bind(this);
  }

  handleClick() {
    this.setState({
      clicked: !this.state.clicked,
    });
  }

  render() {
    return (
      <div
        className={`btn ${this.props.type === "like" ? "like-btn" : ""}`}
        onClick={this.handleClick}
      >
        {this.state.clicked ? "좋아요" : "싫어요"}
      </div>
    );
  }
}

ReactDOM.render(<Button type='like' />, document.getElementById("root"));
```

<br />

#### 🔘 React 요소에 이벤트를 추가할 경우 bind(this)를 해줘야한다

- 이벤트에 event handler 함수를 넘길때 `bind`를 해주지 않으면 event handler 함수내에서 `this`의 `context`를 잃어버려서 this가 `undefined`가 된다
- handleClick 메서드 내에서 `this` 키워드를 사용하고 있는데, 이 this는 Button 컴포넌트의 `context`여야 한다
- handleClick.bind(this)라고 작성해준 위치에서 그 this를 handleClick 에 넘겨서 handleClick 메서드 내에서도 같은 this를 쓰겠다는 뜻이다
- 그래야만 Button 컴포넌트의 `this.state`에 접근하고, `setState` 함수도 쓸 수 있기 때문

> ✨참고✨ **context**

- context는 React 컴포넌트 트리 안에서 전역적(global)이라고 볼 수 있는 데이터를 공유할 수 있도록 고안된 방법 [react_context](https://ko.reactjs.org/docs/context.html/)

<br />

<br />
