---
title: "🐯CoreJS:: 클래스"
tags:
  - [Javascript]
permalink: /study/JS/class

navigation: true
toc: true
toc_sticky: true

date: 2021-08-28
last_modified_at: 2021-08-28
---

![](https://images.velog.io/images/april_5/post/af11642e-189e-4ab2-b32b-bed2ba42ca64/%E1%84%8F%E1%85%A9%E1%84%8B%E1%85%A5%E1%84%8C%E1%85%A1%E1%84%87%E1%85%A1%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%B8%E1%84%90%E1%85%B3%20%E1%84%8F%E1%85%B3%E1%86%AF%E1%84%85%E1%85%A2%E1%84%89%E1%85%B3.png)

`주니어 개발자의 개인 공부 과정을 기록합니다.`

자바스크립트는 프로토타입 기반언어라서 '상속' 개념이 존재하지 않지만, ES6에서 클래스 문법이 추가되었다.

다만, ES6의 클래스에서도 일정 부분 프로토타입을 활용하고 있다는 점 참고하자.

### :: 클래스와 인스턴스

<span style="color:dodgerblue">**클래스**</span>란, 어던 사물의 공통 속성을 모아 정의한 추상적인 개념.

<span style="color:dodgerblue">**인스턴스**</span>는 클래스의 속성을 지니는 구체적인 사례.

상위 클래스(superclass)의 조건을 충족하면서 더욱 구체적인 조건이 추가된 것을 하위 클래스(subclass)라고 한다

---

# 자바스크립트의 클래스

자바스크립트는 프로토타입 기반 언어이므로 클래스의 개념이 존재하지 않는다. 그렇지만 프로토타입을 일반적인 의미에서의 클래스 관점에서 접근해보면 비슷하게 해석할 수도 있다.

예를 들어, 생성자 함수 Array를 `new` 연산자와 함께 호출하면 인스턴스가 생성된다. 이때 Array를 일종의 클래스라고 하면, Array의 prototype 객체 내부 요소들이 인스턴스에 상속된다고 볼 수 있다.
<u>엄밀히는 상속이 아닌 프로토타입 체이닝에 의한 참조</u>지만, 결과적으로는 동일하게 동작하므로 상속이라고 이해해도 무방하다.

한편 Array 내부 프로퍼티들 중 prototype 프로퍼티를 제외한 나머지는 인스턴스에 상속되지 않는다.

![](https://images.velog.io/images/april_5/post/da44b5f7-bfed-4647-a914-b3162d68b006/image.png)

인스턴스에 상속되는지 (인스턴스가 참조하는지) 여부에 따라 `static member`와 `instance member`로 나뉜다. 이 분류는 다른 언어의 클래스 구성요소에 대한 정의를 차용한 것으로서 클래스 입장에서 사용 대상에 따라 구분한 것이다.

> 참고로, 인스턴스에서 직접 접근할 수 없는 메서드가 `static member`이다.
> `static member`는 생성자 함수를 this로 해야만 호출할 수 있다.

그런데 자바스크립트에서는 인스턴스에서도 직접 메서드를 정의할 수 있기 때문에 `인스턴스 메서드`라는 명칭은 혼란스러움을 야기할 수 있다. (프로토타입에 정의한 메서드를 지칭하는 건지, 인스턴스에 정의한 메서드를 지칭하는 건지 등) 따라서 위 명칭 대신에 `프로토타입 메서드`라고 부르는 편이 더 좋을 수 있다.

---

# 클래스 상속

클래스 상속은 객체지향에서 가장 중요한 요소 중 하나이다.

```jsx
// Grade 생성자 함수 및 인스턴스
const Grade = () => {
  const args = Array.prototype.slice.call(arguments);
  for (let i = 0; i < args.length; i++) {
    this[i] = args[i];
  }
  this.length = args.length;
};

Grade.prototype = [];
const g = new Grade(100, 80);
```

자바스크립트에서 클래스 상속을 구현했다는 것은 **결국 프로토타입 체이닝을 잘 연결한 것**과 같다.
다만, 아무리 체이닝을 잘 연결했다고 하더라도 세부적으로 완벽하게 `superclass`와 `subclass`의 구현이 이뤄진 것은 아니다.

예를 들면, `length` 프로퍼티가 `configurable`(삭제 가능)하다는 점과, `Grade.prototype`에 빈 배열을 참조시켰다는 점이 큰 문제이다.

```jsx
...

g.push(90);
console.log(g);
/* Array {
  '0': 100,
  '1': 80,
  '2': 90,
  length: 3,
  __proto__: { length: 3 }
} */

delete g.length;
g.push(70);
console.log(g);
/* Array {
  '0': 70,
  '1': 80,
  '2': 90,
  length: 1,
  __proto__: { length: 1 }
} */
```

`length` 프로퍼티를 삭제하고 다시 `push`를 하니, `push`한 값이 0번째 인덱스에 들어가고 `length`는 1이 되었다.

내장객체인 배열 인스턴스의 `length` 프로퍼티는 `configurable` 속성이 `false`라서 삭제가 불가능한 반면,
Grade 클래스의 인스턴스는 배열 메서드를 상속하지만 기본적으로 일반 객체의 성질을 그대로 지니므로 삭제가 가능해서 문제가 된다.

따라서 `length` 값을 삭제한 후에 `g.__proto__` 즉 `Grade.prototype`이 빈 배열을 가리키고 있기 때문에 자바스크립트가 push 명령에 의해 `g.length`를 읽고자 했을 때 `g.length`가 없었고, 자바스크립트는 프로토타입 체이닝을 타고
`g.__proto__.length`를 읽어왔다.

이처럼 ES5까지의 클래스 상속 구현은 문제가 발생할 여지가 있었고, 이에 ES6에서는 본격적으로 클래스 문법이 도입되었다.

---

💡참고!
클래스의 추상성을 지키는 게 중요한 이유는 상위클래스의 데이터가 오염되면, 상위클래스의 공통성질을 참조하고 있는 다른 수많은 하위클래스까지 데이터 오염이 일어나기 때문이다.

> 추상성:

- 본질적, 보편적, 관념적 성질. 즉, 공통성질.

> 추상화:

- 개별의 사물이나 표상의 공통된 속성이나 관계 따위를 뽑아내는 것.
- 복잡한 자료, 모듈, 시스템 등으로부터 핵심적인 개념 또는 기능을 간추려 내는 것.
- 공통부분을 상위 클래스/인터페이스로 모으는 일.
- 모듈의 기능을 쉽게 이용할 수 있도록 단순화하는 일.

---

<br /><br />

# ES6의 클래스 및 클래스 상속

```jsx
var ES5 = function(name) {
  console.log(name)        // 'es5'
  this.name = name;
};

ES5.staticMethod = function () {
  console.log(this.name)  // 'ES5'
  return this.name + ' staticMethod';
};

ES5.prototype.method = function () {
  return this.name + ' method';
};

var es5Instance = new ES5('es5');
console.log(ES5.staticMethod());    // 'ES5 staticMethod'
console.log(es5Instance.method());  // 'es5 method'

-------------------------------------------

const ES6 = class {
  constuctor (name) {
    this.name = name;
  }

  static staticMethod () {
    console.log(this.name);  // 'ES6'
    return this.name + ' staticMethod';
  }

  method () {
    console.log(this.name);  // undefined
    return this.name + ' method';
  }
};

const es6Instance = new ES6('es6');
console.log(ES6.staticMethod());  // 'ES6 staticMethod'
console.log(es6Instance.method());  // 'undefined method'
```

ES6의 `constructor`는 ES5에서의 생성자 함수와 동일한 역할을 수행한다.

`static` 키워드는 해당 메서드가 `static` 메서드임을 알리는 내용으로, 생성자 함수(클래스) 자신만이 호출할 수 있다.

`method`는 자동으로 `prototype` 객체 내부에 할당되는 메서드이다. 인스턴스가 프로토타입 체이닝을 통해 마치 자신의 것처럼 호출할 수 있는 메서드이다.

<br /><br />

---

### ✨ tl;dr

- 클래스와 인스턴스
  - 어떤 사물의 공통 특성을 모아 정의한 추상적인 개념
  - 인스턴스는 클래스의 속성을 지니는 구체적인 사례
  - 상위 클래스(superclass)의 조건을 충족하면서 더욱 - 구체적인 조건이 추가된 것을 하위 클래스(subclass)라고 함
- 메서드

  - 클래스의 `prototype` 내부에 정의된 메서드는 프로토타입 메서드라고 함
  - 프로토타입 메서드는 인스턴스가 마치 자신의 것처럼 호출할 수 있음
  - 클래스(생성자 함수)에 직접 정의한 메서드는 스태틱 메서드라고 함
  - 스태틱 메서드는 인스턴스가 직접 호출할 수없고 클래스(생성자 함수)에 의해서만 호출할 수 있음

- 클래스 상속을 흉내 내기 위한 세가지 방법

  - `SubClass.prototype`에 `SuperClass`의 인스턴스를 할당한 다음 프로퍼티를 모두 삭제하는 방법
  - 빈 함수(Bridge)를 활용하는 방법
  - `Object.create`를 이용하는 방법

- ES6
  - 클래스 문법이 도입됨
  - 이전까지는 상속 및 추상화를 구현하기 위해 상당히 복잡한 방법을 사용했는데 ES6에서는 상당히 간단하게 처리됨
