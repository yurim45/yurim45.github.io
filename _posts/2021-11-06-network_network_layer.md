---
title: "🌏 네트워크 구조 이해:: OSI모델의 네트워크 계층"
tags:
  - [network]
permalink: /network/network_layer

navigation: true
toc: true
toc_sticky: true

date: 2021-11-06
last_modified_at: 2021-11-06
---

![]()

<span style="color:Teal">**OSI모델**</span>의 3계층인 <span style="color:Teal">**네트워크 계층**</span>에 대해 공부하기

---

# 🌏 네트워크 계층\_목적지에 데이터 전달하기

### 🚀 What I Will Learn

- IP를 이해한다
- 라우터를 이해한다
- IP주소를 이해한다
- 서브넷(subnet)을 이해한다
- 라우팅을 이해한다

---

## <span style="background-color:aquamarine">LESSON 17. 네트워크 계층의 역할</span>

전 세계에는 수많은 네트워크가 있고 그 네트워크들은 서로 연결되어 거대한 인터넷을 이루고 있다. 이번에는 <u>**네트워크 간의 연결**</u>에 대해 알아보자

### 1) 네트워크 간의 연결 구조

> ✔️ **네트워크 계층의 역할**: 다른 네트워크에 있는 목적지로 데이터를 전달하려면 네트워크 계층의 기술이 필요하다

![](https://images.velog.io/images/april_5/post/c272c3b2-434e-4d1b-adbb-c831271bb50e/image.png)

<u>**데이터 링크 계층**</u>에서는 이더넷 규칙을 기반으로 데이터 전송을 담당.
하지만 이 규칙에 따라 같은 네트워크에 있는 컴퓨터로는 데이터를 전송할 수 있지만, <span style="background-color:yellow">인터넷이나 다른 네트워크로는 데이터를 전송할 수 없다</span> 😥😥😥😥😥

- 데이터 링크 계층의 장비로는 네트워크 A의 컴퓨터 끼리는 데이터 전송이 되지만, 네트워크 A에서 네트워크 B나 C로는 데이터 전송이 안된다.

![](https://images.velog.io/images/april_5/post/5700820d-ec14-43c2-b801-e5470ea5319d/image.png)

이 네트워크 간의 통신을 가능하게 하는 것이 **네트워크 계층의 역할**이다.
이 계층을 통해 다른 네트워크로 데이터를 전송하려면 <span style="color:Teal">**라우터(router)**</span>라는 네트워크 장비가 필요하다

> **라우터(router)**: 목적지가 정해지면 <span style="color:tomato">**해당 목적지까지 어떤 경로로 가는 것이 좋은지**</span>를 알려주는 기능을 한다.

하지만 데이터를 보내려는 상대가 어디에 있는지 모르면 라우터도 목적지까지의 경로를 알려주지 못한다. 이 때 <u>네트워크를 식별할 수 있는 주소</u>를 <span style="color:Teal">**IP 주소**</span>라고 한다

IP 주소로

- 목적지를 지정하는 것 뿐만 아니라
- 데이터를 어떤 경로로 보낼지도 결정해야 한다
- 목적지 IP 주소까지 어떤 경로로 데이터를 보낼지 결정하는 것을 <span style="color:Teal">**라우팅(routing)**</span>이라고 한다
  - 라우터의 **라우팅 테이블(routing table)**로 경로 정보를 등록하고 관리한다

![](https://images.velog.io/images/april_5/post/b941a45c-707a-40ba-80c8-21220094bb8a/image.png)

<br />

### 2) IP(Internet Protocol)란?

네트워크 계층에는 IP라는 프로토콜이 있고, 이 IP가 있어서 라우터가 가능한 것이다.

네트워크 계층에서는 <span style="background-color:yellow">캡슐화</span>를 할 때는 데이터에 <span style="color:Teal">**IP헤더**</span>가 추가되는데, 이렇게 만들어진 것을 <span style="color:Teal">**IP패킷**</span>이라고 한다

- 데이터 링크 계층에서 이더넷 헤더와 트레일러가 추가 된것은 <span style="color:Teal">**프레임**</span>이라고 했다

![](https://images.velog.io/images/april_5/post/1654d302-8c60-433e-9108-0788eb522925/image.png)

> 📌 IP 헤더에 **출발지 IP주소**와 **목적지 IP 주소**가 있다는 것을 기억하자!

<br /><br />

---

## <span style="background-color:aquamarine">LESSON 18. IP 주소의 구조</span>

### 1) IP 주소란?

> IP 주소는 실생활에 비유하면 우편물을 보낼 때의 주소와 같은 개념이다.

IP 주소는 <span style="color:Teal">**인터넷 서비스 제공자(ISP)**</span>에게 받을 수 있다.
IP 버전에는 <span style="color:Teal">**IPv4**</span>와 <span style="color:Teal">**IPv6**</span>가 있다

|              | IPv4           | IPv6            |
| ------------ | -------------- | --------------- |
| 크기         | 32비트         | 128비트         |
| IP 주소 갯수 | 약 43억(億) 개 | 약 340간(澗) 개 |

> 일(一) 십(十) 백(百) 천(千) 만(萬) 억(億) 조(兆) 경(京) 해(垓) 자(秭) 양(穰) 구(溝) **간(澗)** 정(正) 재(載) 극(極) ···

IP 주소에는 <span style="color:Teal">**공인 IP 주소**</span>와 <span style="color:Teal">**사설 IP 주소**</span>가 있는데 왜 두 종류나 필요할까?

- IPv4 주소는 위에서 말했듯이 주소의 수가 고갈되고 있다
- 그래서 <u>인터넷에 직접 연결되는 컴퓨터나 라우터</u>에는 <span style="color:Teal">**공인 IP 주소**</span>를 할당하고,
- <u>회사나 가정의 랜에 있는 컴퓨터</u>는 <span style="color:Teal">**사설 IP 주소**</span>를 할당하는 정책을 사용하고 있다.

![](https://images.velog.io/images/april_5/post/0b42b0cf-7f02-49ae-bd02-1e0c3aac0121/image.png)

- 랜 안에 컴퓨터가 여러 대 있다면 공인 IP 주소는 사용할 수 있는 숫자가 제한되므로
  - 컴퓨터 한 대당 공인 IP 주소를 하나씩 할당하기 어렵다
- 그래서 우선, <u>인터넷 서비스 제공자가 제공하는 **공인 IP 주소**</u>는 <span style="color:tomato">**라우터에만 할당**</span>하고
- 랜 안에 있는 컴퓨터에는
  - 랜의 네트워크 관리자가 자유롭게 **사설 IP 주소**를 할당하거나
  - 라우터의 **DHCP** 기능을 사용하여 주소를 자동으로 할당한다

그러면 공인 IP 주소 한 개로 랜안에 있는 컴퓨터 세대에 인터넷을 모두 연결할 수 있는 환경을 만들 수 있다

> **DHCP(Dynamic Host Configuration Protocol)**: IP 주소를 자동으로 할당하는 프로토콜

<br />

IP 주소와 MAC 주소는 비트 수가 다른데,

|      | MAC 주소 | IP 주소 |
| ---- | -------- | ------- |
| 크기 | 48비트   | 32비트  |
| 표시 | 16진수   | 10진수  |

> 8비트를 옥텟(octet)이라고 부르기도 한다 <br /> 32비트를 8비트씩 끊어서 네 개의 옥텟으로 구분하고, <br /> 숫자는 10진수로 변환했을 때 0~255까지 범위가 정해져 있다

![](https://images.velog.io/images/april_5/post/290d6cd2-28ea-4fbb-9482-d8790c9b2b86/image.png)

> 📌 사람이 읽기 쉽도록 10진수로 표시하지만, 실제로 IP주소는 <span style="color:tomato">**2진수**</span>로 되어있다는 것을 기억하자!

또한, IP 주소는 <span style="color:Teal">**네트워크 ID**</span>와 <span style="color:Teal">**호스트 ID**</span>로 나눠져 있다.

- **네트워크 ID**는 <u>어떤 네트워크인지</u>를 나타내고,
- **호스트 ID**는 <u>해당 네트워크의 어느 컴퓨터인지</u>를 나타낸다.

이 두 가지 정보가 합쳐져 IP 주소가 된다.

<br /><br />

---

## <span style="background-color:aquamarine">LESSON 19. IP 주소의 클래스(class) 구조</span>

IP 주소는 <u>네트워크의 규모에 따라 A~E 클래스로 나누어져</u> 있다. 네트워크 클래스 구조에 대해 알아보자.

### 1) IP 주소 클래스(class)란?

IPv4의 IP 주소는 32비트다.

- 이 32비트를 옥탯 단위로 끊어서 네트워크 ID를 크게 만들거나
- 호스트 ID를 작게 만들어 네트워크 크기를 조정할 수도 있다

<u>네트워크 크기는 <span style="color:Teal">**클래스**</span> 라는 개념으로 구분</u>하고 있다

| 클래스 이름 | 내용                       | 네트워크 ID 크기 | 호스트 ID |
| ----------- | -------------------------- | ---------------- | --------- |
| A 클래스    | 대규모 네트워크 주소       | 8비트            | 24비트    |
| B 클래스    | 중형 네트워크 주소         | 16비트           | 16비트    |
| C 클래스    | 소규모 네트워크 주소       | 24비트           | 8비트     |
| D 클래스    | 멀티캐스트(multicast) 주소 | x                | x         |
| E 클래스    | 연규 및 특수용도 주소      | x                | x         |

일반 네트워크에서는 A~C 클래스까지 사용할 수 있다

| 종류     | 공인 IP 주소의 범위                                          | 사설 IP 주소의 범위         |
| -------- | ------------------------------------------------------------ | --------------------------- |
| A 클래스 | 1.0.0.0~9.255.255.255 <br /> 10.0.0.0~10.255.255.255         | 11.0.0.0~126.255.255.255    |
| B 클래스 | 128.0.0.0~172.15.255.255 <br /> 172.16.0.0~172.31.255.255    | 172.32.0.0~191.255.255.255  |
| C 클래스 | 192.0.0.0~192.167.255.255 <br /> 192.168.0.0~192.168.255.255 | 192.169.0.0~223.255.255.255 |

<br /><br />

---

## <span style="background-color:aquamarine">LESSON 20. 네트워크 주소와 브로드캐스트 주소의 구조</span>

<span style="color:tomato">**컴퓨터에 할당할 수 없는**</span> IP 주소인 네트워크 주소와 브로드캐스트 주소에 대해 알아보자.

### 1) 네트워크 주소와 브로드캐스트 주소의 구조란?

IP 주소에는 네트워크 주소와 브로드캐스트 주소가 있다. <u>이 두 주소는 특별한 주소</u>로, **컴퓨터나 라우터가 자신의 IP로 사용하면 안 된다**

![](https://images.velog.io/images/april_5/post/fe329304-d864-4f96-9c11-019fd8ac8509/image.png)

✔️ **네트워크 주소**

- 전체 네트워크에서 <span style="color:Teal">**작은 네트워크를 식별**</span>하는데 사용된다
  - 호스트 ID가 10진수로 0이면 그 네트워크 전체를 대표하는 주소가 된다 ➔ 쉽게 말해 <u>전체 네트워크 대표 주소</u>

<br />

✔️ **브로드캐스트 주소**

- 네트워크에 있는 컴퓨터나 장비 모두에게 <span style="color:Teal">**한 번에 데이터를 전송**</span>하는데 사용되는 **전용 IP 주소**

<br /><br />

---

## <span style="background-color:aquamarine">LESSON 21. 서브넷(subnet)의 구조</span>

<u>네트워크를 분할하는 것</u>을 서브넷팅이라고 한다. 서브넷의 구조에 대해 알아보자.

### 1) 서브넷(subnet)이란?

IP 주소는 A, B, C, D, E 클래스로 나누어져 있고, 일반적으로 사용되는 IP 주소는 A, B, C로 나뉘어져 있다.

A 클래스 네트워크는 호스트 ID가 24비트로, 하나의 네트워크에 1677만 7214개의 IP 주소를 사용한다.

이 상태에서 <span style="color:Teal">**브로드캐스트 패킷을 전송**</span>하면 모든 컴퓨터에 패킷이 전송되고 네트워크가 혼잡해지게 되는데, 😱😱😱

![](https://images.velog.io/images/april_5/post/9b4e3bd4-b409-4d8f-b5d5-cf508562ab70/image.png)

A 클래스의 대규모 네트워크를 <u><span style="color:Teal">**작은 네트워크**</span>로 분할하여 브로드캐스트로 전송되는 패킷의 범위를 좁힐수 있다.</u>
➔ 이렇게 하면 더 많은 네트워크를 만들 수 있어서 IP 주소를 더 효과적으로 활용 할 수 있다.

이처럼 네트워크를 분할하는 것을 <span style="color:Teal">**서브넷팅(subneting)**</span>이라고 하고, 분할된 네트워크를 <span style="color:Teal">**서브넷(subnet)**</span>이라고 한다.

![](https://images.velog.io/images/april_5/post/8616b52a-554c-4f97-aa83-69fa9dd11ef6/image.png)

> 기존에 있던 호스트 ID에서 비트를 빌려 서브넷 ID로 바꿔 서브넷을 만든다.

<br />

### 1) 서브넷 마스크란?

IP 주소를 서브넷팅하면

- 어디까지가 네트워크 ID고 어디부터가 호스트 ID인지 판단하기가 어려울 때가 있는데 😥

이 때 **서브넷 마스크**라는 값을 사용한다.

> **서브넷 마스크**: 네트워크 ID와 호스트 ID를 식별하기 위한 값이다

<br /><br />

---

## <span style="background-color:aquamarine">LESSON 22. 라우터(router)의 구조</span>

<u>서로 다른 네트워크와 통신</u>하려면 라우터가 필요하다. 라우터에 대해 알아보자.

### 1) 라우터(router)란?

서로 다른 네트워크와 통신하려면 라우터가 필요하고, <u>라우터는 <span style="color:Teal">**네트워크를 분리**</span></u>할 수 있다

![](https://images.velog.io/images/april_5/post/bd201dcb-b578-4a47-b2d2-9b39a86678b6/image.png)

> 스위치(레이어 2 스위치)만 있는 네트워크에서는 모든 컴퓨터와 스위치가 동일한 네트워크에 속하게 되고, 허브도 스위치와 마찬가지로 네트워크를 분리할 수 없다 😥😥😥 <br /> ![](https://images.velog.io/images/april_5/post/bf133b91-9652-44ab-b5af-a2ca2c6e8563/image.png) <br /> ➔ 라우터가 있으면 네트워크를 분할할 수 있다

네트워크를 분할한 다음, 컴퓨터 한 대가 다른 네트워크로 접속하려면❓,

- 컴퓨터 1이 <span style="background-color:yellow">다른 네트워크에 데이터를 전송하려면 **라우터의 IP 주소를 설정**</span>해야 한다.
  - 이것은 네트워크의 출입구를 설정하는 것으로 <span style="color:Teal">**기본 게이트웨이(default gateway)**</span>라고 한다.

![](https://images.velog.io/images/april_5/post/0f93f105-3b04-46fc-aefc-40907a6e6355/image.png)

라우터의 IP 주소를 지정해야 하는 이유는,

- 컴퓨터 1은 다른 네트워크로 데이터를 보낼 때 어디로 전송해야 하는지 알지 못한다 😱
- 그래서 <span style="color:Teal">**네트워크의 출입구**</span>를 지정하고, <u>일단은 라우터로 데이터를 전송</u>한다
  - 컴퓨터 1은 `192.168.1.0/24` 네트워크에 속해 있기 때문에 라우터의 IP 주소인 `192.168.1.1`로 설정했다.
- 하지만 <span style="background-color:yellow">게이트웨이 설정만으로는 컴퓨터 1에서 컴퓨터 6으로 데이터를 보낼 수 없기 때문에 라우터의 <span style="color:Teal">**라우팅(routing)**</span>기능이 필요</span>하다

<br />

### 1) 라우팅(routing)이란?

<span style="color:Teal">**라우팅**</span>은
<u>경로 정보를 기반</u>으로 현재의 네트워크에서 다른 네트워크로 **최적의 경로를 통해 데이터를 전송**한다
이 경로 정보가 등록되어 있는 테이블이 <span style="color:Teal">**라우팅 테이블**</span>이다

![](https://images.velog.io/images/april_5/post/f8b03071-6478-40d2-8d7e-2a797bc0a9c0/image.png)

라우팅 테이블을 등록하는 방법은 네트워크 관리자가

(1) **수동으로 등록하는 방법**과

- 정보를 하나하나 라우터에 등록
- 등록된 내용이 수정되면 수동으로 변경해야 해서 작업량도 많아지기 때문에 <span style="background-color:yellow">소규모 네트워크에 적합</span>

(2) **자동으로 등록하는 방법**이 있다.

- 라우터 간에 경로 정보를 서로 교환하여 라우팅 테이블 정보를 자동으로 수정
- 수동으로 등록하는 방법처럼 직접 네트워크 관리자가 변경하지 않아도 되기 떄문에 훨씬 편하기 때문에 <span style="background-color:yellow">대규모 네트워크에 적합</span>

이처럼 <u>라우터 간에 라우팅 정보를 교환하기 위한 프로토콜</u>을 <span style="color:Teal">**라우팅 프로토콜**</span>이라고 한다.
대표적인 라우팅 프로토콜에는 RIP, OSPF, BGP 등이 있고 각각 다른 특징이 있다.

<br /><br />

---

### :: 용어 정리💡

- `네트워크 계층(network layer)`: 네트워크 계층은 다른 네트워크와 통신하기 위한 경로 설정을 위해 라우터를 통한 라우팅을 하며 패킷 전송을 담당한다

- `IP(Internet Protocol, 인터넷 프로토콜)`: 인터넷에 있는 한 컴퓨터에서 다른 컴퓨터로 데이터를 보내는 데 사용되는 네트워크 계층 프로토콜이다

- `IP 주소 클래스(IP address class)`: IPv4에서 사용하는 주소 그룹에는 다섯 개 가 있다. A, B, C클래스는 네트워크 ID와 호스트 ID로 구성되며, D 클래스는 멀티캐스트 주소로 사용된다. E 클래스는 필요에 따라 사용하기 위해 확보해 놓은 것이다

- `라우터(router)`: 서로 다른 네트워크를 연결해 주는 장치로 현재의 네트워크에서 다른 네트워크로 패킷을 전송할 수 있도록 한다

- `라우팅(routing)`: 네트워크에서 패킷을 목적지로 보낼 때 목적지까지 갈 수 있는 여러 가지 경로 중 한 가지 경로를 설정해 주는 과정이다

- `라우팅 테이블(rotuing table)`: 컴퓨터 네트워크에서 목적지 주소를 목적지에 도달하기 위한 네트워크 노선으로 변환시킬 목적으로 사용된다. 다른 네트워크로 가기 위한 가장 좋은 라우터의 정보를 가지고 있다

- `서브넷(subnet)`: 큰 네트워크를 분할해서 만든 작은 네트워크다

- `서브넷팅(subneting)`: 네트워크를 분할하기 위해 IP 주소의 구성을 변경하는 작업이다

- `서브넷 ID`: IP 주소의 네트워크 부분을 늘리기 위해 서브넷 마스크로 사용되는 비트로 서브넷 비트(subnet bits)라고도 한다

- `서브넷 마스크(subnet mask)`: IP 주소의 네트워크 부분만 나타나게 하여 같은 네트워크인지를 판별하게 하는 마스크다

- `멀티캐스트(multicast)`: 한 컴퓨터(호스트)에서 패킷을 여러 컴퓨터로 동시에 전송하는 것을 말한다

- `브로드캐스트(broadcast)`: IP 네트워크에 있는 모든 컴퓨터(호스트)로 데이터를 전송하는 방식이다
