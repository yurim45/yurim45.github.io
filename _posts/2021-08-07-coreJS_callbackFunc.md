---
title: "🐯CoreJS:: 콜백 함수"
tags:
  - [Javascript]
permalink: /study/JS/callbackFunc

navigation: true
toc: true
toc_sticky: true

date: 2021-08-07
last_modified_at: 2021-08-07
---

![]()

`주니어 개발자의 개인 공부 과정을 기록합니다.`

---
# 콜백 함수란?

>**콜백 함수(callback function)**란, 다른 코드의 인자로 넘겨주는 함수

콜백 함수를 넘겨받은 코드는 이 콜백 함수에게 <span style="color:dodgerblue">**제어권**</span>을 넘겨 주며, 콜백 함수는 **필요에 따라 적절한 시점**에 실행한다.

---

## :: ✨제어권

예제)
```jsx
let count = 0;
const cbFunc = () => {
	console.log(count);
  	if (++count > 4) clearInterval(time);
};

const timer = setInterval(cbFunc, 300);
// 실행 결과
// 0 (0.3초)
// 1 (0.6초)
// 2 (0.9초)
// 3 (1.2초)
// 4 (1.5초)
```

예제를 통해 코드 실행 방식과 제어권을 살펴보면,

| code | 호출 주체 | 제어권 |
| :- | :- | :- |
| cbFunc(); | 사용자 | 사용자 |
| setInterval(cbFunc, 300); | setInterval | setInterval |

- setInterval이라고 하는 '다른 코드'에 첫 번째 인자로서 cbFunc 함수를 넘겨주자
- 제어권을 넘겨받은 setInterval이 스스로의 판단에 따라 적절한 시점에(0.3초 마다) 이 함수를 실행했다.
- 콜백 함수의 제어권을 넘겨받은 코드는 <span style="color:dodgerblue">**콜백 함수 호출 시점에 대한 제어권**</span>을 가진다.
- 제어권을 넘겨받은 코드는 콜백 함수를 호출할 때 <span style="color:dodgerblue">**인자에 어떤 값들을 어떤 순서로 넘길 것**</span>인지에 대한 제어권도 가진다.

---

## :: ✔️콜백 함수도 함수다
```jsx
const obj = {
	vals: [1, 2, 3],
  	logValues: (v, i) => {
    	console.log(v, i)
    };
};
obj.logValues(1, 2); // (1)
// {vals:[1, 2, 3], logValues: f} 1 2
[4, 5, 6].forEach(obj.logValues);  // (2)
// Window {...} 4 0			  
// Window {...} 5 1			  
// Window {...} 6 2
```
(1) 이름 앞에 점(.)이 있으니 메서드로서 호출
	&#x2001; ➔ 이 때의 `this`는 `obj`
(2) 함수만 전달 받은 것으로, `obj`와 연관이 없어진다.
	&#x2001; ➔ 이 때의 `this`는 `전역 객체(window)`


### ➔ 콜백 함수 내부의 `this`에 다른 값 바인딩하기
별도의 인자로 `this`를 받는 함수의 경우에는 원하는 값을 넘겨주면 되지만, 그렇지 않은 경우에는 `this`의 제어권도 넘겨주게 되므로 사용자가 임의로 바꿀 수 없다.

**:: 콜백 함수 내부의 `this`에 다른 값을 바인딩 하는 방법**

### (1) ~~변수에 담기~~ 
(전통적인 방식) 잘 사용하지 않는다 ❌
~~콜백 함수로 활용할 함수에서는 `this를 다른 변수`에 담아 **`this` 대신** 그 **변수를 사용**하게 하고, 이를 클로저로 만드는 방식이 많이 쓰였다.~~

<br />

### (2) <span style="color:dodgerblue">**bind 메서드**</span> 활용 `+ES5` 
```jsx
const obj = {
	name: 'yrKim',
  	func: () => console.log(this.name);
};

setTimeout(obj.func.bind(obj), 1000); 

const obj2 = { name: 'april' }
setTimeout(obj.func.bind(obj2), 1500); 
```

---

## :: 🚩 콜백 지옥과 비동기 제어

>**콜백 지옥(callback hell)**은 콜백 함수를 익명 함수로 전달하는 과정이 반복되어 코드의 들여쓰기 수준이 감당하기 힘들 정도로 깊어지는 현상으로 자바스크립트에서는 흔히 발생하는 문제..🥲🥲

➔ **비동기적인 코드**: 즉시 실행이 ❌ 아닌, &#x2000; 별도의 요청, 실행 대기, 보류 등과 관련된 코드

### (1) `+ES6`의 `Promise`를 이용한 방식
```jsx
new Promise((resolve) => {
	setTimeout(() => {
              let name = '에스프레소';
              console.log(name);
              resoleve(name);
    }, 500)
})
  .then((prevName) => {
  	new Promise((resolve) => {
              setTimeout(() => {
                    let name = prevName + ', 아메리카노';
                    console.log(name);
                    resoleve(name);
              }, 500)
	})
  })
  .then((prevName) => {
      new Promise((resolve) => {
                setTimeout(() => {
                      let name = prevName + ', 카페라떼';
                      console.log(name);
                      resoleve(name);
     			}, 500)
      })
   })
```
- `promise`의 인자로 넘겨주는 콜백 함수는 호출할 때 바로 실행되지만
- 그 내부에 `resolve` 또는 `reject` 함수를 호출하는 구문이 있을 경우,
  - 둘 중 하나가 실행되기 전까지는 `.then` 또는 오류 구문 `catch`로 넘어가지 않는다
  - 비동기 작업이 완료될 때 `resolve` 또는 `reject`를 호출하는 방법으로 비동기 작업의 동기적 표현이 가능하다
  
### (2) `Promise` + `Async/await`
```jsx
const addCoffee = (name) => {
	return new Promise((resolve) => {
    	setTimeout((
        	resolve(name);
        ), 500);
    });
};

const coffeeMaker = async () => {
	let coffeeList = '';
    const _addCoffee = async (name) => {
    	coffeeList += (coffeeList ? ',' : '') + 
        await addCoffee(name);
    }
    await _addCoffee('에스프레소');
    console.log(coffeeList);
    await _addCoffee('아메리카노');
    console.log(coffeeList);
    await _addCoffee('카페라떼');
    console.log(coffeeList);
    await _addCoffee('카페모카');
    console.log(coffeeList);
};

coffeeMaker();
```
ES2017에서 등장한 `Async/await`는 가독성이 뛰어나고, 작성법이 간단하다는 장점이 있다.

- 비동기 작업을 수행하고자 하는 함수 앞에 `async` 키워드를 붙혀주고,
- 함수 내부에서 실질적인 비동기 작업이 필요한 위치마다 `await` 키워드를 붙혀주면
- 뒤의 내용을 `Promise`로 자동 전환하고, 해당 내용이 resolve된 이후에 다음으로 진행한다. 

즉, `Promise`의 `.then`과 흡사한 효과를 얻을 수 있다.

![](https://images.velog.io/images/april_5/post/9d49e8fe-88ca-4212-9f9b-3041cab84737/image.png)

---

### ✨ tl;dr
- 콜백 함수는 다른 코드에 인자를 넘겨줌으로써 그 제어권도 함께 위임한 함수이다.
- 제어권을 넘겨받은 코드는 
  1) 콜백 함수를 호출하는 시점을 스스로 판단해서 실행
  2) 콜백 함수를 호출할 때 인자로 넘겨줄 값들 및 그 순서가 정해져 있다. 이 순서를 따르지 않고 코드를 작성하면 엉뚱한 결과를 얻게 되니 주의!
  3) 콜백 함수의 `this`가 무엇을 바라보도록 할지가 정해져 있는 경우도 있는데, 정하지 않은 경우에는 전역객체(window)를 바라본다.
    - 사용자 임의로 `this`를 바꾸고 싶을 경우 `bind` 메서드를 활용하면 된다.
    
- 어떤 함수에 인자로 베서드를 전달하더라도 결국 함수로서 실행된다
- 비동기 제어를 위한 콜백 함수를 사용할 때엔 `Promise` + `Async/await` 을 이용하면 된다



