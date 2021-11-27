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
 

<br />

---

## <span style="background-color:aquamarine">LESSON 29. 웹 서버의 구조(웹 사이트 접속)</span>

### 1) `WWW` 란?

>**`WWW(World Wide Web)`**은 줄여서 **`W3`**나 **`웹(Web)`**이라고도 불린다

WWW는 
- <span style="background-color:yellow">HTML</span>(Hypertext Markup Language)
  - 웹 페이지에서 문장 구조나 문자를 꾸미는 <span style="color:Teal">**태그**</span>를 사용하여 작성하는 마크업 언어
    - 제목, 리스트, 이미지 등을 보여줄 때 태그를 사용
    
- <span style="background-color:yellow">URL</span>(Uniform Resource Locator)
- <span style="color:Teal">**HTTP**</span>(HyperText Transfer Protocol)

라는 세 가지 기술이 사용된다

<br />

### 2) HTTP란?

>클라이언트는 웹 사이트를 보기 위해 
웹 서버의 <span style="color:Teal">**80번 포트**</span>를 이용해 HTTP 통신을 한다.
: <span style="color:Teal">**HTTP 요청**</span>(request) & <span style="color:Teal">**HTTP 응답**</span>(response)

![](https://images.velog.io/images/april_5/post/bd3f267a-5cf0-4814-ba69-78e7c658ebf5/image.png)

클라이언트가 데이터를 <span style="background-color:yellow">요청</span>할 때는
- `GET`이라는 요청 정보와
- 파일 이름과 버전 등을

서버에 전송하고, 서버는 <span style="background-color:yellow">응답</span>으로
- 요청을 정상적으로 처리했다는 `OK`라는 정보를 반환하고
- 요청한 파일을 클라이언트에게 전송한다

<br />

---

## <span style="background-color:aquamarine">LESSON 30. DNS 서버의 구조 (=이름 해석)</span>

응용 계층에는 <u>이름 해석을 통해 도메인 이름을 IP주소로 변환하는 역할을 하는 DNS</u>가 있다. DNS의 구조에 대해 알아보자.

### 1) 도메인 이름이란?

>- **도메인 네임**: 컴퓨터나 네트워크를 식별하기 위해 붙여진 이름 
  - 예시) www.example.com
- **호스트 이름(서버 이름)**: 도메인 이름 앞에 있는 www
- **DNS**: URL을 IP 주소로 변환하는 서비스(시스템)

컴퓨터(서버)의 <span style="color:Teal">**IP주소**</span>를 통해 웹 서버에 접속한다.
- IP주소: 0 ~ 255까지의 숫자 네 개로 구성된 주소 세트
  - 예시) 222.212.45.222

>컴퓨터(서버)에 접속하려면 IP주소를 입력해야 하는데, https://github.com/yurim45 를 입력했다.
IP 주소가 아닌데 웹 사이트에 접속할 수 있는건, 
DNS를 통해 IP 주소와 짝꿍인 URL로 변환되기 때문
![](https://images.velog.io/images/april_5/post/ea230dc6-abe9-4b53-a54d-4e0411bfb0d3/image.png)

- 도메인 이름
  - 컴퓨터나 네트워크를 식별하기 위해 붙여진 이름
  - 앞에 www와 같은 호스트 이름(서버 이름)이 붙는다

- DNS
  - <span style="background-color:yellow">URL을 IP 주소로 변환하는 서비스(시스템)</span>
  - IP 주소가 아닌 ( 호스트 이름 + 도메인 이름 )으로부터 접속 가능하게 해주는 <span style="color:Teal">**이름 해석**</span>을 제공한다.
  - <span style="color:Teal">**DNS 서버**</span>가 입력한 URL의 IP주소를 알려주며, 
  전 세계에 흩어져 있다. 모두 계층적으로 연결되어 있다.

![](https://images.velog.io/images/april_5/post/e42dc578-7ada-445c-8023-d189331ca506/image.png)


<br />

---

## <span style="background-color:aquamarine">LESSON 31. 메일 서버의 구조 (=SMTP, POP3)</span>

### 1) 메일의 송수신 구조

메일의 송수신 프로토콜에는
- <span style="color:Teal">**SMTP**</span> : 메일을 보내는 데 사용되는 프로토콜.
  - 포트 <span style="color:Teal">**25**</span>번 사용
- <span style="color:Teal">**POP3**</span> : 메일을 받는 데 사용되는 프로토콜. 
  - 포트 <span style="color:Teal">**110**</span>번 사용

가 있다

![](https://images.velog.io/images/april_5/post/06bed1ba-fde3-4359-aa2f-e81a79ac9951/SMTP%20POP3.jpeg)

메일 송수신 흐름
① SMTP를 이용, 컴퓨터 1에서 메일 서버 1로 메일 송신
② SMTP를 이용, 메일 서버 1에서 메일 서버 2로 메일 송신
③ POP3를 이용, 메일 서버 2에서 컴퓨터 2로 메일 데이터 수신

<br />

### 2) SMTP를 이용한 메일 송신 & 메일 전송

메일 프로그램은 <span style="color:Teal">**SMTP**</span>를 사용하여 <u>컴퓨터 1 ➔ 메일 서버 1 ➔ 메일 서버 2</u>로 메일을 보낸다.


![](https://images.velog.io/images/april_5/post/9de7c602-2c95-44c2-8709-f1c09de56338/image.png)

![](https://images.velog.io/images/april_5/post/06bed1ba-fde3-4359-aa2f-e81a79ac9951/SMTP%20POP3.jpeg)

<br />

### 3) POP3를 이용한 메일 수신

메일의 수신에는 **사용자 이름**과 **비밀번호**를 이용한 <span style="background-color:yellow">사용자 인증</span>이 필요하다.

![](https://images.velog.io/images/april_5/post/c6b69165-b519-47af-a19a-5b27eaab0a37/image.png)

메일 박스는
- <u>메일을 보관하는 메일 서버의 기능</u>이다.
- 메일 서버는 <span style="color:Teal">**POP3**</span>를 이용, 메일 서버의 메일 박스에서 메일을 가져와 컴퓨터로 전송한다.

![](https://images.velog.io/images/april_5/post/815b4880-4f1a-449f-b33e-c0bcc9ed9ba0/image.png)

메일 수신 과정
① 세션을 시작한다. 
② 컴퓨터 2에서 받는 사람의 사용자 이름을 통지하고 메일 서버 2에 `OK`라는 확인 응답을 반환한다.
③ 컴퓨터 2에서 수신자의 비밀번호를 통지하고 메일 서버 2에 `비밀번호 확인`이라는 확인 응답을 반환한다.
④ 컴퓨터 2에서 자신의 메일이 있는지 확인하고 메일 서버 2는 `있음`이라는 확인 응답을 반환한다.
⑤ 컴퓨터 2에서 메일 박스에 보관된 이메일을 전송받는다.
⑥ 세션을 종료한다.

<br />

>**PING 명령**
- 목적지 컴퓨터와의 통신 확인을 위한 명령
- ICMP 프토콜을 이용, 
- 목적지 컴퓨터에 ICMP 패킷을 전송하고 패킷에 대한 응답이 제대로 오는지를 확인해 네트워크 연결이 정상인지를 판단한다.

<br /><br />

---

### :: 용어 정리💡

- `응용 계층(application layer, 애플리케이션 계층)`: OSI 모델의 최상위 계층으로 다양하게 존재하는 응용 환경에서 공통적으로 필요한 기능을 다룬다. 시스템 간의 응용 처리는 상호 간에 통신하면서 일련의 업무를 처리할 수 있도록 필요한 서비스 기능을 제공한다. 이메일, 파일 전송, 웹 사이트 조회 등 애플리케이션에 대한 서비스를 제공하는 계층이다.

- `WWW(World Wide Web, 월드 와이드 웹)`: 거대한 통신망인 인터넷은 수많은 사이트, 데이터, 정보를 갖고 있으며, 통신 회선이 거미줄처럼 서로 연결되어 있어서 언제 어디서든 필요한 곳에 접근하거나 정보를 공유하고 주고 받을 수 있는 멀티미디어 인터넷 서버다.

- `HTTP(HyperText Transfer Protocol)`: 웹 서비스에서 클라이언트(웹 브라우저)와 웹 서버 간에 정보를 주고 받기 위해 사용되는 네트워크 프로토콜이다.

- `DNS(Domain Name System, 도메인 이름 시스템)`: 네트워크에서 호스트 이름을 IP 주소로 변환하는 데 사용되는 시스템(서비스)이다. DNS 서비스가 동작하는 컴퓨터(서버)를 DNS 서버라고 한다.

- `FTP(File Transfer Protocol, 파일 전송 프로토콜)`: 서버와 클라이언트 간에 파일을 전소하기 위한 프로토콜이다. 일반적으로 통신 포트는 제어 용도로는 21번을 사용하고 데이터 전송 용도로는 20번 포트를 사용한다.

- `SMTP(Simple Mail Transfer Protocol, 단순 메일 전송 프로토콜)`: 인터넷에서 메일을 전송하는 데 사용하는 프로토콜이다. 통신 포트는 일반적으로 25번을 사용한다. SMTP에서 지원하는 서버를 SMTP 서버라고 한다.

- `POP3`: 인터넷에서 메일을 수신하는 데 사용하는 프로토콜이다. 통신 포트는 일반적으로 110번을 사용한다. POP3를 지원하는 서버를 POP3 서버라고 한다.

- `HTML(HyperText Markup Language)`: 인터넷 서비스의 하나인 WWW를 통해 볼 수 있는 문서를 만들 때 사용하는 프로그래밍 언어다. 하이퍼텍스트를 작성하기 위해 개발되었다.

- `URL(Uniform Resource Locator)`: 인터넷에서 파일 위치를 지정하기 위해 기술된 주소다. 웹 사이트 주소를 지정하기 위해 사용한다.



