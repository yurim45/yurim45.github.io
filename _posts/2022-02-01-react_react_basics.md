---
title: "๐React:: React ์์ํ๊ธฐ ์ ,"
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

# React๋ฅผ ์์ํ๊ธฐ ์ ์

## โ React 1 - JSX

### โ JSX๋?

- React์์ ์ฌ์ฉ๋๋ JSX
  `const hi = <p>Hi</p>;`
- javascript๋ HTML๋ ์๋ javascript ํ์ฅ๋ฒ์ ์ ๋ฌธ๋ฒ _syntax extension for JavaScript_
- JSX๋ javascript๊ฐ ์๋๊ธฐ ๋๋ฌธ์ `.js`ํ์ผ์ JSX ๋ฌธ๋ฒ์ด ์์ผ๋ฉด ๋ธ๋ผ์ฐ์ ๋ ํด์ํ์ง ๋ชปํด ๋ฌธ๋ฒ ์ค๋ฅ๊ฐ ๋๋ค. ์ด๋ ๋ฐ๋ฒจ์ ํตํด ๋ธ๋ผ์ฐ์ ๊ฐ ํด์ํ  ์ ์๋๋ก ์ปดํ์ผ ๊ณผ์ ์ด ํ์ํ๋ค

#### ๐ JSX element

- HTML๋ฌธ๋ฒ์ JavaScript ์ฝ๋ ๋ด๋ถ์ ์จ์ฃผ๋ฉด ๊ทธ๊ฒ์ด ๋ฐ๋ก JSX
- ๋ณ์์ ์ ์ฅํ  ์๋ ์๊ณ , ํจ์์ ์ธ์๋ก ๋๊ธธ ์๋ ์๋ค

```jsx
const hi = <p>Hi</p>;

const myFavorite = {
  food: <li>์๋ฌ๋</li>,
  animal: <li>dog</li>,
  hobby: <li>programming</li>,
};
```

<br />

#### ๐ JSX attribute

- ํ๊ทธ์ attribute(์์ฑ)์ ์ฃผ๊ณ  ์ถ์ ๋๋ ํญ์ "" ์๋ฐ์ดํ๋ก ๊ฐ์ธ์ฃผ๊ธฐ
- attribute๋ฅผ ์ถ๊ฐํ๊ณ  ์ถ์ ๋๋ ์ค์  HTML์์ ์ฐ๋ attribute name(์์ฑ๋ช)๊ณผ ๋ค๋ฅผ ์ ์์ผ๋ ์ฃผ์!
  [react ๊ณต์๋ฌธ์](https://reactjs.org/docs/dom-elements.html#all-supported-html-attributes/)

```jsx
const hi = <p>Hi</p>;

const myFavorite = {
  food: <li>์๋ฌ๋</li>,
  animal: <li>dog</li>,
  hobby: <li className='list-item'>programming</li>,
};
```

<br />

#### ๐ Self-Closing Tag

- JSX์์๋ ์ด๋ค ํ๊ทธ๋ผ๋ self closing tag๊ฐ ํญ์ ๊ฐ๋ฅ
- `<input>`๊ณผ ๊ฐ์ด ํ๋์ ํ๊ทธ๊ฐ ์์์ธ ๊ฒฝ์ฐ์๋ `<input />`์ ๊ฐ์ด ํญ์ `/`์ผ๋ก ๋๋ด์ค์ผ ํ๋ค
- `<div />`์ `<div></div>`๋ ๊ฐ์ ํํ

#### ๐ Nested JSX

**1. (ํ์) ์๊ดํธ๋ก ๊ฐ์ธ๊ธฐ**

- ์ค์ฒฉ๋ ์์๋ฅผ ๋ง๋ค๋ ค๋ฉด () ์๊ดํธ๋ก ๊ฐ์ธ์ฃผ๊ธฐ!

```jsx
const good = (
  <>
    {" "}
    //Fragments
    <p>hi</p>
    <p>์๋!</p>
  </>
);
```

<br />

**2. (ํ์) `Fragments` ํญ์ ํ๋์ ํ๊ทธ๋ก ์์**

- ์ ์ผ ์ฒ์ ์์๊ฐ sibling์ด๋ฉด ์๋๋ฏ๋ก, ๋ฌด์กฐ๊ฑด ํ๋์ ํ๊ทธ๋ก ๊ฐ์ธ์ ธ์ผ ํ๋ค
  [react_Fragments](https://ko.reactjs.org/docs/fragments.html/)

### โ Rendering

- html ์์(element), ๋๋ React ์์ ๋ฑ์ ์ฝ๋๊ฐ ๋์ผ๋ก ๋ณผ ์ ์๋๋ก ๊ทธ๋ ค์ง๋ ๊ฒ์ ๋ ๋๋ง(rendering) ์ด๋ผ๊ณ  ํ๋ค
- `ReactDOM.render` ํจ์๋ฅผ ์ฌ์ฉ

```jsx
ReactDOM.render(<h1>Hello, world!</h1>, document.getElementById("root"));
```

<br />

---

## โ React 2 - Component์ Props

### โ Component๋?

> component(์ปดํฌ๋ํธ)๋ ์ฌ์ฌ์ฉ ๊ฐ๋ฅํ UI ๋จ์

- ์ปดํฌ๋ํธ๋ **๋๋ฆฝ์ **์ผ๋ก, **์ฌ์ฌ์ฉ**๊ฐ๋ฅํ ์ฝ๋๋ก ๊ด๋ฆฌํ  ์ ์๋ค
- ์ปดํฌ๋ํธ๋ ํจ์๋ ๋น์ทํ๋ค. ํจ์๋ ๊ธฐ๋ฅ์ด ๋๋ฆฝ์ ์ด๊ณ  ์ฌ์ฌ์ฉํ  ์๊ฐ ์๊ณ  ์ปดํฌ๋ํธ๋ `input`์ ๋ฐ์์ `return` ํ  ์ ์๋ค.
- ๐ฉ**์ง์ค!** React ์ปดํฌ๋ํธ์์๋ **input์ props**๋ผ๊ณ  ๋งํ๊ณ  return์ ํ๋ฉด์ ๋ณด์ฌ์ ธ์ผ ํ  React์์๊ฐ return๋๋ค

### โ Component ๋ง๋ค๊ธฐ

- component๋ `classํ`๊ณผ `functionํ`์ด ์๋ค

#### ๐ ํจ์๋ก Welcome ์ปดํฌ๋ํธ ๊ตฌํํ๊ธฐ

```jsx
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}
```

<br />

#### ๐ class๋ก Welcome ์ปดํฌ๋ํธ ๊ตฌํํ๊ธฐ

- class๋ก ์ปดํฌ๋ํธ๋ฅผ ๋ง๋๋ ค๋ฉด `React.Component` ๋ฅผ extendํด์ ์์ฑ
- ์ปดํฌ๋ํธ๋ฅผ ์์ฑํ  ๋ `render()` ๋ฉ์๋๋ **๋ฌด์กฐ๊ฑด ์ ์**ํด์ผํ๊ณ , `return`๋ ํด์ฃผ์ด์ผ ํ๋ค
- `render()` ๋ฉ์๋๋ ๋ฌด์กฐ๊ฑด ์ ์ํด์ผํ๋ค๋ ๋ง์, component๋ฅผ ๋ง๋ค ๋ ํ์ํ ๋ฉ์๋๊ฐ ์๋ ๋ ์๋ค๋ ๋ป. ๊ทธ๋ฐ๋ฐ **๊ทธ ์ค์์ `render()` ๋ง ํ์**์ด๋ค

```jsx
class Welcome extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}</h1>;
  }
}
```

<br />

### โ Component ์ฌ์ฉ

- function/class ์ด๋ฆ์ผ๋ก ์ฌ์ฉํ  ์ ์๊ณ  ํ๊ทธ์ฒ๋ผ `<Welcome />` ์ผ๋ก ์์ฑ
- component๋ฅผ ์ฌ์ฉํ  ๋์ ์ํ๋ attribute๋ฅผ ์ถ๊ฐํ  ์ ์๋๋ฐ parameter๋ก ํด๋น attrubute๋ฅผ ๋ฐ์ ์ฌ์ฉํ๋๋ฐ ์ด๊ฒ์ `props`๋ผ๊ณ  ํ๋ค
- `props`๋ **property์ ์ค์๋ง**๋ก, `.`(dot)์ผ๋ก ์์ฑ๋ช์ ์ ๊ทผ๊ฐ๋ฅํ๊ณ , `props.์์ฑ๋ช` ์ผ๋ก ์์ฑ ๊ฐ์ ๊ฐ์ ธ์ฌ ์ ์๋ค

```jsx
// 1. Welcome ์ปดํฌ๋ํธ ์ ์
// Welcome ์ปดํฌ๋ํธ๋ฅผ ์ฌ์ฉํ ์ธก(๋ถ๋ชจ)์์ name์ด๋ผ๋ attribute๋ฅผ ๋ถ์ฌํ๊ณ . props.name์ ๊ฐ์ ์ฌ์ฉ
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

// 2. App ์ปดํฌ๋ํธ ์ ์
// div๋ก ๊ฐ์ธ์ ธ์๊ณ ,
// <Welcome /> ์ปดํฌ๋ํธ๋ฅผ ์ธ๋ฒ ์ฌ์ฉ. name์ด๋ผ๋ attribute๋ฅผ ๋ถ์ฌํ์
function App() {
  return (
    <div>
      <Welcome name='Sara' />
      <Welcome name='Cahal' />
      <Welcome name='Edite' />
    </div>
  );
}

// 3. ํ๋ฉด์ React ์์ ๊ทธ๋ ค์ฃผ๊ธฐ
ReactDOM.render(<App />, document.getElementById("root"));
```

<br />

### โ ๋ ์์ Component๋ก ๋ถ๋ฆฌํ๊ธฐ

- ์ฌ์ฌ์ฉํ  ๊ฐ๋ฅ์ฑ์ด 1์ด๋ผ๋ ์๋ค๋ฉด ์ปดํฌ๋ํธ๋ก ๋ง๋ค์ด์ฃผ๋ ๊ฒ์ด ์ข๋ค

<br />

---

## โ React 3-Component์ State

### โ state

> state๋?? ๋ง ๊ทธ๋๋ก ์ปดํฌ๋ํธ์ ์ํ ๊ฐ
> **state์ props๋ ๋ ๋ค object** ์ด๊ณ , ํ๋ฉด์ ๋ณด์ฌ์ค ์ ๋ณด(์ํ)๋ฅผ ๊ฐ์ง๊ณ  ์๋ค๋ ์ ์์ ์๋ก ๋น์ทํ ์ญํ ์ ํ๋ค

- props๋ ์ปดํฌ๋ํธ๋ฅผ ์ฌ์ฉํ๋ **๋ถ๋ชจ์ชฝ์์ ์ ๋ฌํด์ผ๋ง** ์ฌ์ฉํ  ์ ์๊ณ (parameter ์ฒ๋ผ)
- state๋ **์ปดํฌ๋ํธ ๋ด**์์ ์ ์ํ๊ณ  ์ฌ์ฉ

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
        // onClick์ this.setState๋ผ๋ ํจ์๋ฅผ ํธ์ถํ์ฌ state๋ฅผ ์๋ฐ์ดํธ ํ๋ค
        onClick={() => {
          this.setState({ clicked: !this.state.clicked });
        }}
      >
        {this.state.clicked ? "์ข์์" : "์ซ์ด์"}
      </div>
    );
  }
}

ReactDOM.render(<Button />, document.getElementById("root"));
```

<br />

#### ๐ `constructor()`

- constructor๋ class์ instance๊ฐ ์์ฑ๋  ๋ ํญ์ ํธ์ถ๋๋ ํจ์(์์ฑ์)
- ์ด๊ธฐํํ  ๊ฐ๋ค์ constructor์์ ์ธํ
- super() ๋ผ๋ ํค์๋๋ ๊ผญ ์์ฑํ์!!! ๊ทธ๋์ผ React.Component class์ ์๋ ๋ฉ์๋๋ค(ex. render)์ ์ฌ์ฉํ  ์ ์๋ค

### โ props์ state

- `this.props.type`์ด 'like'์ด๋ฉด `like-btn`์ด๋ผ๋ ํด๋์ค ์์ฑ์ด ์ถ๊ฐ
  [์ฝ๋๋ณด๊ธฐ](https://codepen.io/yeri-kim/pen/axKQMd/)

<br />

---

## โ React 4 - React ์ปดํฌ๋ํธ์ Lifecycle

![](https://images.velog.io/images/april_5/post/02e6831f-252c-49b3-82fa-7b7e2eea22db/react-component-lifecycle.png)

- `render`, `componentDidMount`, `componentDidUpdate`, `componentWillUnmount` ๋ฑ์ ํจ์๋ `React.Component` class์์ ์ ๊ณตํ๋ ๋ฉ์๋
- ์ปดํฌ๋ํธ๋ฅผ ๋ง๋ค ๋ class๋ก ์์ฑํ๋ฉด ์ด๋ฐ ๋ฉ์๋๋ฅผ ์ฌ์ฉํ  ์ ์๊ณ , ์ปดํฌ๋ํธ๊ฐ lifecycle์ ๋ฐ๋ผ ๊ฐ์์ ๋ฉ์๋๊ฐ ํธ์ถ๋๋ค

![](https://images.velog.io/images/april_5/post/ed68b033-eba4-45ea-9952-173f37eda6aa/react-component-lifecycle2.png)

---

## โ React 5 - ์ด๋ฒคํธ ํธ๋ค๋ง

### โReact์์๋ React element์ `onClick` ์ด๋ฒคํธ๋ฅผ ์ถ๊ฐํด์ event handler ํจ์๋ฅผ ๋๊ฒจ์ค๋ค

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
        {this.state.clicked ? "์ข์์" : "์ซ์ด์"}
      </div>
    );
  }
}

ReactDOM.render(<Button type='like' />, document.getElementById("root"));
```

<br />

#### ๐ React ์์์ ์ด๋ฒคํธ๋ฅผ ์ถ๊ฐํ  ๊ฒฝ์ฐ bind(this)๋ฅผ ํด์ค์ผํ๋ค

- ์ด๋ฒคํธ์ event handler ํจ์๋ฅผ ๋๊ธธ๋ `bind`๋ฅผ ํด์ฃผ์ง ์์ผ๋ฉด event handler ํจ์๋ด์์ `this`์ `context`๋ฅผ ์์ด๋ฒ๋ ค์ this๊ฐ `undefined`๊ฐ ๋๋ค
- handleClick ๋ฉ์๋ ๋ด์์ `this` ํค์๋๋ฅผ ์ฌ์ฉํ๊ณ  ์๋๋ฐ, ์ด this๋ Button ์ปดํฌ๋ํธ์ `context`์ฌ์ผ ํ๋ค
- handleClick.bind(this)๋ผ๊ณ  ์์ฑํด์ค ์์น์์ ๊ทธ this๋ฅผ handleClick ์ ๋๊ฒจ์ handleClick ๋ฉ์๋ ๋ด์์๋ ๊ฐ์ this๋ฅผ ์ฐ๊ฒ ๋ค๋ ๋ป์ด๋ค
- ๊ทธ๋์ผ๋ง Button ์ปดํฌ๋ํธ์ `this.state`์ ์ ๊ทผํ๊ณ , `setState` ํจ์๋ ์ธ ์ ์๊ธฐ ๋๋ฌธ

> โจ์ฐธ๊ณ โจ **context**

- context๋ React ์ปดํฌ๋ํธ ํธ๋ฆฌ ์์์ ์ ์ญ์ (global)์ด๋ผ๊ณ  ๋ณผ ์ ์๋ ๋ฐ์ดํฐ๋ฅผ ๊ณต์ ํ  ์ ์๋๋ก ๊ณ ์๋ ๋ฐฉ๋ฒ [react_context](https://ko.reactjs.org/docs/context.html/)

<br />

<br />
