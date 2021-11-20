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

>① 데이터가 제대로 도착했는지 확인  <br />
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
① 데이터가 제대로 도착했는지 확인 <br />
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

전송 계층의 연결형 통신 프로토콜에는 <span style="background-color:yellow">TCP</span>가 사용되고, 비연결형 통신 프로토콜에는 <span style="background-color:yellow">UDP</span>가 사용된다

<br />

---

## <span style="background-color:aquamarine">LESSON 24. TCP의 구조</span>

### 1) TCP(Transmission Control Protocol, 전송 제어 프로토콜)란?

**TCP**: 전송 계층에서 <u>신뢰할 수 있는 정확한 통신을 제공</u>하는,  <span style="color:Teal">**신뢰성/정확성**</span>이 우선인 **연결형 통신 프로토콜**인 <span style="color:Teal">**TCP**</span>

![](https://images.velog.io/images/april_5/post/72461312-7b0f-4d05-a8ab-89c55da1f793/image.png)

- **세그먼트(segment)**: TCP 헤더가 붙은 데이터

- **TCP 헤더**: TCP로 전송할 때 붙히는 헤더. <u>목적지까지 데이터를 제대로 전송하기 위해 필요한 정보</u>가 있다

![](https://images.velog.io/images/april_5/post/5441b02c-56f9-49c3-9f77-dd0cb1b72939/image.png)

데이터를 전송하기 전에 <span style="background-color:yellow">연결(connection)</span>이라는 <span style="color:Teal">**가상의 독점 통신로**</span> 확보 작업을 해야하는데, 이 연결을 확립한 후 데이터를 전송할 수 있다

>**연결(connection)**: TCP 통신에서 정보를 전달하기 위해 사용되는 가장의 통신로로, 연결을 확립하고 데이터를 전송한다

TCP 헤더에는 <span style="color:Teal">**코드 비트**</span>라는 부분이 있는데, 코드 비트는 TCP 헤더의 <u>연결 제어 정보가 기록되는 곳</u>이다

초기값은 <span style="color:Teal">**0**</span>이고, 연결을 확립하려면 <span style="color:Teal">**SYN(연결 요청)**</span>과 <span style="color:Teal">**ACK(확인 응답)**</span>가 필요하다

![](https://images.velog.io/images/april_5/post/09a200cf-9d36-449d-a250-fa1bcf5f2387/image.png)

<br />

### 2) 3-way 핸드셰이크(three-way handshake)란?

<span style="background-color:yellow">연결(connection)</span>은 <span style="color:Teal">**SYN(연결 요청)**</span>과 <span style="color:Teal">**ACK(확인 응답)**</span>를 사용하여 확립 할 수 있고 
신뢰할 수 있는 연결을 하려면 데이터를 전송하기 전에 패킷 교환을 세 번(three-way handshake) 확인 한다

><span style="color:Teal">**3-WAY 핸드셰이크(three-way handshake)**</span>: 데이터를 보내기 전에 연결을 확립하기 위해 패킷 요청을 세번 교환하는 것을 의미. <br /> **핸드셰이크**는 사람들이 상대방을 확인하고 악수를 하는 것처럼 <u>데이터 통신에서도 확실하게 데이터가 전송되었는지 확인하면서 이루어지는 통신 수단</u>이다.

![](https://images.velog.io/images/april_5/post/4c4f039f-64a0-4088-91f2-2caa4aa64adf/3-way%20%E1%84%92%E1%85%A2%E1%86%AB%E1%84%83%E1%85%B3%E1%84%89%E1%85%A8%E1%84%8B%E1%85%B5%E1%84%8F%E1%85%B3.jpeg)

① 통신을 하려면 서버에게 허가를 받아야 하므로, 먼저 클라이언트에서 서버로 연결 확립 허가를 받기 위한 요청(SYN)을 보낸다. <br />
② 서버는 클라이언트가 보낸 요청을 받은 후에 허가한다는 응답을 회신하기 위해 연결 확립 응답(ACK)을 보낸다. 동시에 서버도 클라이언트에게 데이터 전송 허가를 받기 위해 연결 확립 요청(SYN)를 보낸다. <br />
③ 서버의 요청을 받은 클라이언트는 서버로 허가한다는 응답으로 연결 확립 응답(ACK)를 보낸다.


<br /><br />

데이터를 전송할 때뿐만 아니라 전송한 후에도 <u>연결을 끊기 위한 요청</u>을 교환해야 한다. 
연결을 끊을 때는 <span style="color:Teal">**FIN(연결 종료)**</span>과 <span style="color:Teal">**ACK(확인 응답)**</span>를 사용한다



![](https://images.velog.io/images/april_5/post/3cfa9f72-7464-44d0-a44b-4d88ea13f5e6/image.png)

① 컴퓨터 1에서 컴퓨터 2로 연결 종료 요청(FIN)을 보낸다. <br />
② 컴퓨터 2에서 컴퓨터 1로 연결 종료 응답(ACK)를 반환한다. <br />
③ 또한 컴퓨터 2에서도 컴퓨터 1로 연결 종료 요청(FIN)을 보낸다. <br />
④ 컴퓨터 1에서 컴퓨터 2로 연결 종료 응답(ACK)을 반환한다. <br />

<br />

---

## <span style="background-color:aquamarine">LESSON 25. 일련번호와 확인 응답 번호의 구조</span>

### 1) 일련번호와 확인 응답 번호란?

3-way 핸드셰이크가 끝나고 <u>실제 데이터를 보내거나 상대방이 받을 때</u>는 
**TCP 헤더**의 <span style="color:Teal">**일련 번호(sequence number)**</span>와 <span style="color:Teal">**확인 응답 번호(acknowledgement number)**</span>를 사용한다.

![](https://images.velog.io/images/april_5/post/eaf3003a-5bc8-4353-88bf-3b3b95a8c961/image.png)

<span style="color:Teal">**TCP**</span>는 데이터를 분할해서 보내는데 
- <span style="color:Teal">**일련번호**</span>는 송신 측에서 **수신 측에** <u>*이 데이터가 몇 번째 데이터인지*</u> 알려 주는 역할을 한다. 
  - 전송된 데이터에 일련번호를 부여하면 수신자는 원래 데이터의 몇 번째 데이터를 받았는지 알 수 있다.

- <span style="color:Teal">**확인 응답 번호**</span>는 수신 측이 <u>*몇 번째 데이터를 수신했는지*</u> **송신 측에** 알려주는 역할을 한다. 
  - 그래서 이 번호는 다음 번호의 데이터를 요청하는데도 사용한다. 


<br />

데이터가 항상 올바르게 전달되는 것은 아니므로
<u>일련번호와 확인 응답 번호를 사용해서 데이터가 손상되거나 유실된 경우에 데이터를 재전송</u>하게 되어있다. 이것을 <span style="color:Teal">**재전송 제어**</span>라고 한다.

<br />

### 1) 윈도우 크기란?

>**윈도우 크기**: 버퍼(상대방에게 쌓인 세그먼트를 일시적으로 보관하는 장소) 용량의 크기

**TCP의 특징**은 <span style="color:Teal">**세그먼트(데이터)**</span> <u>하나를 보낼 때마다 확인 응답을 한 번 반환</u>하는 통신인데, 한 번 보낼 때마다 한 번 응답을 반환하는 방식이어서 <u>효율이 낮다</u>

하지만, 매번 확인 응답을 기다리는 대신 <u>세그먼트를 연속해서 보내고 난 다음에 확인 응답을 반환하면 효율이 높아지</u>지만 상대방에는 세그먼트가 점점 쌓이게 된다. 
상대방에게 쌓인 세그먼트는 <span style="color:Teal">**버퍼(buffer)**</span>라는 장소에 일시적으로 보관한다.
- 버퍼(buffer) 덕분에 세그먼트를 연속해서 보내도 수신 측은 대응할 수 있고 효율도 높아진다
- 하지만 수신 측은 대량으로 데이터가 전송되면 보관하지 못하고 넘쳐 버리는 경우를 <span style="color:Teal">**오버플로(overflow)**</span>라고 한다.

오버플로가 발생하지 않도록 <span style="color:Teal">**버퍼의 한계 크기**</span>를 알고 있어야 한다. 그것이 **TCP 헤더**의 <span style="color:Teal">**윈도우 크기(window size)**</span> 값에 해당한다.

![](https://images.velog.io/images/april_5/post/8cf4d509-af79-49fb-bac5-d85e7c705b1d/image.png)

>**윈도우 크기**: <span style="color:Teal">**얼마나 많은 용량의 데이터를 저장해 둘 수 있는지**</span>를 나타낸다. 즉, 확인 응답을 일일이 하지 않고 연속해서 송수신할 수 있는 데이터 크기다.


<br />

---

## <span style="background-color:aquamarine">LESSON 26. 포트 번호(port number)의 구조</span>

### 1) 포트 번호(port number)란?

>**포트 번호**: 어떤 애플리케이션인지 구분하는 역할

![](https://images.velog.io/images/april_5/post/4ed21bea-2be9-4c64-8ae1-c2a42dcc0ab6/image.png)

전송 계층의 역할 중 전송된 데이터의 목적지가 어떤 애플리케이션(웹 브라우저나 메일 프로그램 등)인지 구분하는 역할을 하기 위해선 
**TCP 헤더**의 <span style="color:Teal">**출발지 포트 주소**</span>(source port number)와 <span style="color:Teal">**목적지 포트 주소**</span>(destination port number)가 필요하다. TCP 헤더에 포트 번호가 있기 때문에 애플리케이션을 구분할 수 있게 된다.

포트 번호는 `0 ~ 65535번` 까지 사용할 수 있고, 크게 세 종류로 구분된다.

|포트 종류|범위|설명|
|--|--|--|
|잘 알려진 포트 (well-known port)|0번 ~ 1023번|주요 프로토콜이 사용하도록 예약되어 있음 <br /> 일반적으로 서버 측 애플리케이션에서 사용|
|등록된 포트 (registered port)|1024번 ~ 49151번|- 1024번: 예약되어 있지만 사용되지는 않는 포트 <br /> - 1025 이상: 랜덤 포트라고 하고 클라이언트 측의 송신 포트로 사용|
|동적 포트 (dynamic port)|49152번 ~ 65535번|

![](https://images.velog.io/images/april_5/post/95114df5-0776-41ec-93f1-fec0a936a0c5/image.png)

|애플리케이션| 포트 번호|
|--|--|
|SSH|	22|
|SMTP|	25|
|DNS|	53|
|HTTP|	80|
|POP3|	110|
|HTTPS	|443|


이처럼 동작하는 애플리케이션은 각각 포트 번호가 있어서 다른 애플리케이션과 서로 구분된다. 
<u>데이터를 전송할 때는 상대방의 **IP 주소**가 필요</u>하지만, 
<u>어떤 애플리케이션이 사용되고 있는지 구분하려면 **TCP는 포트 번호**</u>가 필요하다.

<br />

---

## <span style="background-color:aquamarine">LESSON 27. UDP(User Datagram Protocol)의 구조</span>

### 1) UDP(User Datagram Protocol)란?

>**UDP**: 사용자 다이어그램 프로토콜. 전송 계층에서 데이터를 효율적이고 빠르게 보낼 때 사용되는 프로토콜

UDP는 <span style="color:Teal">**비연결형 통신**</span>이라서 데이터를 전송할 때 TCP처럼 시간이 걸리는 확인 작업을 일일이 하지 않는다. 

UDP는 TCP와 달리 <span style="color:Teal">**효율성</span>을 중요하게 여기는 프로토콜** 이라 TCP와 같은 신뢰성과 정확성을 요구하게 되면 효율이 떨어진다.

**UDP의 장점**은 <u>데이터를 효율적으로 빠르게 보내는 것</u>이라서 스트리밍 방식으로 전송하는 동영상 서비스와 같은 곳에 사용된다. 
- 동영상을 TCP 데이터 통신으로 전송하면 수신을 확인하는데 시간이 너무 오래 걸려서 동영상을 원할하게 볼 수 없다. 그래서 동영상 같은 건 대개 빠른 UDP를 사용한다.


<br />

### 2) UDP 헤더란?

UDP 에서는 <span style="color:Teal">**UDP 헤더**</span>가 붙은 데이터를 <span style="color:Teal">**UDP 데이터 그램**</span>이라고 한다.


![](https://images.velog.io/images/april_5/post/4b991034-4eb5-4da1-ad5c-f827fc1276c8/image.png)

- TCP와 UDP 차이

![](https://images.velog.io/images/april_5/post/287837cf-4eb8-49ba-a71d-daa59c24a3e7/image.png)

- TCP는 번거롭게 여러 번 확인 응답을 보내면서 전송하지만, 
- UDP는 효율성과 빠른 속도가 중요해서 상대방을 확인하지 않고 연속해도 데이터를 보낸다. 
  - 또한 UDP를 사용하면 <u>랜에 있는 컴퓨터나 네트워크 장비에 데이터를 일괄로 보낼 수 있다</u>. 이것을 <span style="color:Teal">**브로드캐스트**</span>라고 한다.

![](https://images.velog.io/images/april_5/post/4aafe7bb-8937-468f-aa02-46fe083d4347/image.png)

<br /><br />

---

### :: 용어 정리💡

- `전송 계층(transport layer, 트랜스포트 계층)`: 신뢰할 수 있는 데이터를 순차적으로 전달하는 역할을 하므로 상위 계층들이 데이터 전달의 유효성이나 효율성을 신경 쓰지 않도록 한다. 데이터가 중복되거나 누락되지 않고 오류 없이 순서에 맞게 전송되도록 관리한다.

- `연결형(connection-oriented)`: 데이터를 교환하기 전에 연결을 맺고 데이터를 교환하는 동안 계속 연결을 관리하는 프로토콜의 한 형태다.

- `비연결형(connectionless)`: 연결(connection)에 대한 초기화 과정이 없는 통신이다.

- `TCP(Transmission Control Protocol, 전송 제어 프로토콜)`: 전송 계층의 프로토콜은 연결형(connection-oriented) 통신 방식이며 신뢰할 수 있는 데이터 전송을 보장한다.

- `대역폭(bandwidth)`: 정해진 시간 동안 전송될 수 있는 데이터의 양(주로 속도를 의미한다)을 말한다. 대역폭은 제한적이다.

- `UDP(User Datagram Protocol)`: 정보를 서로 주고받을 때 보내는 쪽에서 일방적으로 데이터를 전달하는 통신 프로토콜이다. 연결을 맺을 필요가 없고 정보를 보내거나 받는다는 신호도 필요하지 않다.

- `3-way 핸드셰이트(three-way handshake)`: TCP 통신에서 사용하는 신뢰성을 제공하기 위한 통신 방식이다. 컴퓨터 간에 연결을 맺기 위한 초기화 과정으로 세 단계로 되어 있어서 three-way라고 부른다.

- `잘 알려진 포트(well-known ports)`: 특정 애플리케이션이 사용할 수 있도록 예약되어 있는 포트로 1~1023번 포트를 말한다.

- `브로드캐스트(broadcast)`: 네트워크의 모든 컴퓨터와 장비에 같은 패킷을 일괄 전송하는 방식이다.

- `일련번호(sequence number)`: TCP에서는 데이터를 보낼 때마다 각 데이터에 고유한 번호를 부여해서 전송을 시도한다. 이 번호를 이용하여 TCP 패킷의 순서를 제어할 수 있다.

- `포트 번호(port number)`: 컴퓨터가 데이터 통신을 할 때 통하고자 하는 네트워크 서비스나 특정 프로세스를 식별하는 노리 단위다. 포트 번호는 0~65535번을 사용할 수 있다. 0~1023번은 잘 알려진 포트(well-known ports)로 특정 애플리케이션이 사용할 수 있도록 예약된 번호다.





