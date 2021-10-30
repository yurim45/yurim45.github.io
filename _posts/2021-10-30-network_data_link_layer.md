---
title: "🌏 네트워크 구조 이해:: OSI모델의 데이터 링크 계층"
tags:
  - [network]
permalink: /network/dataLinkLayer

navigation: true
toc: true
toc_sticky: true

date: 2021-10-30
last_modified_at: 2021-10-30
---

![]()

`개인 공부 과정을 기록합니다.`

<span style="color:Teal">**OSI모델**</span>의 2계층인 <span style="color:Teal">**데이터 링크 계층**</span>에 대해 공부하기

---

# 🌏 데이터 링크 계층:: 랜에서 데이터 전송하기

### 🚀 What I Will Learn

- 이더넷(Ethernet)을 이해한다
- CSMA/CD방식을 이해한다
- MAC 주소를 이해한다
- 스위치를 이해한다
- 충돌 도메인을 이해한다
- 이더넷 표준을 이해한다

---

## <span style="background-color:aquamarine">LESSON 12. 데이터 링크 계층의 역할과 이더넷</span>

랜에서는 데이터를 주고받는 규칙으로 `이더넷`을 사용. 그럼 **이더넷(Ethernet)**이란?


### 1) 이더넷(Ethernet)이란?

랜에서 데이터를 주고 받으려면, 두 번째 계층인 <span style="color:Teal">**데이터 링크 계층**</span>의 기술이 필요.

![](https://images.velog.io/images/april_5/post/670938b8-0dd4-4530-b253-0df00b4f3c03/image.png)

>**데이터 링크 계층**: 네트워크 장비 간에 신호를 주고받는 규칙을 정하는 계층. 

랜에서 데이터를 정상적으로 주고받기 위해 필요한 계층이다. 그 규칙들 중 가장 많이 사용되는 규칙이 **이더넷(Ethernet)**

>**이더넷(Ethernet)**: 랜에서 적용되는 규칙. 허브와 같은 장비에 연결된 컴퓨터와 데이터를 주고받을 때 사용.
>>**허브**: 약해지거나 파형이 뭉그러진 전기 신호를 복원시키고, 해당 전기 신호를 전달받은 포트를 제외한 나머지 포트에 전달하는 역할을 한다. <br />
더미 허브라고도 불리는 이유는, 들어온 데이터를 그대로 모든 포트에 보내기만 하기 때문.

특정 컴퓨터에만 데이터를 보내는데, 관계 없는 다른 컴퓨터들이 그 데이터를 받아 본다면? 😱😱😱😱😱😱😱😱😱😱😱
이런 경우를 대비해서 *다른 컴퓨터는 데이터를 못보도록 하는 규칙*이 정해져 있다
- 그래서 보내려는 데이터에 **목적지** 정보를 추가해서 보내고, 
- 목적지 이외의 컴퓨터는 데이터를 받아도 무시하게 된다

다만, 컴퓨터 여러 대가 동시에 데이터를 보내면 데이터들이 서로 부딪힐 수 있는데 즉 충돌(collision)이 일어날 수 있는데 

![](https://images.velog.io/images/april_5/post/5f2edf3a-b29c-4f58-a2aa-66f8b4e282d6/image.png)

<span style="background-color:yellow">이더넷은 여러 컴퓨터가 동시에 데이터를 전송해도 충돌이 일어나지 않는 구조</span>로 되어있다
- 데이터가 동시에 케이블을 지나가면 충돌할 수 밖에 없어서 데이터를 보내는 시점을 늦추게 되는데, 이더넷에서 시점을 늦추는 방법을 **CSMA/CD**라고 한다

<br />

### 2) CSMA/CD이란?

>**CSMA/CD**: Carrier Sense Multiple Access with Collision Detection의 약어로 **반송파 감지 다중 접속 및 충돌 탐지**라는 뜻을 가진다

CSMA/CD에서 
<span style="color:Teal">**CS**</span>는 `데이터를 보내려고 하는 컴퓨터가 케이블에 신호가 흐르고 있는지 아닌지를 확인한다`는 규칙
<span style="color:Teal">**MA**</span>는 `케이블에 데이터가 흐르고 있지 않다면 데이터를 보내도 좋다`라는 규칙
<span style="color:Teal">**CD**</span>는 `충돌이 발생하고 있는지를 확인한다`는 규칙

이러한 규칙으로 데이터를 주고받으면 충돌이 일어나지 않는다

![](https://images.velog.io/images/april_5/post/f1b59d35-c811-44f7-9583-eee7337e63ab/image.png)

<span style="background-color:yellow">하지만 <span style="color:tomato">지금은 효율이 좋지 않다는 이유로 CSMA/CD는 거의 사용하지 않고</span>
**스위치(switch)**라는 네트워크 장비를 사용하여 충돌을 막는다</span>

<br /><br />

---

## <span style="background-color:aquamarine">LESSON 13. MAC(Media Access Control Address) 주소의 구조</span>

랜 카드를 제조할 때 정해지는 물리적인 주소에 대해 알아보자

### 1) MAC(Media Access Control Address) 주소란?

랜 카드는 비트열(0과 1)을 전기로 변환하는데, 이런 랜카드에는 
- **MAC(Media Access Control Address) 주소**라는 번호가 정해져 있다. 
- 제조할 때 새겨지기 때문에 물리 주소라고도 부르며 
- **전 세계에서 유일한 번호**로 할당되어 있다
  - 중복되지 않도록 규치깅 명확하게 정해져 있고 48비트 숫자로 구성되어 있다
  - 그 중 앞쪽 24비트는 랜카드를 만드는 제조사 번호
  - 뒤쪽 24비트는 제조사가 랜카드에 붙인 일련번호
  
  ![](https://images.velog.io/images/april_5/post/7dc1d245-1009-4936-b1f1-37d57b318a27/image.png)


### 2) MAC 주소를 사용한 통신

OSI 모델이나 TCP/IP 모델에서는 각 계층에 헤더를 붙인다
- OSI 모델은 데이터 링크 계층에 해당
- TCP/IP 모델에서는 네트워크 계층에 해당

![](https://images.velog.io/images/april_5/post/b7c1d0c8-c65e-44de-8d5a-c97cbf1b2053/image.png)

이 계층에서 <span style="color:Teal">**이더넷 헤더**</span>와 <span style="color:Teal">**트레일러**</span>를 붙인다
그리고 이렇게 이더넷 헤더와 트레일러가 추가된 데이터를 <span style="color:Teal">**프레임**</span>이라고 한다

이더넷 헤더는 총 14바이트로 구성되어 있다
  - 목적지의 MAC 주소(6바이트)
  - 출발지 MAC 주소(6바이트)
  - 유형(2바이트) 

![](https://images.velog.io/images/april_5/post/912a9f25-ce96-41c7-996d-964c3b65a058/image.png)

**이더넷 유형(Ethernet type)**은 이더넷으로 전송되는 상위 계층 <span style="background-color:yellow">프로토콜의 종류를 나타내는데, 식별하는 16진수 번호</span>가 들어간다

|유형 번호|프로토콜|
|--|--|
|0800|IPv4|
|0806|ARP|
|8035|RARP|
|814C|SNMP over Ethernet|
|86DD|IPv6|

<br />

<span style="color:Teal">**트레일러**</span>는 <span style="color:Teal">**FCS(Frame Check Sequence)**</span>라고도 하는데, 데이터 전송 도중에 오류가 발생하는지 확인하는 용도로 사용한다

<br />

네트워크를 통해 프레임(이더넷 헤더와 트레일러가 추가된 데이터)이 전송되는데
- 이더넷 헤더에 데이터의 목적지인 컴퓨터 주소(<span style="color:Teal">**목적지 MAC 주소**</span>)와 자신의 주소(<span style="color:Teal">**출발지 MAC 주소**</span>)를 넣고 데이터를 전송 → 이때 <span style="background-color:yellow">캡슐화</span>가 일어난다

>📌요악하면!! 💡데이터 링크 계층에서 데이터에 이더넷 헤더와 트레일러를 추가하여 <span style="color:Teal">**프레임**</span>을 만들고, 💡물리 계층에서 이 프레임 비트열을 <span style="color:Teal">**전기 신호**</span>로 변환하여 네트워크를 통해 전송

![](https://images.velog.io/images/april_5/post/7391c047-fd86-4177-a0b3-d79d57496276/image.png)


<br /><br />

---

## <span style="background-color:aquamarine">LESSON 14. 스위치(switch)의 구조</span>

스위치(switch)는 허브와 달리 데이터 충돌이 발생하지 않는다. 네트워크 구성에서 빠질 수 없는 스위치에 대해 알아보자.

### 1) MAC(Media Access Control Address) 주소 테이블란?

스위치(switch)는
- <span style="color:Teal">**데이터 링크 계층**</span>에서 동작하고
- <span style="color:Teal">**레이어 2 스위치**</span> 또는 <span style="color:Teal">**스위칭 허브**</span>라고도 불린다
- 장비 외형은 허브와 비슷하다

스위치 내부에는 
- <span style="background-color:yellow">MAC 주소 테이블(MAC address table)</span> 또는 브리지 테이블 (bridge table)이라는 것이 있고

MAC 주소 테이블은 
- 스위치의 <span style="color:Teal">**포트 번호**</span>와 해당 포트에 연결 되어 있는 컴퓨터의 <span style="color:Teal">**MAC 주소**</span>가 등록되는 데이터 베이스다.

<br />

스위치의 전원을 켰을때 
- MAC 주소 테이블에는 아무것도 등록되어 있지 않고
- 컴퓨터에서 목적지 MAC 주소가 추가된 프레임이 전송되면 MAC 주소 테이블을 확인하고 
- 출발지 MAC 주소가 등록되어 있지 않으면 MAC 주소를 포트와 함께 등록한다

이런 기능을 **MAC 주소 학습 기능**이라고 하고, 더미 허브에는 없는 기능이다.

![](https://images.velog.io/images/april_5/post/bad17781-811a-440e-b04e-89baa0fbdffb/image.png)

스위치가 수신 포트 이외의 모든 포트에서 데이터를 송신하는 것을 <span style="color:Teal">**플러딩(flooding, 홍수)**</span>이라고 한다.

스위치에서 MAC 주소를 기준으로 목적지를 선택하는 것을 <span style="color:Teal">**MAC 주소 필터링**</span>이라고 한다.


<br /><br />

---

## <span style="background-color:aquamarine">LESSON 15. 데이터가 케이블에서 충돌하지 않는 구조</span>

케이블에 데이터가 아무리 많이 전송되어도 데이터가 충돌하지 않는 구조 이해하기

### 1) 전이중 통신과 반이중 통신

- <span style="color:Teal">**전이중 통신 방식**</span>은 데이터의 송수신을 동시에 통신하는 방식. 데이터를 <span style="color:tomato">**동시에 전송해도 충돌이 발생하지 않는다**</span>

  - 컴퓨터를 두 대를 랜 케이블을 직접 연결한 경우

![](https://images.velog.io/images/april_5/post/b0c91019-be1e-4e8c-83de-a520dc398281/image.png)

<br />


- <span style="color:Teal">**반이중 통신 방식**</span>은 회선 하나로 송신과 수신을 번갈아가면서 통신하는 방식. 데이터를 <span style="color:tomato">**동시에 전송하면 충돌이 발생**</span>한다.

  - 컴퓨터 두 대를 허브에 연결한 경우
  
![](https://images.velog.io/images/april_5/post/147ec02c-e921-4fec-8c5c-d8dd663d4bf7/image.png)

<br />

- 스위치는 충돌이 일어나지 않는 구조로 되어 있기 때문에 <span style="color:Teal">**전이중 통신 방식**</span>으로도 데이터를 주고 받을 수 있다
  - 컴퓨터 두 대를 스위치에 연결한 경우
  
  ![](https://images.velog.io/images/april_5/post/8f52d451-d7f0-4e92-89b0-29696bb114ee/image.png)
  
<br />

### 2) 충돌 도메인(collsion domain)이란?

**충돌 도메인(collsion domain)**: 허브는 반이중 통신 방식으로 동시에 데이터를 전송하면 충돌이 일어나는데, 충돌이 발생할 때 그 영향이 미치는 범위. 충돌 도메인이 넓을수록 네트워크가 지연된다.

![](https://images.velog.io/images/april_5/post/dbf24684-d444-4c04-b002-21f0ed031ed4/image.png)


<br /><br />

---

## <span style="background-color:aquamarine">LESSON 16. 이더넷의 종류와 특징</span>

케이블에 데이터가 아무리 많이 전송되어도 데이터가 충돌하지 않는 구조 이해하기

### 1) 이더넷 규격

다음 표에 이더넷의 대표적인 규격을 정리해뒀다.

|규격 이름|	통신 속도|	케이블|	케이블 최대 길이	|표준화 연도|
|--|--|--|--|--|
|10BASE5	|10Mbps	|동축케이블	|500m|	1982년|
|10BASE2	|10Mbps	|동축케이블	|185m|	1988년|
|10BASE-T	|10Mbps	|UTP케이블(Cat3이상)	|100m|	1990년|
|100BASE5-TX	|100Mbps	|UTP케이블(Cat5이상)	|100m	|1995년|
|1000BASE-T	|1000Mbps	|UTP케이블(Cat5이상)|	100m	|1999년|
|10GBASE-T	|10Gbps|	UTP케이블(Cat6a이상)	|100m	|2006년|

![](https://images.velog.io/images/april_5/post/0d8760e3-7794-4888-9d34-1e02c92a51c6/image.png)

- 10: Mbps 단위인 통신 속도
- BASE: BASEBAND라는 전송 방식
- T: 케이블 종류

<br /><br />

---

### :: 용어 정리💡

- `데이터 링크 계층(data link layer)`: 네트워크 기기 간에 데이터를 전송하고 물리 주소를 결정한다.

- `이더넷(Ethernet)`: 컴퓨터 네트워크 기술 중 하나로 전 세계의 사무실이나 가정에서 일반적으로 사용되는 랜에서 가장 많이 활용되는 기술 규격이다.

- `충돌(collision)`: 데이터를 한 번에 하나만 전송 할 수있는 채널에 전송 장치 두 개가 같은 시점에 패킷을 보낼 때 일어나는 데이터 충돌을 말한다.

- `MAC 주소(Medium Access Control address)`: 랜에 사용되는 네트워크 모델인 이더넷의 물리적인 주소로 컴퓨터 네트워크에서 각각의 기기를 구분하기 위해 사용하는 주소다.

- `스위치(switch, 스위칭 허브)`: 랜을 구성할 때 사용하는 단말기 간 스위칭 기능이 있는 통신망 중계 장치다. 컴퓨터(호스트)에서 특정한 다른 다른 단말기로 패킷을 보낼 수 있는 기능이 있어 통신 효율이 향상된다.

- `전이중 통신 방식(full-duplex communication)`: 전화 회선과 같이 송신과 수신이 양쪽에서 동시에 이루어지는 양방향 통신이다. 서로 다른 회선이나 주파수를 이용하여 데이터 신호가 충돌되는 상황을 방지한다. 스위칭 허브를 사용하면 랜 카드와 허브 간의 동시 송수신이 가능해진다.

- `ARP(Address Resolution Protocol, 주소 변환 프로토콜)`: 네트워크 계층 주소와 데이터 링크 계층 주소사이의 변환을 담당하는 프로토콜이다. IP 주소를 물리 주소인 MAC 주소로 변환하는 데 사용한다.

- `ARP 캐시(ARP cache)`: 가장 최근에 변환한 'IP 대 하드웨어 주소'를 보관하고 있는 램(RAM)의 한 영역이다.

- `ARP 요청(ARP request)`: IP 주소를 대치할 수 있는 물리 주소인 MAC 주소를 찾아내기 위해 보내는 브로트캐스트 패킷 요청이다.

- `ARP 응답(ARP reply)`: ARP 요청(request)에 대한 응답으로 요청한 IP 주소에 대한 물리 주소인 MAC 주소가 실려있다.