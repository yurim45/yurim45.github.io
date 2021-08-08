---
title: "🐯CoreJS:: 실행 컨텍스트"
tags:
  - [Javascript]
permalink: /study/JS/execution_context

navigation: true
toc: true
toc_sticky: true

date: 2021-08-07
last_modified_at: 2021-08-07
---

`주니어 개발자의 개인 공부 과정을 기록합니다.`

---

# 실행 컨텍스트

자바스크립트는 어떤 <span style="color:dodgerblue">**실행 컨텍스트가 활성화되는 시점**</span>에
- 선언된 변수를 위로 끌어올리고(호이스팅 hoisting)
- 외부 환경 정보를 구성하고
- `this` 값을 설정하는 등의 동작을 수행

하는데, 이로 인해 다른 언어에서는 발견할 수 없는 특이한 현상들이 발생한다.

---
## 실행 컨텍스트란?
>**execution context**
실행할 코드에 환경 정보들을 모아놓은 **객체**

- 자바스크립트에서 <span style="color:red">**가장 중요한 개념**</span>
- 함수를 실행할 때 실행 컨텍스트가 구성됨
- 함수가 실행될 때 `call stack`에 쌓아올려 코드의 환경과 순서를 보장함

### 💡Stack과 Queue❓
- Stack : FILO(First In Last Out), LIFO(Last In First Out)
- Queue : FIFO(First In First Out), LILO(Last In Last Out)
![](https://images.velog.io/images/april_5/post/7b6280e4-447f-4ad7-8f66-11acaa9d5998/image.png)

---

## 실행 컨텍스트의 구성 
- 전역 공간 → 자동으로 생성
- ~~eval() 함수 → 사용을 권장하지 않음~~
- **함수를 실행** → 가장 흔한 실행 컨텍스트 구성 방법
- ES6 부터는 블록`{ }`에 의해서도 실행 컨텍스트가 생성 

<br />

### :: 실행 컨텍스트와 콜 스택 예제

```js
// ------------------- (1)
var a = 1;
function outer() {
  function inner() {
    console.log(a); // undefined
    var a = 3;
  }
  inner(); // -------- (2)
  console.log(a); // 1
}
outer(); // ---------- (3)
console.log(a); // 1
```
위 코드를 실행하는 순간 
(1)전역 컨텍스트가 콜 스택에 담긴다.
- **전역 컨텍스트**라는 개념은 일반적인 **실행 컨텍스트**와 특별히 다를 것이 없다. 
- 별도의 실행 명령이 없어도 브라우저에서 자동으로 실행된다.

그 이후 코드들을 순차로 진행하다가
(3)에서 `outer`함수를 호출하면 자바스크립트 엔진은 
- `outer`에 대한 환경 정보를 수집
- `outer 실행 컨텍스트`를 생성한 후 콜 스택에 담는다

이 때, 콜 스택 맨 위에 outer실행 컨텍스트가 놓인 상태이므로 전역 컨텍스트와 관련된 코드의 실행을 일시 중단하고 outer 실행 컨텍스트와 관련된 코드(즉, outer함수 내부 코드)들을 순차로 실행한다.

다시 (2)에서 `inner`함수의 실행 컨텍스트가 콜 스택 가장 상위에 담기면 outer 컨텍스트와 관련된 코드의 실행을 중단하고 inner 함수 내부의 코드들을 순서대로 진행한다.

![](https://images.velog.io/images/april_5/post/cf167098-2f0d-4883-ab98-b903e7d7d0f9/image.png)

이렇게 어떤 실행 컨텍스트가 활성화될 때 자바스크립트 엔진은 해당 컨텍스트에 **관련된 코드들을 실행하는 데 필요한 환경 정보들을 수집**해서 <span style="color:dodgerblue">**실행 컨텍스트 객체**</span>에 저장한다.
이 객체는 자바스크립트 엔진이 활용할 목적을 생성될 뿐, 개발자가 코드를 통해 확인은 할 수 없다.

---

## 활성화 된 실행 컨텍스트 객체의 수집 정보
### 1. VariableEnvironment
>최초 실행 시의 스냅샷을 유지. VariableEnvironment의 정보를 복사해서 LexicalEnvironment를 생성, 그 이후엔 LexicalEnvironment를 주로 활용하게 된다.

- 현재 컨텍스트 내의 **식별자들에 대한 정보** + **외부 환경 정보**
- 선언 시점의 LexicalEnvironment의 snapshot으로, <span style="color:dodgerblue">**변경 사항은 반영되지 않는다**</span>.

>VariableEnvironment와 LexicalEnvironment의 내부는 **environmentRecord**와 **outerEnvironmentReference**로 구성돼 있다.

### 2. LexicalEnvironment
: 처음에는 VariableEnvironment와 같지만 <span style="color:dodgerblue">**변경 사항이 실시간으로 반영**</span>된다.


#### 🚩 environmentRecord와 <span style="color:dodgerblue">**호이스팅**</span> ✨
  - environmentRecord에는 현태 컨텍스트와 관련된 코드의 매개변수 이름, 함수 선언, 변수명 등 **식별자 정보들이 저장**(선언된 변수의 식별자 등)
>컨텍스트 내부 전체를 처음부터 끝까지 **순서대로** 수집한다.
변수 정보를 수집하는 과정을 모두 마쳤더라도 아직 실행 컨텍스트가 관여할 코드들은 실행 전 상태인데, 
코드가 실행되지 전임에도 불구하고 자바스크립트 엔진은 이미 해당 환경에 속한 코드의 변수명들을 모두 알고 있게 된다. 여기서 **호이스팅**이라는 개념이 등장한다.

#### 🚩 스코프, 스코프 체인, outerEnvironmentReference
- 스코프scope?
>식별자에 대한 유효범위

  - ES5까지는 전역 공간을 제외하면 **오직 함수에 의해서만** 스코프가 생성
  - <span style="color:dodgerblue">**ES6에서는 블록에 의해서도 스코프 경계가 발생하게 함**</span>으로써 다른 언어와 비슷해졌다. 
  - 다만, `var` 변수에 대해서는 작용하지 않고 새로 생긴 `let`, `const`, `class`, `strict mode에서의 함수 선언` 등에 대해서만 작용한다.
    - ES6에서는 둘을 구분하기 위해 함수 스코프, 블록 스코프라는 용어를 사용한다.

- 스코프 체인?
>여러 스코프에서 동일한 식별자를 선언한 경우에는 **무조건 스코프 체인 상에서 가장 먼저 발견된 식별자에만 접근 가능**하게 하는 것

### 3. ThisBinding
  - `this` 식별자가 바라봐야 할 대상 객체

---

## 전역변수와 지역변수
- 전역변수 : 전역 공간에서 선언한 변수. 전역 컨텍스트의 `LexicalEnvironment`에 담긴 변수
- 지역변수 : 함수 내부에서 선언한 변수

>안전한 코드 구성을 위해 가급적 전역번수의 사용은 최소화하는 것이 좋다

---

## this
- 실행 컨텍스트의 thisBinding에는 this로 지정 된 객체가 저장됨
- 실행 컨텍스트 활성화 당시에 this가 지정되지 않은 경우, this에는 전역 객체가 저장 됨
- 그 밖에는 함수를 호출하는 방법에 따라 this에 저장되는 대상이 다름

---

![](https://images.velog.io/images/april_5/post/1f2612fe-98c3-48e0-9e51-606c2dfa834a/%E1%84%89%E1%85%B5%E1%86%AF%E1%84%92%E1%85%A2%E1%86%BC%20%E1%84%8F%E1%85%A5%E1%86%AB%E1%84%90%E1%85%A6%E1%86%A8%E1%84%89%E1%85%B3%E1%84%90%E1%85%B3.jpeg)


