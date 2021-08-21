---
title: "🐯CoreJS:: Javascript this"
tags:
  - [Javascript]
permalink: /study/JS/this

navigation: true
toc: true
toc_sticky: true

date: 2021-07-16
last_modified_at: 2021-07-16
---

![]()

`주니어 개발자의 개인 공부 과정을 기록합니다.`

---

자바스크립트의 가장 혼란스로운 개념? <span style="color:dodgerblue">**this**</span>?

다른 대부분의 객체지향 언어에서 `this`는 클래스로 생성한 인스턴스 객체를 의미한다. 클래스에서만 사용할 수 있기 때문에 혼란의 여지가 많지는 않다.

하지만 자바스크립트에서의 `this`는 어디서든 사용할 수 있고, `this`가 바라보는 대상이 <span style="color:dodgerblue">**상황에 따라 바라보는 대상이 달라진다**</span>

함수와 객체(메서드)의 구분이 느슨한 자바스크립트에서
`this`는 실질적으로 이 둘을 구분하는 거의 유일한 기능이다.

<br />

---

# 상황에 따라 달라지는 `this`
자바스크립트에서 `this`는 기본적으로 실행 컨텍스트가 생성될 때 함께 결정된다.
실행 컨텍스트는 함수를 호출할 때 생성되므로.`this`는 함수를 호출할 때 결정된다고 할 수 있다.

함수를 호출하는 방식에 따라 값이 달라지는데
- 전역 공간에서의 `this`
- 메서드로서 호출할 때 그 메서드 내부에서의 `this`
- 함수로서 호출할 때 그 함수 내부에서의 `this`
- 콜백 함수 호출 시 그 함수 내부에서의 `this`
- 생성자 함수 내부에서의 `this`
이 있다


## 🔹 전역 공간에서의 `this`

>전역 공간에서 `this`는 전역 객체를 가리킨다.
개념상 전역 컨텍스트를 생성하는 주체가 바로 전역 객체이기 때문이다.

전역 객체는
- 자바스크립트 **런타임 환경에 따라 다른 이름과 정보**를 가지고 있다
  - 브라우저 환경에서 전역 객체는 `window` 이고
  - `Node.js` 환경에서는 `global` 이다

- 전역 공간에서의 `this`는 전역 객체를 의미하며며, 자바스크립트의 <span style="color:dodgerblue">**모든 변수는 특정 객체의 프로퍼티로 할당**</span>된다. 그리고 그 <span style="color:dodgerblue">**특정 객체란 실행 컨텍스트의 `LexicalEnvirment(L.E)`**</span> 이다.


```js
let a = 1;
console.log(a) // 1
console.log(window.a) // 1
console.log(this.a) // 1

window.a = 3
console.log(a) // 3
console.log(this.a) // 3
console.log(this.a) // 3

window.b = 5
delete a // false
delete window.a // false
delete window.b // true
```

변수에 `delete` 연산자를 쓰는 것이 이상해보일 수도 있지만, `window.`를 생략한 것과 같다. 전역 변수가 곧 전역 객체의 프로퍼티이므로 문제되지 않는다.

전역 변수를 선언하면 자바스크립트 엔진이 자동으로 전역 객체의 프로퍼티로 할당하면서 **추가적으로 해당 프로퍼티의 configurable 속성**(변경 및 삭제 가능성)을 `false`로 정의한다.

>전역 변수와 전역 객체의 프로퍼티는
**호이스팅** 여부 및 **configurable** 여부에서 차이가 있다

<br />

---


## 🔹 메서드로서 호출할 때 그 메서드 내부에서의 `this`

### ✔️함수 vs. 메서드

어떤 함수를 실행하는 방법은 여러 가지가 있는데, 일반적으로
- 함수로서 호출하는 경우
- 메서드로서 호출하는 경우가 있다

>프로그래밍 언어에서 함수와 메서드는 미리 정의한 동작을 수행하는 **코드 뭉치**로, 이 둘을 구분하는 유일한 차이는 <span style="color:dodgerblue">**독립성**</span>에 있다

- **함수**: 그 자체로 독립적인 기능을 수행
- **메서드**: 자신을 호출한 대상 객체에 관한 동작을 수행

```js
const func = function (x) {
  console.log(this, x)
}

// 함수로서 호출
func(1)          // Window { ... } 1

const obj = {
  method : func
}

// 메서드로서 호출
obj.method(2);   // { method: f } 2
obj['method'](2) // { method: f } 2
```

### ✔️ 메서드 내부에서의 `this` 

`this`에는 호출한 주체에 대한 정보가 담긴다
어떤 함수를 메서드로서 호출하는 경우 호출 주체는 함수명(프로퍼티명) 앞의 객체이다

```js
const obj = {
  methodA : function () { console.log(this) }
  inner : {
    methodB : function () { console.log(this) }
  }
}

obj.methodA();             // { methodA: f, inner: {...} } (=== obj)

obj.inner.methodB();       // { methodB: f } (=== obj.inner)
obj.inner['methodB']();    // { methodB: f } (=== obj.inner)
obj['inner']['methodB'](); // { methodB: f } (=== obj.inner)
```

<br />

---

## 🔹 함수로서 호출할 때 그 함수 내부에서의 `this`

### ✔️ 함수 내부에서의 `this`

  - 어떤 함수를 함수로서 호출할 경우에는 `this`가 지정되지 않는다

  - _`this`에는 호출한 주체의 정보를 담고 있는데, 함수로서 호출하는 것은 호출 주체를 명시하지 않고 개발자가 코드를 직접 실행한 것이기 때문에 호출 주체를 알 수 없다_

  >실행 컨텍스트 활성화할 당시에 `this`가 지정되지 않은 경우 `this`는 전역 객체를 바라본다. 따라서 함수에서의 `this`는 전역 객체를 가리킨다.

### ✔️ 메서드의 내부함수에서의 `this`

```js
const obj1 = {
  outer : function () { 
    	console.log(this);          // (1)
  		const innerFunc = function () {
        	console.log(this);      // (2) (3)
        }
        innerFunc();                // (2) 호출
    
    const obj2 = {
    	innerMethod : innerFunc
    }
    obj2.innerMethod()              // (3) 호출
  }
}
obj1.outer();                       // (1) 호출
```

(1)호출: 호출할 때 <span style="color:dodgerblue">**점(.)이 있다 ➔ 메서드로서 호출**</span> ➔ obj1을 바인딩 함

(2)호출: 호출할 때 <span style="color:red">**점(.)이 없다 ➔ 함수로서 호출**</span> ➔ 전역객체(window)을 바인딩 함

(3)호출: 호출할 때 <span style="color:dodgerblue">**점(.)이 있다 ➔ 메서드로서 호출**</span> ➔ obj2을 바인딩 함


### ✔️ 메서드의 내부함수에서의 `this`를 우회하는 방법(ES6+)

`self` 함수를 사용

```js
const obj1 = {
  outer : function () { 
    	console.log(this);         
  		const innerFunc1 = function () {
        	console.log(this);      
        }
        innerFunc1();          // 전역객체(window) 호출 
    
    const self = this;
    const innerFunc2 = function () {
        	console.log(self);      
        }
        innerFunc2();          // obj1.outer 호출
  }
}                   
```

### ✔️ `this`를 바인딩하지 않는 함수, 화살표 함수(ES6+)

화살표 하수는 실행 컨텍스트를 생성할 때 `this` 바인딩 과정 자체가 빠지게 되어, 상위 스코프의 `this`를 그대로 활용할 수 있다.

<br />

---

## 🔹 콜백 함수 호출 시 그 함수 내부에서의 `this`

>**콜백 함수**란?
함수 A의 **제어권을 다른 함수(또는 메서드) B에게 넘겨주는** 경우 함수 A를 콜백 함수라 한다.

- 함수 A는 함수 B의 내부 로직에 따라 실행
- `this` 역시 함수 B 내부 로직에서 정한 규칙에 따라 값이 결정된다.

<br />

---

## 🔹 생성자 함수 내부에서의 `this`

>**생성자 함수**란?
어떤 공통된 성질을 지니는 객체들을 생성하는데 사용하는 함수.
구체적인 인스턴스를 만들기 위한 틀

- 객체지향 언어에서 생성자를 클래스 `class`,
- 클래스 `class`를 통해 만든 객체를 인스턴스 `instance`
- 예시)
  - 클래스`class` : 붕어빵 틀
  - 인스턴스`instance` : 팥붕어빵, 크림붕어빵

>**생성자**란?
구체적인 인스턴스를 만들기 위한 틀

자바스크립트는 <span style="color:dodgerblue">**함수에 생성자로서의 역할을 함께 부여**</span>했는데,
`new` 키워드와 함께 함수를 호출하면 해당 함수가 생성자로서 동작하게 되고
**어떤 함수가 생성자 함수로서 호출된 경우 내부에서의 `this`는 곧 새로 만들 구체적인 인스턴스`instance` 자신**이 된다

---

# 명시적으로 `this`를 바인딩하는 방법

상황별로 `this`에 어떤 값이 바인딩되는지를 살펴봤다.
이제는 이러한 규칙을 깨고 `this`에 별도의 대상을 바인딩하는 방법을 알아보자.

<br />

---

## 🔸 `call` 메서드
>`call` 메서드는 메서드의 호출 주체인 함수를 즉시 실행하도록 하는 명령

- `call` 메서드의 첫 번째 인자를 `this`로 바인딩하고
- 두 번째 인자로 임의의 객체를 `this`로 지정할 수 있다

```js
const func = function (a, b, c) {
	console.log(this, a, b, c);

}

func(1, 2, 3);                // Window{...} 1 2 3
func.call({x: 1}, 4, 5, 6);   // {x: 1} 4 5 6
```

<br />

---

## 🔸 `apply` 메서드
>`apply` 메서드는 `call` 메서드와 기능적으로 완전히 동일하다.
다만, `call` 메서드와 달리 <span style="color:red">**두 번째 인자를 배열로 받아**</span> 그 배열의 요소들을 호출할 함수의 매개변수로 지정한다는 차이점이 있다.

```js
const func = function (a, b, c) {
	console.log(this, a, b, c);

}

func.apply({x: 1}, [4, 5, 6]);   // {x: 1} 4 5 6
```

>🚩**참고**
`call` / `apply` 메서드는 유사배열객체에 모든 배열 배서드를 적용할 수 있는다. 단, 원본 문자열에 변경을 가하는 메서드(`push`, `pop`, `shift`, `unshift`, `splice`)는 에러 발생.

>🚩**참고**
<span style="color:red">**ES6에서는 유사배열객체 또는 순회 가능한 모든 종류의 데이터 타입을 배열로 전환하는 `Array.from` 메서드를 새로 도입**</span>
```js
const obj = {
	0: 'a',
  1: 'b',
  2: 'c'
  length : 
}
Array.from(obj)  // ['a' , 'b', 'c']
```

<br />

---

## 🔸 `bind` 메서드

>`bind` 메서드는 ES5+에서 추가된 기능으로, `call` 메서드와 비슷하지만, 즉시 호출하지는 않고 넘겨받은 **`this` 및 인수들을 바탕으로 새로운 함수를 반환**하기만 하는 메서드

```js
const func = function (a, b, c) {
	console.log(this, a, b, c);

}
func(1, 2, 3);             // Window{...} 1 2 3

const bindFunc1 = func.bind({x: 1});
bindFunc1(1, 2, 3);         // {x: 1} 1 2 3

const bindFunc2 = func.bind({x: 1}, 4, 5);
bindFunc2(6);         // {x: 1} 4 5 6
bindFunc2(7);         // {x: 1} 4 5 7
```

<br />

---

## 🔸 화살표 함수의 예외사항

`ES6`에서 새롭게 도입된 화살표 함수는 실행 컨텍스트 생성 시 `this`를 바인딩하는 과정이 제외되었다. 즉, 이 함수 내부에는 `this`가 아예 없으며, 접근하고자 하면 스코프체인상 **가장 가까운 `this`에 접근**하게 된다.


<br />

---

## 🔸 별도의 인자로 `this`를 받는 경우(콜백 함수 내에서의 `this`)

요소를 순회하면서 콜백 함수를 반복 호출하는 내용의 일부 메서드는 별도의 인자로 `this`를 받기도 한다

<br />

---

### ✨ tl;dr

🎵 명시적 `this` 바인딩이 없는 한,
- 전역 공간에서의 `this`는 전역객체를 참조
- `(.)이 있는 경우` (= 어떤 함수를 메서드로서 호출한 경우)`this`는 메서드 호출 주체(메서드명 앞의 객체)를 참조
- `(.)이 없는 경우` (= 어떤 함수를 함수로서 호출한 경우) `this`는 전역 객체를 참조. 메서드의 내부함수에서도 동일
- 콜백 함수 내부에서의 `this`는 해당 콜백 함수의 제어권을 넘겨받은 함수가 정의한 바를 참조, 정의하지 않은 경우에는 전역객체를 참조
- `new` 생성자 함수에서의 `this`는 생성될 인스턴스를 참조

<br />

🎵 명시적 `this` 바인딩의 경우
- `call`, `apply` 메서드는 `this`를 명시적으로 지정하면서 함수 또는 메서드를 호출
- `bind` 메서드는 `this` 및 함수에 넘길 인수를 일부 지정해서 새로운 함수를 반환
- 요소를 순회하면서 콜백 함수를 반복 호출하는 내용의 일부 메서드(`set`, `map`, `forEach`) 는 별도의 인자로 `this`를 받기도 한다.

으로 `this`를 예측할 수 있다



