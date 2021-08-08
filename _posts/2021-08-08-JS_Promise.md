---
title: "✨JS:: promise()"
tags:
  - [Javascript]
permalink: /study/JS/promise

navigation: true
toc: true
toc_sticky: true

date: 2021-08-08
last_modified_at: 2021-08-08
---

![](https://media.vlpt.us/images/april_5/post/0aa0ff89-a30b-4001-962e-e61626d72573/promise.png)


`주니어 개발자의 개인 공부 과정을 기록합니다.`

콜백 함수를 대체해서 깔끔한 코드(가독성↑)를 작성할 수 있도록 도와주는,
비동기를 간편하게 처리할 수 있도록 도와주는, 
JavaScript에 내장되어 있는`Object`인 `Promise`에 대해 공부하고 정리해본다.

---
# Promise란?
`Promise` 객체는 비동기 작업이 맞이할 미래의 완료 또는 실패와 그 결과 값을 반환한다.

>**Promise란?**
정해진 장시간의 기능을 수행하고 나서 정상적으로 기능이 작동했다면 성공(fulfilled) 메세지와 결과를, 예상치 못한 문제가 발생했다면 에러(rejected)를 전달 함

```jsx
const promise = new Promise(resolve, reject) => {
	// code
};
```

---

## ✨상태(state)

`Promise`는 상태(state)를 가지는데,
- **대기(pending)**: 이행하거나 거부되지 않은 초기 상태. 지정한 operation을 수행중인 상태.
- **이행(fulfilled)**: 연산이 성공적으로 완료됨. operation을 성공적으로 끝낸 상태.
- **거부(rejected)**: 연산이 실패함.
- **처리(settled)**: 이행 또는 거부된 상태.
- **resolved**: 프로미스가 다른 프로미스의 상태에 맞춰 처리됨, 또는 상태가 "잠김"되었다는 의미

대기 중인 프로미스는 값과 함게 이행할 수도, 어떤 이유(오류)로 거부될 수도 있는데, 이행 또는 거부될 때, 프로미스에 연결한 처리기는 그 프로미스의 `.then` 메서드로 대기열에 오른다.
![](https://images.velog.io/images/april_5/post/2f9051c4-ac49-4b57-8864-5c8eb84a8f58/image.png)

---

## ✨Producer/Consumer

- **producer**: 원하는 기능을 수행해서 해당하는 데이터를 만들어 냄
- **consumer**: 원하는 데이터를 소비하는 것


### :: 🌐 Promise 만들기(Producer)
<span style="color:hotpink">**★주의! 새로운 Promise가 만들어질 때, 우리가 전달한 executor라는 콜백 함수가 자동으로 바로 실행 됨.
  ➔ 유저가 버튼을 클릭했을 때 등의 이벤트 동작 시점이 필요하다면 그에 따른 조치를 해야 함**</span>
![](https://images.velog.io/images/april_5/post/3cb28788-12a3-4d8f-be03-124761171c50/image.png)

```jsx
const promise = new Promise(resolve, reject) => {  // (1)
	// doing some heave work(network, read files)
    console.log('doing something...');
    setTimeout(() => {
      resolve('yrkim');                            // (2)
      reject(new Error('no network!'));            // (3)
    }, 2000);
}
```
(1) Promise를 정의한 순간 executor라는 콜백 함수 생성
(2) 성공했을 때
(3) 실패했을 때. reject는 `Error`라는 object를 생성해서 값을 전달


### :: 🌐 Consumers: Promise 사용하기
<span style="color:hotpink">**★then, catch, finally를 이용하여 값을 받아올 수 있음**</span>
```jsx
promise  // promise가 정상적으로 실행이 된다면
  .then(value => {            // (1)
      console.log(value); // april
	});
  .catch(error => {           // (2)
      console.log(error); // Error: no network!
	}); 
  .finally (() => {           // (3)
      console.log('finally');
	}); 
```

(1) **then**: promise가 정상적으로 수행될 때 값을 받아올꺼야!
  - `promise`가 정상적으로 수행되어서 `resolve`라는 콜백 함수를 통해서 전달한 값이 `value`라는 파라미터로 전달 됨.
  
(2) **catch**: promise에 에러가 발생했을 때!
  - `reject`를 통해 받아온 에러메세지를 출력
  
(3) **finally**: 성공/실패 상관없이 무조건 마지막에 호출!

### :: ⛓ Promise chaining: Promise 연결하기
보통 <span style="color:hotpink">**하나 또는 두 개 이상의 비동기 작업을 순차적으로 실행해야 하는 경우**</span> Promise chaining을 이용해 해결하는데,
<span style="color:dodgerblue">**Promise chaining**</span>이 가능한 이유는 
- `promise.then`을 호출하면 `Promise` 반환되기 때문. 
- 반환된 `Promise`는 당연히 `.then`을 호출할 수 있다. 

이런 개념을 Promise chaining라고 한다.

<br />

```jsx
const getHen = () => {
    new Promise((resolve, reject) => {
      setTimeout(() => {resolve('🐓'), 1000});
    });
});

getHen()
    .then(hen => getEgg(hen))
    .then(egg => cook(egg))
    .then(meal => console.log(meal)); // 🐓 => 🥚 => 🥠
```

콜백 함수를 전달할 때, 받아오는 value를 다음 함수로 전달해서 바로 다음을 호출하는 경우에는 <span style="color:dodgerblue">**받아오는 value가 생략 가능**</span>하다
```jsx
// ↓코드를 깔끔하게 정리할 수 있음
getHen()
    .then(getEgg)
    .catch(error => {  // (1)
        return '🌭'; 
    });
    .then(cook)
    .then(console.log);
    .catch(console.log);
```
(1) `getEgg`를 실행할 때 오류가 발생했을 때 처리하는 로직. 
  - 예시) 🐓을 받아오다가 에러발생하면 🌭를 리턴(전달, 대체)하겠다
  - 에러 핸들링이 미흡할 경우 Promise chaining이 처리되지 않기 때문에 즉, 그 다음 `.then`이 실행되지 않기 때문에 대체할 수 있는 에러 핸들링이 필요하다.
  
---

### ✨ tl;dr
<span style="color:blue">**콜백지옥 해결!!! `Promise()`**</span>

- 자바스크립트 비동기 처리를 위한 그 시작, 프로미스
  - 비동기적인 것을 실행할 때 콜백함수 대신에 사용

- JavaScript에서 제공하는 비동기를 간편하게 처리할 수 있도록 도와주는 Object
- 정의된 장시간의 기능을 수행하고 나서
  - 정상적으로 기능이 수행 되었다면 성공 메세지와 처리결과를 전달해주고
  - 정상적으로 기능이 수행되지 않았다면 에러 메세지를 전달 함

- **Promise에서 중요한 두 가지!**
  1) **State(상태)**: 성공했는지 실패했는지? 
    - 지정한 operation이 수행중일 때는 pending 상태가 되고 성공하게 되면 fulfilled의 상태가 됨
    - file을 찾을 수가 없거나 네트웍에 문제가 생긴다면 rejected 상태가 됨

  2) **producer**와 **Consumer**의 차이를 이해하는 것
    - producer: 우리가 원하는 기능을 수행해서 해당하는 데이터를 만들어내는!
    - Consumer: 우리가 만들어낸 데이터를 소비하는!

