---
title: "✨JS:: 비동기의 꽃🌹 async/await"
tags:
  - [Javascript]
permalink: /study/JS/async_await

navigation: true
toc: true
toc_sticky: true

date: 2021-08-08
last_modified_at: 2021-08-08
---

![](https://images.velog.io/images/april_5/post/6003b913-6932-4ee8-ab54-d9e1e98972ec/async%20await.png)

`주니어 개발자의 개인 공부 과정을 기록합니다.`

>callback ➔ async.js ➔ Promise(ECMAScript 2015/ES6) ➔ Generator(ECMAScript 2015/ES6) ➔ async/await(ECMAScript 2017/ES8)

### :: `syntactic sugar`
async와 await은 새로운 것이 추가된 게 아니라 기존에 존재하는 promise위에 조금 더 간편한 API를 제공하는데, 

이렇게 기존에 존재하는 것 위에 또는 기존에 존재하는 것을 감싸서 조금 더 간편하게 쓸수있는 API를 제공하는 것을 <span style="color:hotpink">**syntactic sugar**</span>라 한다

---
# async/await
- 비동기 함수를 `async` 함수로 만들기 위하여 function()앞에 `async` 키워드를 추가
- `async function()`은 `await` 키워드가 비동기 코드를 호출할 수 있게 해주는 함수

![](https://images.velog.io/images/april_5/post/ee8a8ffe-78de-4b79-aafd-3ef98fb85d61/image.png)

---
## :: async🌹

`async` 사용하기 전의 `Promise`로 작성된 코드
```jsx
function fetchUser() { 
      return new Promise((resolve, reject) => { {}안에 있는 코드들이 비동기적으로 실행
          // do network reqeust in 10 secs....  
          resolve 'april';
      })                      
}

const user = fetchUser();
user.then(console.log); // then이라는 콜백함수 호출. console.log 출력값은 april
console.log (user);
```

↓ `promise`를 쓰지않고 `async`를 사용하여 변형하면 

```jsx
async function fetchUser() { 
	// do network reqeust in 10 secs....  
	return 'april';
}

const user = fetchUser();
user.then(console.log); // Promise를 return
console.log (user); // console.log 출력값은 april
```

---

## :: await🌷 

>`async`가 붙은 function안에서만 사용할 수 있음

```jsx
function delay(ms) {
    return new Promise(resolve => setTimeout(resolve, ms));
}

async function getApple() { // getApple라는 promise 함수
    await delay(3000); // delay가 실행되는 3초 동안 기다렸다가
    return '🍎'; // 🍎를 리턴
}

async function getBanana() {
    await delay(2000);
    return '🍌';
}

// promise도 너무 중첩하여 사용하게 되면 콜백 지옥..
// function pickFruits() {
//	return getApple()
//     	       .then(apple => {
//                  return getBanana()
//                         .then(banana => '${apple} + ${banana}')
//             })
// }

async function pickFruits() {
    const apple = await getApple();    // (1)
    const banana = await getBanana();  // (2)
    return '${apple} + ${banana}'; 
}

pickFruits().then(console.log); // 5초 후 🍎 + 🍌
```

### ✨ `await` 병렬 처리 `.all | .race` API

(2)는 (1)이 처리되는 동안 기다릴 필요없이 실행되도 무방한 코드이다.

굳이 (1)이 실행되는 3초 동안 기다릴 것 없이, (1)이 실행될 때 (2)도 실행되면 되는데, 이런 점을 개선시키기 위해 **병렬 처리**를 하게 된다


```jsx
async function pickFruits() {
	const applePromise = getApple();  // 선언되자 마자 실행
	const bananaPromise = getApple(); // 선언되자 마자 실행
	const apple = await applePromise;
	const banana = await bananaPromise;
	return '${apple} + ${banana}'; 
}

pickFruits().then(console.log); // 1초 후 🍎 + 🍌
```
<br />
<br />

그러나 ↑ 위의 코드는 너무 지저분..ㄷㄷ 🥲🥲🥲🥲🥲

**↓ Promise `.all` API를 이용하면!!**
```jsx
function pickAllFruits() {
	return Promise.all([getApple(), getBanana()]) // (1)
	.then(fruies => fruies.join(' + '));          // (2)
}

pickAllFruits().then(console.log); // 🍎 + 🍌
```
(1) `.all`이라는 API는 Promise라는 배열을 전달하게 되면, 모든 Promise들이 병렬적으로 모아주는 API

(2) 병렬적으로 다 모은 `fruies=[🍎, 🍌]` 후(then), `join` API를 이용하여 string(문자열)로 변환

**↓ 다른 Promise API `.race`**

```jsx
function pickOnlyOne() {
	return Promise.race([getApple(), getBanana()]) // (1)
}

pickOnlyOne().then(console.log); // 🍌
```
(1) `.race`는 전달된 배열 중 가장 먼저 실행되는 처음 값을 가져옴.

`getBanana`가 `getApple`보다 먼저 값을 리턴하므로 `getBanana`만 전달 함

