---
title: "🐯CoreJS:: 프로토타입"
tags:
  - [Javascript]
permalink: /study/JS/prototype

navigation: true
toc: true
toc_sticky: true

date: 2021-08-21
last_modified_at: 2021-08-21
---

![](https://images.velog.io/images/april_5/post/8dc70d82-08d1-4fd8-bbe5-27fe0d8e7f90/%E1%84%91%E1%85%B3%E1%84%85%E1%85%A9%E1%84%90%E1%85%A9%E1%84%90%E1%85%A1%E1%84%8B%E1%85%B5%E1%86%B8.png)


`주니어 개발자의 개인 공부 과정을 기록합니다.`


자바스크립트는 프로토타입 기반 언어이다. 
- 클래스 기반 언어에서는 `상속`을 사용하지만 
- 프로토타입 기반 언어에서는 <U>어떤 객체를 원형(prototype)으로 삼고 이를 복제(참조)함</U>으로써 상속과 비슷한 효과를 얻는다. 

이런 독특한 개념인 프로토타입에 대해 알아보자.

<br />


---

# 프로토타입의 개념 이해

## `Constructor`, `prototype`, `instance`


![](https://images.velog.io/images/april_5/post/beb16828-941f-4489-92a4-b18cdebb2034/image.png)

이 그림을 좀 더 구체적인 형태로 바꾸면,

![](https://images.velog.io/images/april_5/post/59f2f065-efba-4c93-8c04-89adbe9b13a3/image.png)

이런 그림이 된다. 위와 아래의 그림을 보면서 흐름을 따라가 보자.
- 어떤 생성자 함수`Constructor`를 `new` 연산자와 함께 호출하면
- `Constructor`에서 정의된 내용을 바탕으로 새로운 인스턴스`instance`가 생성된다
- 이때 `instance`에는 `__proto__`라는 프로퍼티가 자동으로 부여되는데,
- 이 프로퍼티는 `Constructor`의 `prototype`라는 프로퍼티를 참조한다.


>모든 객체들이 메소드와 속성들을 상속 받기 위한 템플릿으로써 프로토타입 객체(prototype object)를 가진다는 의미


<br />

<span style="color:dodgerblue">**`prototype`와 `__proto__`라는 프로퍼티의 관계가 프로토타입의 핵심**</span>이다.
- `prototype`은 객체이다. 이를 참조하는 `__proto__`(dunder proto: 던더 프로토) 역시 객체이다.
- `prototype` 객체 내부에는 인스턴스가 사용할 메서드를 저장한다.
- 그러면 인스턴스에서도 숨겨진 프로퍼티인 `__proto__` 객체를 통해 이 메서드들에 접근할 수 있게 된다.

<br />

| 참고로,  |
| :- |
| ES5.1 명세에는 __proto__가 아니라 [[prototype]]이라는 명칭으로 정의되어 있다. 명세에는 instance.__proto__와 같은 방식으로 접근하는 것을 허용하지 않고, 오직  <span style="color:dodgerblue">**Object.getPrototypeOf(instance)/Reflelect.getPrototypeOf(instance)**</span>를 통해서만 접근할 수 있도록 정의했다. |
| 실무에서는 가급적 `__proto__`를 사용하지 않기를 권장. 대신 <span style="color:dodgerblue">**Object.getPrototypeOf()/Object.create()**</span> 등을 이용하도록 하자. |

<br /><br />

---


![](https://images.velog.io/images/april_5/post/f3952c8a-38aa-4d07-af1c-bb3509d4a2a0/image.png)

예제를 통해 이해해보자.

```jsx
const Person = (name) => {
  this._name = name;
};

Person.prototype.getName = () => {
  return this._name;
};
```

`Person`의 인스턴스는 `__proto__` 프로퍼티를 통해 `getName`을 호출할 수 있다.

```jsx
const april = new Person('april');

april.__proto__.getName(); // (1) undefined
```

`instance`의 `__proto__`가 `Constructor`의 `prototype` 프로퍼티를 참조하므로 결국 둘은 같은 객체를 바라보기 때문이다.

(1) 다만, 여기서 `undefined`가 반환된 이유는 `this`에 바인딩 된 대상이 잘못됐기 때문인데, 어떤 함수를 **메서드로서** 호출할 때는 메서드명 바로 앞의 객체가 곧 `this`가 된다.  [🐯 Javascript this](https://yurim45.github.io/study/JS/this)

`__proto__` 객체에 `name` 프로퍼티가 있다면?

```jsx
const april = new Person('april');

april.__proto__._name = 'april__proto__';
april.__proto__.getName(); // (1) april__proto__
```

관건은 `this`인데, `this`를 인스턴스로 하는 방법은 `__proto__` 없이 인스턴스에서 곧바로 메서드를 쓰는 것이다.

```jsx
const april = new Person('april');

april.getName(); // (1) april
```

이 표현이 가능한 이유는 <span style="color:dodgerblue">**`__proto__`가 생략 가능한 프로퍼티**</span>이기 때문이다.

>정리하자면, 
`new` 연산자로 `Constructor`를 호출하면 `instance`가 만들어지는데, 
이 `instance`의 생략 가능한 프로퍼티인 `__proto__`는 `Constructor`의 `prototype`을 참조한다.

<br />

이번엔 우리가 자주 사용하는 배열을 통해 이해해보자.

![](https://images.velog.io/images/april_5/post/d709d6ea-942e-4712-b7aa-1e3a5ab82620/image.png)

배열의 여러 메서드들을 사용할 수 있었던 이유에 대해 이해할 수 있을 것이다. 

<br /><br />

---

## 프로토타입 체인

어떤 데이터의 `__proto__` 프로퍼티 내부에 다시 `__proto__` 프로퍼티가 연쇄적으로 이어진 것을 <span style="color:dodgerblue">**프로토타입 체인(prototype chain)**</span>이라 하고, 
이 체인을 따라가며 검색하는 것을 <span style="color:blue">**프로토타입 체이닝(prototype chaining)**</span>이라고 한다.

**프로토타입 체이닝(prototype chaining)**은
어떤 메서드를 호출하면 자바스크립트 엔진은 
- 데이터 자신의 프로퍼티들을 검색해서 원하는 메서드가 있으면 그 메서드를 실행하고, 
- 없으면 `__proto__`를 검색해서 있으면 그 메서드를 실행하고, 
- 없으면 다시 `__proto__`를 검색해서 실행하는 식으로 진행한다.

<br />

| 참고로, 메서드 오버라이드(method overriding)와 동일한 맥락이다. |
| :- |
| 메서드 위에 메서드를 엎어씌웠다는 표현.|
| 자바스크립트 엔진이 메서드를 찾는 방식은 가장 가까운 대상인 자신의 프로퍼티를 검색하고, 없으면 그 다음으로 가까운 대상인 `__proto__`를 검색하는 순서로 진행된다. '**교체**'하는 형태라면 원본에는 접근할 수 없는 형태가 되겠지만 '**얹는**, **덮어 씌운**' 형태라면 원본이 아래에 유지되고 있고 원본에 접근할 수 있다. |

<br />

![](https://images.velog.io/images/april_5/post/ff511f17-c666-49d0-8c66-2a1dd5b7823e/%E1%84%91%E1%85%B3%E1%84%85%E1%85%A9%E1%84%90%E1%85%A9%E1%84%90%E1%85%A1%E1%84%8B%E1%85%B5%E1%86%B8.png)


<br />
<br />

### ☑️ 객체 전용 메서드의 예외사항

- 어떤 생성자 함수이든 `prototype`은 반드시 객체이다.
- `Object.prototype`이 언제나 프로토타입 체인의 최상단에 존재한다.
- 따라서, 객체에서만 사용할 메서드는 다른 여느 데이터 타입처럼 프로토타입 객체 안에 정의할 수가 없다. 
- 따라서, `Object.prototype`에 있는 메서드는 어느 자료형이던 인스턴스에서 바로 호출할 수 있다.
- 따라서, 객체에서만 사용할 메서드는 `prototype` 안에 정의하지 않는다. 객체에서만 사용할 메서드를 `prototype` 내부에 정의하면 다른 데이터타입도 프로토타입 체인을 타고 올라와서 해당 메서드를 사용할 수 있게 되기 때문이다.
- 이런 메서드를 Static method라 한다.

<br />
<br />

### ☑️ 다중 프로토타입 체인

프로토타입 체인을 2단계 이상으로 연결하고 싶다면, 

>`__proto__`가 가리키는 대상, 즉 생성자 함수의 `prototype`이
연결하고자 하는 상위 생성자 함수의 인스턴스를 바라보게끔 해주면 된다.

```jsx
const Grade = () => {
  const ars = Array.prototype.slice.call(arguments);
  for( var i = 0; i < args.length; i++) {
    this[i] = args[i];
  }
  this.length = args.length;
};

const g = new Grade(100, 80);  // (1)
```

(1) 변수 `g`는 `Grade`의 인스턴스를 바라본다.
`Grade`의 인스턴스는 여러 개의 인자를 받아 각각 순서대로 인덱싱해서 저장하고 `length` 프로퍼티가 존재하는 등으로 배열의 형태를 지니지만, 배열의 메서드를 사용할 수 없는 유사배열객체이다.
`g { 0: 100, 1: 80, length: 2 }`

따라서, 배열 메서드를 바로 사용할 수 없다. 
이를 가능하게 하고 싶다면, 인스턴스 g의 `__proto__`, 즉 `Grade.prototype`이 배열의 인스턴스를 바라보게 해주면 된다.

<br /><br />

---

### ✨ tl;dr

- 어떤 생성자 함수를 `new` 연산자와 함께 호출하면
  - `Constructor`에서 정의된 내용을 바탕으로 새로운 인스턴스가 생성되는데, 
  - 이 인스턴스에는 `__proto__`라는, `Constructor`의 `ptototype` 프로퍼티를 참조하는 프로퍼티가 자동으로 부여된다.
  - `__proto__`는 생략 가능한 속성이라서, 
  - 인스턴스는 `Constructor.ptototype`의 메서드를 마치 자신의 메서드인 것처럼 호출할 수 있다.
  
<br />

- `Constructor.ptototype`에는 `constructor`라는 프로퍼티가 있는데, 이는 다시 생성자 함수 자신을 가리킨다. 
  - 이 프로퍼티는 **인스턴스가 자신의 생성자 함수가 무엇인지를 알고자 할 때 필요한 수단**이다.

<br />

- 직각삼각형의 대각선 방향, 즉 `__proto__` 방향을 계속 찾아가면 최종적으로는 `Object.ptototype`에 도달하게 된다. 
  - 이런 식으로 `__proto__` 안에서 다시 `__proto__`를 찾아가는 과정을 <span style="color:dodgerblue">**프로토타입 체이닝**</span>이라고 하며, 
  - 이 프로토타입 체이닝을 통해 각 프로토타입 메서드를 자신의 것처럼 호출할 수 있다. 
  - 이때 접근 방식은 자신으로부터 가장 가까운 대상부터 점차 먼 대상으로 나아가며, 원하는 값을 찾으면 검색을 중단한다.

<br />

- `Object.ptototype`에는 모든 데이터 타입에서 사용할 수 있는 범용적인 메서드만이 존재하며
  - 객체 전용 메서드는 여느 데이터 타입과 달리 `Object` 생성자 함수에 스태틱하게 담겨 있다.
  
<br />

- <span style="color:dodgerblue">**프로토타입 체인**</span>은 반드시 2단계로만 이뤄지는 것이 아니라 무한대로 생성할 수도 있다.



