---
title: "🌏 네트워크 기초 지식:: 통신의 기본 규칙"
tags:
  - [network]
permalink: /network/ptorocol

navigation: true
toc: true
toc_sticky: true

date: 2021-10-11
last_modified_at: 2021-10-11
---

![]()

`개인 공부 과정을 기록합니다.`

네트워크 통신의 기본 규칙인 <span style="background-color:aquamarine">프로토콜</span>에 대해 공부해보자!

---

# 🌏 네트워크 통신의 기본 규칙

### 🚀 What I Will Learn

- 프로토콜을 이해한다
- OSI 모델과 TCP/IP 모델을 이해한다
- 캡슐화와 역캡슐화를 이해한다

---

## <span style="background-color:aquamarine">LESSON 06. 네트워크의 규칙</span>

### 1) 프로토콜(protocol)이란?

><span style="color:Teal">**프로토콜(protocol)**</span>: 네트워크에서 지켜아 할 규칙(약속)

<br /><br />

---

## <span style="background-color:aquamarine">LESSON 07. OSI 모델과 TCP/IP 모델</span>

네트워크에서는 **데이터를 주고받기 위한 통신 규격**이 정해져 있는데, 이 통신 규격이 OSI 모델과 TCP/IP 모델이다

### 1) OSI 모델이란?

`ISO(International Organization for Standardization)`는 `국제 표준화 기구`이다. dl OSI에서 표준 규격을 제정했다. 이게 바로 <span style="color:Teal">**OSI 모델**</span>이다. 

><span style="color:Teal">**OSI 모델**</span>: 네트워크 기술의 기본이 되는 모델. 

<span style="background-color:yellow">데이터의 송수신은 컴퓨터에서 컴퓨터로 데이터를 전송하는 것</span>을 말하는데, 이때 컴퓨터 내부에서는 여러가지 일을 한다. 이러한 일은 일곱 개의 <span style="color:Teal">**계층**</span>으로 나뉘는데 그 계층이 바로 OSI 모델이다.
계층이라는 용어 대신 <span style="color:Teal">**레이어**</span>라는 용어를 사용하기도 한다.

![](https://images.velog.io/images/april_5/post/f7ffece7-35c1-46c2-8406-d7ad19a64c24/image.png)

통신을 할 때 데이터는 맨 위의 응용 계층에서 순차적으로 아래 계층으로 전달되고, 수신 측 데이터를 하위 계층에서 상위 계층으로 전달된다.
이때 각 계층은 독립적이므로 데이터가 전달되는 동안에 다른 계층의 영향을 받지 않는다.
그리고, <span style="background-color:yellow">각각의 계층에는 다양한 프로토콜이 있다.</span>


|계층|이름|설명|
|--|--|--|
|7계층|응용 계층 <br /> (어플리케이션 계층)|이메일 & 파일 전송, 웹 사이트 조회 등 어플리케이션에 대한 서비스를 제공|
|6계층|표현 계층 <br /> (프레젠테이션 계층)|문자 코드, 압축, 암호화 등의 데이터를 변환|
|5계층|세션 계층|세션 체결, 통신 방식을 결정|
|4계층|전송 계층 <br /> (트랜스포트 계층)|신뢰할 수 있는 통신을 구현|
|3계층|네트워크 계층|다른 네트워크와 통신하기 위한 경로 설정 및 논리 주소를 결정|
|2계층|데이터 링크 계층|네트워크 기기 간의 데이터 전송 및 물리 주소를 결정|
|1계층|물리 계층|시스템 간의 물리적인 연결과 전기 신호를 변환 및 제어|


<br /><br />

### 2) TCP/IP 모델이란?

><span style="color:Teal">**TCP/IP 모델**</span>: OSI 모델의 7계층을 4계층으로 변형된 모델

현재는 TCP/IP 모델을 사용하고 있다.

![](https://images.velog.io/images/april_5/post/a0ff80b0-88d9-4a82-9252-396caf1b3cf0/image.png)


<br /><br />

---

## <span style="background-color:aquamarine">LESSON 08. 캡슐화와 역캡슐화</span>

데이터를 송수신할 때는는 **캡슐화와 역캡슐화**가 이루어 진다.

### 1) 캡슐화와 역캡슐화란?

A컴퓨터에서 B컴퓨터로 데이터를 보내려면 데이터의 앞부분에 전송하는 데 필요한 정보를 붙여서 다음 게층으로 보내야 한다. 이 정보를 헤더라고 한다.
헤더에는 데이터를 전달받을 상대방에 대한 정보도 포함되어 있다.

![](https://images.velog.io/images/april_5/post/69b6b505-8f84-46f0-987d-68b041177bbc/image.png)

이처럼 헤더를 붙여 나가는 것을 캡슐화라고 하고, 데이터를 받는 쪽에서는 헤더를 하나씩 제거할 텐데, 이 것을 역캡슐화라고 한다.

일반적으로 5계층 세션 계층과 6계층 표현 계층은 7계층 응용계층에 포함하여 생각할 수 있어서 <span style="background-color:aquamarine">OSI 모델의 캡슐화와 역캡슐화 흐름</span>은 아래의 그림과 같다.

![](https://images.velog.io/images/april_5/post/0a4f1b14-3b77-42e8-92a0-d693d879dcde/OSI%20%E1%84%86%E1%85%A9%E1%84%83%E1%85%A6%E1%86%AF.png)

<br />

><span style="color:Teal">**캡슐화 과정**</span>
> 1) **응용 계층**에서 웹 사이트를 접속하기 위한 요청 데이터 생성
> 2) 해당 데이터는 전송 계층이 전달되고, **전송 계층**에서 신뢰할 수 있는 통신이 이루어지도록 응용 계층에서 만들어진 데이터에 **헤더**를 붙힌다
> 3) 이렇게 만들어진 데이터를 다른 네트워크와 통신하기 위해 **네트워크 계층**에서 헤더를 붙힌다
> 4) 네트워크 계층에서 만들어진 데이터에 물리적인 통신 채널을 연결하기 위해 **데이터 링크 계층**에서 **헤더**와 **트레일러**를 붙힌다
>  ㅤ• <span style="color:Teal">**트레일러**</span>: 데이터를 전달할 떄 데이터의 마지막에 추가하는 정보
> 5) 이렇게 만들어진 데이터는 최종적으로 <span style="color:Teal">**전기 신호**</span>로 변환돼서 수신측에 도착

역캡슐화는 캡슐화의 정 반대 과정이다.

><span style="color:tomato">**역캡슐화 과정**</span>
> 1) **데이터 링크 계층**에서 **데이터 링크 계층 헤더**와 **데이터 링크 계층 트레일러**를 제거
> 2) **네트워크 계층**에서 **헤더**를 제거
> 3) **전송 계층**에서 **헤더**를 제거
> 4) 그리고 **모든 헤더가 제거된 데이터**가 수신 측에 도착


<br /><br />

---

## 📌 참고!

### VPN이란?

><span style="color:dodgerblue">**VPN**</span>은 Virtual Private Network(가상 사설망)의 약어이다
>가상 통신 터널을 만들어 기업 본사나 자사와 같은 거점 간을 연결하여 통신하거나 외부에서 인터넷으로 사내에 접속하는 것을 말한다

예시) **서울**에 본사가 있고 **부산**에 자사가 있다면 
- **본사** 내부 랜(LAN)에서 **지사** 내부 랜(LAN)에 접속해 통신하는 것은 물리적인 거리가 멀어 어렵다. 
- 이럴 때는 <span style="color:dodgerblue">**VPN**</span>을 사용하여 본사와 지사를 연결하여 통신할 수 있다.

그리고 **VPN**은 <span style="background-color:yellow">두 종류</span>로 구성되어 있는데

- 1) 인터넷 VPN: 인터넷 VPN에는 거점 간 접속과 원격 접속 연결이 있다. 둘 다 일반 인터넷망을 사용한다.
  - 거점 간 접속은 IPsec이라는 암호 기술 프로토콜을 사용하여 접속
  - 반면 원격 접속 연결은 외부에서 사용하는 컴퓨터와 사내 네트워크를 연결하기 때문에 암호화된 통신로를 만든다.

 ![](https://images.velog.io/images/april_5/post/5e644b63-2553-4879-8e71-df9c4dab7314/image.png)

- 2) IP-VPN
  - MPLS라는 기술을 사용하며 인터넷망이 아닌 통신 사업자 전용 <span style="color:dodgerblue">**폐쇄망**</span>을 사용한다. 
  MPLS는 폐쇄망을 사용하기 때문에 제삼자에 의한 해킹이나 데이터 변조의 위험이 없어 암호화 기능이 필요하지 않다.

<br /><br />

---

### :: 용어 정리💡

- `프로토콜(protocol)`: 컴퓨터 간에 정보를 주고받을 때의 통신 방법에 대한 규칙이나 표준이다.

- `OSI 모델(Open Standards Interconnection model)`: 국제표준화기구(ISO)가 1977년에 정의한 국제 통신 표준 규약이다. 네트워크의 기본 구조를 일곱 개 계층으로 나눠서 표준화한 통신 규약으로 현재 다른 모든 통신 규약의 기반이 된다.

- `TCP/IP 모델(Transmission Control Protocol/Internet Protocol model)`: OSI 모델 7계층의 네트워크에서 데이터를 전송하는 과정을 네 개 계층(Layer)으로 단순화시켜 사용하는 모델이다. 인터넷 모델이라고도 한다.

- `캡슐화/역캡슐화(encapsulation/decapsulation)`: 캡슐화는 컴퓨터 통신에서 상위 계층의 통신 프로토콜 정보를 데이터에 추가하여 하위 계층으로 전송하는 기술이다. 반대로 역캡슐화는 상위 계층의 통신 프로토콜에서 하위 계층에서 추가한 정보와 데이터를 분리하는 기술이다.

- `헤더(header)`: 저장되거나 전송되는 데이터의 맨 앞에 위치하는 추가적인 정보 데이터다. 데이터의 내용이나 성격을 식별 또는 제어하는 데 사용한다.

