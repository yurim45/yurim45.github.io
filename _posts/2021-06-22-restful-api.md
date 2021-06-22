---
title: "💡RESTful API"
tags:
  - [Blog, jekyll, Github, Git, RESTful API]
permalink: /cs/

navigation: true
toc: true
toc_sticky: true

date: 2021-06-22
last_modified_at: 2021-06-22
---

`주니어 개발자의 개인 공부 과정을 기록합니다.`

# RESTful API

`RESTful API`?? `RESTful URL`?? 많이 들어는 봤는데,, 정확하게 모르겠다.🥲 <br />
현재 사용되고 있는 API 설계 규칙 가운데 가장 널리 사용되고 있는 규칙이라고 하니 이번 기회에 정리해보자!

### REST?

> REST(REpresentational State Transfer)란 웹에 존재하는 모든 자원(resorce, ex. 이미지, 동영상, 데이터)에 고유한 URI를 부여하여 자원에 대한 주소를 지정하는 방법론, 또는 규칙 <br /> > `RESTful API`는 `REST` 특징을 지키면서 API를 제공한다는 의미이다.

<br /><br />

## RESTful API란?

- `REST` 특징을 지키면서 정보를 주고받는 데에 개발자들 사이에 널리 쓰이는 일종의 형식.
  - REST: 웹에 존재하는 모든 자원에 고유한 `uri`을 부여하는 방법
    - URI: 자원을 구조와 함께 나타내는 형식의 구분자
  - API: 어떤 소프트웨어가 다른 소프트웨어로 부터 지정된 형식으로 요청, 명령을 받을 수 있는 수단 ex. Web API, windows API 등

<br />

조금 더 풀어보면, <span style='color:blue'> “프론트엔드에서 백엔드 API를 호출할 때 url을 어떻게 만들 것인가?”</span> 정도로 설명할 수 있다.

<br /><br />

## `REST API`의 특징

- 각 요청이 어떤 동작이나 정보를 위한 것인가를 그 요청의 모습 자체로 추론 가능하다
- 서버로 REST API 요청을 보낼 때는 HTTP 규약에 따라 신호를 전송하는데, REST API는 `GET`, `POST`, `DELETE`, `PUT`, `PATCH` 메소드를 사용한다
  - `POST` <span style=“color:blue”>**C**</span>reate
  - `GET` <span style=“color:blue”>**R**</span>ead
  - `PUT` <span style=“color:blue”>**U**</span>pdate 정보를 통째로 변경할 때
  - `PATCH` <span style=“color:blue”>**U**</span>pdate 일부 정보만 변경할 때
  - `DELETE` <span style=“color:blue”>**D**</span>elete

<br /><br />

## `REST API`의 장점

- 원하는 타입으로 데이터를 주고 받을 수 있다.
- Open API 를 제공하기 쉽다
- 기존 웹 인프라(HTTP)를 그대로 사용할 수 있다.

<br /><br />

## `REST API`의 단점

- 사용할 수 있는 메소드가 4 가지 밖에 없다.
- HTTP 통신 모델에 대해서만 지원한다.

<br /><br />

---

### ✨ tl;dr

✔️ REST API란?

- 정보를 주고받는 데에 있어서 개발자들 사이에 널리 쓰이는 일종의 형식
- 각 요청이 어떤 동작이나 정보를 위한 것인가를 그 요청의 모습 자체로 추론 가능하다
