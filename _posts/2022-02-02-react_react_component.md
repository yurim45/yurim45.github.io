---
title: "🚀React:: React Intro | component와 JSX,"
tags:
  - [React]
permalink: /study/react/react_component

navigation: true
toc: true
toc_sticky: true

date: 2022-02-02
last_modified_at: 2022-02-02
---

![](https://images.velog.io/images/april_5/post/707c8c3b-7893-4776-890a-bd897bb78728/React.png)

# React란?

> Component 단위의 Javascript Library

- `가상 돔(Virtual Dom)` 을 통해 UI를 빠르게 업데이트한다
- `가상 돔(Virtual Dom)` 은 이전 UI 상태를 메모리에 유지해서, **변경될 UI의 최소 집합을 계산하는 기술**이다. 이 기술로 불필요한 UI 업데이트는 줄고, 성능은 좋아진다
- 웹 페이지의 **규모가 커지고 복잡하고 다양한 UI, UX의 웹 어플리케이션**을 개발하며 **생산성을 향상**시키고
- **많은 양의 데이터 관리**와
- **코드의 유지 보수**를 더욱 편리하게 하기 위해 Frontend Framework(Library)가 등장

<br />

---

### ✨참고✨ Frontend Framework(Library)

#### :: Angular

- 2010년 Google에서 개발한, TypeScript 기반의
- 매우 안정적이고 탄탄한 Frontend App 개발이 가능하며
- Framework답게 다양한 기능이 내장되어 있다
- 무겁고 배우기 어렵다

#### :: Vue

- 2014년 Evan You라는 개인이 개발한 Framework
- 코드가 깔끔하고 배우기 쉽다

#### :: React

- 2013년 Facebook에서 개발한 Library
- MVC(Model-View-Controller) Architecture (ex. Angular, Vue)와는 다르게 **리액트는 오로지 View만 담당**
- 그만큼 내장되어 있는 기능이 부족해 **third-party 라이브러리(ex. React-router, Redux)를 함께 사용**
- React Native의 사용

<br />

---

## ● CRA

> 리액트 프로젝트를 시작하는데 필요한 개발 환경을 세팅 해주는 도구(toolchain)

- React는 UI 기능만 제공하기 때문에 개발자가 직접 구축해야하는 것들이 많은데,
- 전반적인 시스템을 직접 구축할 수 있어 원하는 환경에 맞게 최적화할 수 있지만
- 반대로, 신경써야 할 것들이 많기 때문에 처음 시작하는 단계에서는 직접 개발 환경 구축이 어려울 수 있다
- 이러한 문제를 해결하기 위해 `CRA(Create-React-App)`가 나타났다

<br />

---

## ● Component의 개념과 종류

> `Component`란? 재활용 가능한 UI 구성 단위

<br />

### ○ 특징

- **재활용**하여 사용할 수 있다.
- **코드 유지보수**에 좋다.
- 해당 페이지가 **어떻게 구성되어 있는지 한 눈에 파악**하기 좋다.
- 컴포넌트는 또 다른 컴포넌트를 포함할 수 있다. (부모 컴포넌트 - 자식 컴포넌트)
- 🚩**집중!** 컴포넌트의 이름은 항상 대문자로 시작!

  - React는 소문자로 시작하는 컴포넌트를 DOM 태그로 처리한다.
  - 예를 들어 `<div />`는 `HTML div 태그`를 나타내지만, `<Welcome />`은 `컴포넌트를 나타내며` 범위 안에 Welcome이 있어야 한다.

  💬 `addComment` component명을 소문자로 작성했다가 읽어오지 못했던 경험을 잊지말자.😭😭😭😭😭😭😭

<br />

### ○ 종류

- Class형 컴포넌트(Class Component)
  - `render()` 함수가 꼭 있어야 한다
- 함수형 컴포넌트(Functional Component)

<br />

---

## ● JSX

> 리액트에서 사용하는 자바스크립트 확장 문법

- JavaScript Syntax Extension
- JSX로 작성한 코드는 브라우저에서 동작하는 과정에서 바벨을 사용하여 일반 자바스크립트 형태의 코드로 변환된다

<br />

### ○ 특징

- 자바스크립트 표현 : `{ ... javascript... }`
- `class` vs. `className`
- Inline Styling : `<div style={{color : "red"}}>Hello React</div>`
- Self Closing tag : `<div></div>` vs. `<div />`
- 모든 요소를 감싸는 최상위 요소 (cf. React Fragments : `<> ... </>`)

  : JSX의 큰 특징 중 하나는 내부 요소들을 감싸는 최상위 요소가 있어야 한다. Fragments는 DOM에 별도의 노드를 추가하지 않고 하나의 컴포넌트 안에 여러 요소(자식)들을 간단하게 그룹화 할 수 있는 기능이다. 요소들을 감싸는 `div` 태그의 불필요한 생성을 막을 수 있어 유용하게 사용된다.

<br />

---

### ✅ 목표!

- 오늘날 React가 많이 사용되고 있는 이유를 알고
- React가 무엇인지 개념을 익히고
- CRA가 무엇인지 이해하고
- Component의 개념과 종류에 대해 설명할 수 있다
- JSX가 무엇인지, 특성은 무엇인지 설명할 수 있다
