---
title: "🚀React:: React 리덕스로 상태 관리하기"
tags:
  - [React]
permalink: /study/react/redux

navigation: true
toc: true
toc_sticky: true

date: 2022-03-12
last_modified_at: 2022-03-12
---

![](https://images.velog.io/images/april_5/post/97b9b2a4-994b-4e19-951e-80f582381616/image.png)

`개인 공부를 위해 작성했습니다`

자바스크립트를 위한 <span style="color:#7F42C3">**상태 관리 라이브러리, 리덕스👍**</span>
리액트를 사용하는 많은 프로젝트에서 리덕스도 같이 사용하는데, 그 이유는

- 컴포넌트 코드와 상태 관리 코드의 분리가 가능하고
- SSR시 데이터 전달이 간편하다
- 리액트 컨텍스트보다 효율적인 렌더링이 가능하다
- 미들웨어를 활용한 다양한 기능 추가도 가능하다
  - 강력한 미들웨어 라이브러리 (ex. redux-saga)
  - 로컬 스토리지에 데이터 저장하고 불러오는 코드를 쉽게 작성할 수 있다

이런 이유로 공부한 react-redux에 대해 정리해본다.

---

# 리덕스로 상태 관리하기

## 리덕스 사용 시 따라야 할 세 가지 원칙

### 1. 전체 상태값을 <span style="color:#7F42C3">**하나의 `store` 객체에 저장**</span>한다

전체 상태값이 하나의 자바스크립트 객체로 표현되기 때문에 활용도가 높아진다. 리덕스를 사용하면

- 하나의 객체를 직렬화(serialize)해서 <span style="color:dodgerblue">**서버와 클라이언트가 프로그램 전체 상태값을 서로 주고 받을 수 있고**</span>
- 프로그램이 특정한 상태에 있을 때 발생하는 <span style="color:dodgerblue">**버그를 확인하기 위해 그 상태값을 저장한 후 반복해서 재현**</span>할 수 있다
- 최근의 상태값을 버리지 않고 저장해 놓으면 실행 취소(undo)와 다시 실행(redo) 기능을 쉽게 구현할 수 있다

<br />

### 2. 상태값은 <span style="color:#7F42C3">**불변 객체**</span>이다

상태값은 오직 <span style="color:dodgerblue">**액션 객체에 의해서만 변경**</span>되어야 한다

```js
const incrementAction = {
  type: "INCREMENT", // --------------(1)
  amount: 123, // --------------(2)
};

store.dispatch(incrementAction); // --(3)
```

<br />

`incrementAction`라는 이름의 **액션 객체**를 살펴보면,
(1) 액션 객체는 `type` 속성값이 존재해야 한다. `type` 속성값으로 액션 객체를 구분한다.
(2) `type` 속성값을 제외하면 나머지는 상태값을 수정하기 위해 사용되는 정보다
(3) 액션 객체와 함께 `dispatch` 메서드를 호출하면 상태값이 변경된다.

리덕스의 상태값을 수정하는 유일한 방법은 `액션 객체`와 `dispatch` 메서드를 호출하는 것이다. <span style="color:red">**다른 방법으로 상태값을 수정하면 안 된다**</span>.

상태값은 `dispatch` 메서드가 <span style="color:dodgerblue">**호출된 순서대로 리덕스 내부에서 변경**</span>된다

*불변 객체를 사용하는 이유*는, **이전 상태값과 이후 상태값을 비교해서 변경** 여부를 파악할 때 유리하기 때문이다. 불변 객체를 사용하지 않고 직접 상태값을 수정하게 되면 이전 상태값 비교가 어렵다.

<br />

### 3. 상태값은 <span style="color:#7F42C3">**순수 함수**</span>에 의해서만 변경되어야 한다

> **리듀서(reducer)**: 리덕스에서 상태값을 변경하는 함수
> (state, action) => nextState

리듀서는 <span style="color:#7F42C3">**이전 상태값**</span>과 <span style="color:#7F42C3">**액션 객체**</span>를 입력받아 새로운 상태값을 만드는 <span style="color:#7F42C3">**순수 함수**</span>이다.

순수 함수는

- `side effect`(전역 변수의 값을 수정하거나 API 요청을 보내는 등 함수 외부의 상태를 변경시키는 것)를 발생시키지 않아야 하고,
- 같은 인수에 대해 항상 같은 값을 반환해야 한다.
  - 랜덤 함수나 시간 함수를 이용하면 순수 함수가 아니다.
  - 같은 인수를 입력해도 호출하는 시점에 따라 다른 값을 반환하기 때문이다.

이러한 특성 덕분에 순수 함수는 테스트 코드를 작성하기 쉽다.

<br />

---

## 리덕스의 주요 개념

- 상태값이 변경되는 과정

![](https://images.velog.io/images/april_5/post/02ab76ad-734b-49d8-a1bd-61191a07bb9f/image.png)

`뷰(컴포넌트)`가 상태값을 변경하고 싶을 때는 액션을 발생시킨다.
`액션`은 `미들웨어`가 처리하고 (미들웨어에 원하는 기능 추가도 가능하다)
`리듀서`는 액션에 의해서 상태값이 어떻게 변경되는지 로직을 담고 있다. 리듀서는 새로은 상태값을 출력하는데, 그 새로운 상태값을
`스토어`에게 알려주면 스토어는 상태값을 저장한다. 변경된 상태값을 다시 뷰에게 알려준다.

<br />

### 🌈 상태값을 변경하는 과정에서 거치게 되는 4가지 요소

- 🚩 **액션**
  - `dispatch`는 액션이 발생했다는 것을 리덕스에게 알려주는 함수
  - (2) `action creator`를 만들어서 사용하는 이유는, 각 액션 객체의 구조를 일관성 있게 작성하기 위함
  - (3) 액션 `type`을 상수 변수로 관리하는 이유는,
    - `action creator` 에서도 사용하지만
    - `reducer` 에서도 사용하기 때문

```js
// (1) dispatch()를 호출할 때 액션 객체를 직접 입력한 case
store.dispatch({
  type: 'todo/ADD'  // type: 액션을 구분하는 속성값이므로 고유해야 한다.
  title: '리덕스 공부하기'
});

// (2) action creator 함수를 만들어서 호출한 case
const ADD = 'todo/ADD' // (3) 액션 type을 상수 변수로 관리

function addTodo(title) {
  return { type: ADD, title }
}

store.dispatch(addTodo({ title: '리덕스 공부하기' }))
```

<br />

- 🚩 **미들웨어**

  > **미들웨어(middleware)**는 리듀서가 액션을 처리하기 전에 실행하는 함수

  - 미들웨어의 기본 구조
    - 함수 세 개가 중첩된 구조로 되어있다.

```js
// 미들웨어의 기본 구조: 화살표 사용
const myMiddleware = (store) => (next) => (action) => next(action);

// 미들웨어의 기본 구조: 화살표 사용X
const myMiddleware = function (store) {
  return function (next) {
    return function (action) {
      return next(action);
    };
  };
};
```

<br />

🌱 미들웨어 작성 예제

```js
const middleware1 = (store) => (next) => (action) => {
  console.log("middleware1 start"); // (2)
  const result = next(action); // (3)
  console.log("middleware1 end"); // (8)
  return result;
};

const middleware2 = (store) => (next) => (action) => {
  console.log("middleware2 start"); // (4)
  const result = next(action); // (5)
  console.log("middleware2 end"); // (7)
  return result;
};

const myReducer = (state, action) => {
  console.log("myReducer"); // (6)
  return state;
};

const store = createStore(myReducer, applyMiddleware(middleware1, middleware2));
store.dispatch({ type: "someAction" }); // (1)
```

<br />

(1) 액션이 발생했을 때 미들웨어부터 처리가 된다.
첫 번째 미들웨어 `middleware1`가 실행되고 (2)가 출력된다. 그 다음 줄의 (3)`next`를 호출했을 때 (4)이 출력된다.
(3)`next`는 `middleware2`를 의미한다.
(5)`next`는 없기 때문에 (5)`next`는 `reducer`를 호출한다.
그래서 (6)를 출력하게 되고 (5)`next`인 `myReducer()`가 종료되면서 (7)이 출력되고 (8)이 출력된다.

![](https://images.velog.io/images/april_5/post/6bcbb2e1-957b-4379-848f-21976beb1d71/image.png)

즉, 미들웨어의 순서대로 호출되고 next를 호출하면서 다음 미들웨어를 호출하게 되고 마지막 미들웨어에서는 리듀서를 호출한다.

상태값 변경을 검사하는 코드는 각 이벤트 처리 함수에서 구현해야 하는데, `react-redux` 패키지의 `connect`함수에서는 자체적으로 상태값 변경을 검사한다.

- 🚩 **리듀서**

  > **리듀서(reducer)**는 액션에 발생했을 때 새로운 상태값을 만드는 함수다

  - 리듀서의 기본 구조

```js
(state, action) => nextState;
```

<br />

🌱 리듀서 작성 예제

```js
function reducer(state = INITIAL_STATE, action) { // (1) state = INITIAL_STATE
  switch (action.type){ // (2) 액션 타입별 case로 처리
    case REMOVE_ALL :
      return { ...state, todos: [] } // (3) 불변 객체로 관리
    case REMOVE :
      return { ...state, todos state.todos.filter(todo => todo.id !== action.id) }
    default :
      return state; // (4)
  }
}

const INITIAL_STATE = { todos: [] }
```

<br />

리덕스는 스토어를 호출할 때 상태값이 없는 상태로 리듀서를 호출하므로
(1) 매개변수의 기본값을 사용해서 초기 상태값을 정의한다.
(2) 각 액션 타입별로 `switch case`문을 만들어서 처리한다.
(3) 상태값은 불변 객체로 관리해야 하므로 수정할 때 마다 새로운 객체를 생성한다.
(4) 처리할 액션이 없다면 상태값을 변경하지 않는다.

불변 객체를 관리할 목적으로 <span style="color:#7F42C3">**이머(immer)**</span> 패키지를 사용한다

🌱 이머(immer)를 사용해서 불변 객체를 관리하는 예제

```js
import produce from "immer";

const person = { name: "yurim", age: 20 };
const newPerson = produce(person, (draft) => {
  // (1)
  draft.age = 30;
});
```

<br />

(1) `produce()`의 첫 번째 인자는 변경하고자 하는 객체,
두 번째 인자는 첫 번째 인자로 받은 객체를 수정하는 함수
`draft` 객체를 수정하면 `produce()`가 새로운 객체를 반환한다.

🌱 이머(immer)를 사용해서 예제 코드 리펙토링 하기

```js
function reducer(state = INITIAL_STATE, action) {
  return produce(state, draft => {
    switch (action.type){
      case ADD :
        return { draft.todos.push(action.todo) } // (1)
      case REMOVE_ALL :
        return { draft.todos = [] }
      case REMOVE :
        return { draft.todos = draft.todos.filter(todo => todo.id !== action.id) }
      default :
        return state;
    }
  })
}

const INITIAL_STATE = { todos: [] }
```

<br />

(1) `draft`가 새로운 객체를 반환하므로, `push`메서드를 사용해도 기존 상태값은 직접 수정되지 않는다.

🌱 `createReducer()`로 리듀서 작성하기
`switch`문 보다 더 간결하게 리듀서 함수를 작성할 수 있다

```js
function reducer(state = INITIAL_STATE, { // (1)
  [ADD]: (state, action) => state.todos.push(action.todo),
  [REMOVE_ALL]: state => ( state.todos = [] ),
  [REMOVE]: (state, action) => (state.todos = state.todos.filter(todo => todo.id !== action.id))
})
```

<br />

첫 번째 인자로 초기값을 받고,
(1) 두 번째 인자로 액션 처리 함수를 담고 있는 객체를 받는다.

- 🚩 **스토어**

  > **스토어(store)**는 리덕스의 상태값을 가지는 객체.
  > 액션의 발생은 스토어의 dispatch()로 시작된다

- 리덕스의 첫 번째 원칙에 따라 전체 상태값을 하나의 `store` 객체에 저장한다.
- 하지만 여러개의 `store` 객체를 사용해도 문제가 되지 않는다.
- 단순히 데이터 종류에 따라 구분하기 위한 용도라면 `combineReducer()`를 사용하면 된다.
- 특별한 이유가 없다면 스토어는 하나만 만드는 게 좋다.

<br />

---

### ✨ tl;dr

리덕스는

- 전체 상태값을 하나의 `store` 객체에 저장한다.
- **액션 객체**로 상태값 변경이 가능한데,
  - 액션 객체는 `type`속성값으로 액션 객체를 구분한다.
  - 액션 객체와 함께 `dispatch` 메서드로 상태값을 변경한다
- **미들웨어**는 리듀서가 액션을 처리하기 전에 실행하는 함수다.
  - 데이터를 처리하는 중간 과정에서 로직을 넣어서 필요한 기능을 추가할 수 있다 (ex. redux-saga)
    - 디버깅 목적으로 상태값 변경 시 로그를 출력하거나
    - 리듀서에서 발생한 예외를 서버로 전송하는 등의 목적으로 미들웨어가 활용된다.
- **리듀서**는 액션이 발생했을 때 새로운 상태값을 만드는 함수.
  - <span style="color:#7F42C3">**리덕스의 상태값을 수정하는 유일한 방법**</span>은
    - 액션 객체와 `dispatch` 메서드를 호출하는 것이다.
  - 불변 객체를 관리할 목적으로 `이머(immer)` 패키지를 사용한다
  - 리듀서 작성 시 주의할 점
    - 데이터 참조: 리덕스의 상태값은 불변 객체이기 때문에 언제든지 객체의 참조값이 변경될 수 있으므로 객체를 참조할 때는 고유한 ID값을 이용하는게 좋다
    - 순수 함수: 랜덤함수, 시간함수 등 호출하는 시점에 따라 다른 값이 반환될 수 있으므로 사용하면 안 된다.
- **스토어**는 리덕스의 상태값을 가지는 객체. 액션의 발생은 스토어의 dispatch()로 시작된다
- 리덕스는 <span style="color:#7F42C3">**단방향 데이터 흐름**</span>의 특성을 지니기 때문에 <span style="color:#7F42C3">**상당히 직관적이고 예측 가능하다는 장점**</span>이 있다. (간단하고 직관적인 구조)
