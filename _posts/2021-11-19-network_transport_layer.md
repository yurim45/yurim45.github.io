---
title: "🌏 네트워크 구조 이해:: OSI모델의 전송 계층"
tags:
  - [network]
permalink: /network/transportLayer

navigation: true
toc: true
toc_sticky: true

date: 2021-11-19
last_modified_at: 2021-11-19
---

![]()

<span style="color:Teal">**OSI모델**</span>의 4계층인 <span style="color:Teal">**전송 계층**</span>에 대해 공부하기

---

# 🌏 전송 계층_신뢰할 수 있는 데이터 전송하기

### 🚀 What I Will Learn

- 전송 계층의 역할을 이해한다
- 연결형 통신과 비연결형 통신을 이해한다
- TCP를 이해한다
- UDP를 이해한다

---

## <span style="background-color:aquamarine">LESSON 23. 전송 계층의 역할</span>

### 1) 전송 계층의 두 가지 역할

>① 데이터가 제대로 도착했는지 확인
② 전송된 데이터의 목적지가 어떤 애플리케이션인지 식별

OSI모델의 물리 계층, 데이터 링크 계층, 네트워크 계층의 3계층이 있으면 목적지에 데이터를 보낼 수 있다. 

네트워크 계층에서 다른 네트워크로 데이터를 전송하려면 라우터가 필요하고, 라우터의 라우팅 기능을 사용하여 전송할 수 있지만,
- 라우팅 정보가 잘못될 수 있고 
- 많은 라우터를 경유하는 도중에 라우터에 문제가 생기거나 
- 패킷이 손상되거나 유실되더라도

이 3계층에서는 아무것도 할 수 있는게 없다

>OSI모델의 전송 계층은 목적지에 신뢰할 수 있는 데이터를 전달하기 위해 필요!!!

![](https://images.velog.io/images/april_5/post/af235b3e-1c1c-4e85-a7ed-3681625c9878/image.png)

전송 계층에는 <span style="color:Teal">**오류를 점검하는 기능**</span>이 있어서 오류가 발생하면 데이터를 재전송하도록 요청한다

>즉, 네트워크 계층에서는 데이터를 전달하고
<span style="background-color:yellow">**전송 계층**에서는 데이터가 제대로 도착했는지 확인</span>

전송 계층은
컴퓨터가 데이터를 전달받고 어떤 애플리케이션에 전달해야 하는지 판단 후 해당 애플리케이션에 전달할 수 있도록 해준다

![](https://images.velog.io/images/april_5/post/c579339d-9124-43fe-80c4-4e0f1d5ba2d4/image.png)

<br />

>**- 전송 계층의 두 가지 역할**
① 데이터가 제대로 도착했는지 확인
② 전송된 데이터의 목적지가 어떤 애플리케이션인지 식별

<br />

### 1) 연결형 통신과 비연결형 통신

전송 계층의 특징을 간단히 요약하면 <span style="color:Teal">**신뢰성/정확성**</span>과 <span style="color:Teal">**효율성**</span>으로 구분할 수 있다

- **신뢰성/정확성**: 데이터를 목적지에 문제없이 전달하는 것
- **효율성**: 데이터를 빠르고 효율적으로 전달하는 것

여기서
<u>신뢰할 수 있고 정확한 데이터를 전달하는 통신</u>을 <span style="color:Teal">**연결형 통신**</span>이라고 하고,

>**연결형 통신**: <span style="color:Teal">**신뢰성/정확성**</span>이 우선인 통신이라서 여러 번 확인하고 보내는, 상대편과 확인해가며 통신하는 방식

<u>효율적으로 데이터를 전달하는 통신</u>을 <span style="color:Teal">**비연결형 통신**</span>이라고 한다

>**비연결형 통신**: <span style="color:Teal">**효율성**</span>이 우선인 통신이므로 확인 절차 없이 일방적으로 보내는, 상대편을 확인하지 않고 일방적으로 데이터를 전송하는 방식 <br /> 예시) 동영상: *데이터가 늦게 도착해서 화면이 버벅거리는 것 보다, 데이터가 약간 유실되더라도 원활하게 보는 것이 좋으니까!*

![](https://images.velog.io/images/april_5/post/2bade79f-eacd-4100-b01a-bc9111317e3a/OSI%20%E1%84%8C%E1%85%A5%E1%86%AB%E1%84%89%E1%85%A9%E1%86%BC%20%E1%84%80%E1%85%A8%E1%84%8E%E1%85%B3%E1%86%BC.jpeg)

전송 계층의 연결형 통신 프로토콜에는 <span style="color:Teal">**TCP**</span>가 사용되고, 비연결형 통신 프로토콜에는 <span style="color:Teal">**UDP**</span>가 사용된다




