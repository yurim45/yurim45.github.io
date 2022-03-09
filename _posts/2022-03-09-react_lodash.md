---
title: "🚀React:: React Lodash throttle(..and debounce)"
tags:
  - [React]
permalink: /study/react/lodash

navigation: true
toc: true
toc_sticky: true

date: 2022-03-09
last_modified_at: 2022-03-09
---

![](https://images.velog.io/images/april_5/post/707c8c3b-7893-4776-890a-bd897bb78728/React.png)

2차 프로젝트 중 GoToTop Btn 기능을 구현했는데, 멘토님의 리뷰를 보고 성능 개선을 위해 공부한 내용을 정리해본다.

# Lodash

> A modern JavaScript utility library delivering modularity, performance & extras.
> 모듈화, 성능 및 기타 기능을 제공하는 자바스크립트 유틸리티 라이브러리
> [lodash\_공식문서](https://lodash.com/)

<br />

---

## ○ throttle vs debounce

debounce와 throttle은 이벤트를 반복적으로 실행할 때, 콜백 함수의 **불필요한 실행을 줄여주는 역할**을 한다.
불필요한 서버 리퀘스트를 막을 수도 있고, <span style="color:dodgerblue">불필요한 통신을 줄임과 동시에 **필요 없는 렌더링 또한 막을 수 있어** 컴포넌트의 **성능 개선**에도 도움</span>을 준다.

<br />

### ● throttle

- throttle은 콜백 함수(func)를 일정 주기(wait) 내에 한 번만 호출한다.
- 보통 스크롤, 드래그, mousemove 이벤트 등에 사용

<br />

### ● debounce

- debounce는 **이벤트가 끝난 뒤**에 설정해둔 시간(wait)이 지나야 콜백(func)이 실행 된다
- input onChange에서 사용(입력 이벤트가 끝난 뒤 실행)

<br />

---

## throttle의 확실한 전/후 비교👍

이정도로 개념 정리를 끝내고 실제 프로젝트에 적용해보았다.
**중요!** 같은 함수를 바라보게 적용해야 언마운트가 됨!
![](https://images.velog.io/images/april_5/post/e1fea74f-ae0b-4beb-b096-3859468d9fbd/image.png)

- 적용전
  ![](https://images.velog.io/images/april_5/post/243b7c9a-da7b-4398-bd34-a07b420f64ca/throttle%20%E1%84%8C%E1%85%A5%E1%86%AB.gif)

- 적용후
  ![](https://images.velog.io/images/april_5/post/b9e7f163-a098-4736-b53e-610786143d11/throttle%20%E1%84%92%E1%85%AE.gif)

<br />

---

## 정리!

debounce는 이벤트가 끝날 때까지 기다렸다가 시작된다는 점, throttle은 이벤트가 시작되면 일정 주기로 계속 실행한다는 점이 다르다.

위코드 초반에는 기능이 구현되기만 하면 `이게 되네?`라며 마냥 좋았었는데,
2차 프로젝트를 진행중인 요즘은, 기능 구현 `당연한거지!` 뿐만 아니라 <span style="color:dodgerblue">**성능**</span>적인 부분에도 관심이 많아졌다.

좋은? 개발자가 되기 위한 나름의 방향이 하나씩 몸에 새겨지고 있는 듯한.. 기분적인 기분쓰...

<br />
<br />
