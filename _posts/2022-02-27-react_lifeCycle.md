---
title: "🚀React:: React Lifecycle & 조건부 렌더링"
tags:
  - [React]
permalink: /study/react/life_cycle

navigation: true
toc: true
toc_sticky: true

date: 2022-02-27
last_modified_at: 2022-02-27
---

![](https://images.velog.io/images/april_5/post/707c8c3b-7893-4776-890a-bd897bb78728/React.png)

부모 컴포넌트와 자식 컴포넌트의 <span style="color:blue">Lifecycle</span>에 대해 알아보고 <span style="color:red">관련된 에러를 해결</span>하는 방법 알기!!
`시기 적절했던 세션👍 바로 적용했던 조건부 렌더링!!`

---

# Lifecycle이란?

> React 컴포넌트 안의 state와 생명주기

![](https://images.velog.io/images/april_5/post/a74e85b6-7ef7-415f-928b-f8357d6f8563/image.png)

<br />

---

## ○ Lifecycle 기본 순서

1. constructor
2. render
3. componentDidMount
4. (fetch 완료)
5. render
6. (setState)
7. componentDidUpdate (setState 되었기 때문에 컴포넌트 업데이트 발생)
8. componentWillUnmount
   ![](https://images.velog.io/images/april_5/post/af4002d6-40ea-4d10-8722-62e31c47d41b/image.png)

<br />

---

## ○ 부모 - 자식 Lifecycle

- 부모 API에서 받은 데이터를 자식에게 props로 전달하여 자식 내부에서 데이터에 접근하여 사용하는 경우
  ![](https://images.velog.io/images/april_5/post/f4de1ee8-53ae-4963-ace4-09d952c931cf/image.png)

<br />

---

# AND연산자(&&) 사용한 조건부 렌더링!

![](https://images.velog.io/images/april_5/post/6365ede1-9a26-419a-8cc6-d8eb992c8c78/image.png)
<span style="color:red">Cannot read property 'map' of undefined</span> 🤬🤬🤬🤬🤬

Mockup 데이터를 구성하여 import하거나 프로젝트가 시작되고 백엔드 API를 붙이기 시작하면서 발생하는 에러 중 하나. 데이터가 없는데 map을 돌렸으니 에러가 발생할 수 밖에.... 😭
상태값의 시점에 관한 문제라면 React의 Lifecycle과 연관이 있고, 이 때 조건부 렌더링 처리를 해 주어 에러를 해결한다.

아래는 1차 프로젝트에서 실제 적용한 <span style="color:blue">조건부 렌더링</span> 코드!

![](https://images.velog.io/images/april_5/post/c5b59358-f30a-4f7a-b47d-ee024375b3f2/image.png)
`1차 프로젝트를 진행하면서 종종 발생했던 에러 중 하나..😂`

<br />

---

## ○ AND연산자(&&) 사용 시 주의할 점!

- 변수가 숫자 타입인 경우 `0`은 `false` 이다.
- 변수가 문자열 타입인 경우 빈 문자열`“”`도 `false`이다.

<br />

---

참고 자료

- [React | Lifecycle](https://velog.io/@joonsikyang/React-Project-Lifecycle)
- [공식문서 | State and Lifecycle](https://ko.reactjs.org/docs/state-and-lifecycle.html)
