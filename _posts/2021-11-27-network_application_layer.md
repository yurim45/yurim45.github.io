---
title: "🌏 네트워크 구조 이해:: OSI모델의 응용 계층"
tags:
  - [network]
permalink: /network/applicationLayer

navigation: true
toc: true
toc_sticky: true

date: 2021-11-27
last_modified_at: 2021-11-27
---

![]()

<span style="color:Teal">**OSI모델**</span>의 7계층인 <span style="color:Teal">**응용 계층**</span>에 대해 공부하기

---

# 🌏 응용 계층_애플리케이션에 데이터 전송하기

### 🚀 What I Will Learn

- 응용 계층의 역할에 대해 이해한다
- 웹 서버의 구조를 이해한다
- DNS의 이름 해석 구조를 이해한다
- 메일의 송수신 구조를 이해한다

---

## <span style="background-color:aquamarine">LESSON 28. 응용 계층의 역할</span>

### 1) 응용 계층의 역할

>클라이언트 측 애플리케이션과 서버 측 애플리케이션이 통신하기 위해 **응용 계층**의 프로토콜을 사용해야 한다!

![](https://images.velog.io/images/april_5/post/6e588407-b227-4f8c-b6c9-672c81aa88e4/image.png)  

- 애플리케이션은
  - <span style="color:Teal">**서비스를 요청하는 측(클라이언트)**</span>과
    - 웹 브라우저, 메일 프로그램 등
  - <span style="color:Teal">**서비스를 제공하는 측(서버)**</span>으로 나뉜다
    - 웹 서버 프로그램, 메일 서버 프로그램 등

>**응용 계층** <br /> ① 애플리케이션이 동작하는 계층. 세션 계층과 표현 계층을 포함한다 <br /> ② <u>클라이언트의 요청을 전달하기 위해 서버 등이 이해할 수 있는 데이터로 변환하고 전송계층으로 전달</u>

![](https://images.velog.io/images/april_5/post/11b9b623-db9a-4a7a-b065-c4d192079123/image.png)    

클라이언트 측 애플리케이션과 서버 측 애플리케이션이 통신하기 위해 **응용 계층**의 <span style="color:Teal">**프로토콜**</span>을 사용해야 한다!

- 응용 게층의 대표적인 프로토콜

 |프로토콜|내용|
|:--:|:--:|
|HTTP|웹 사이트 접속|
|DNS|이름 해석|
|FTP|파일 전송|
|SMTP|메일 송신|
|POP3|메일 수신|

>**DNS의 이름 해석**: 네트워크에서 컴퓨터 등에 붙여진 이름을 기반으로 IP주소 찾는 것

![](https://images.velog.io/images/april_5/post/93523047-2c64-4bec-bac2-a84ce85e9a40/image.png)
 






