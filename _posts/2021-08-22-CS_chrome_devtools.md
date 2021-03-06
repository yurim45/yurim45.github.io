---
title: "💡Chrome DevTools"
tags:
  - [CS]
permalink: /CS/chrome_dev_tools

navigation: true
toc: true
toc_sticky: true

date: 2021-08-22
last_modified_at: 2021-08-22
---

![]()

`주니어 개발자의 개인 공부 과정을 기록합니다.`

현업에 나가 일을 해 보니 생각보다 많이 사용하는 <span style="color:dodgerblue">**크롬 개발자 도구**</span>..
1주차에 배웠던 개발자 도구인데.. 놓치고 있는 건 없는지 다시 정리해본다.

---

# 개발자 도구란?

- 크롬, 사파리 등 브라우저마다 제공하는 개발을 위한 도구(tool) 이다
- <span style="background-color:#ffff99">**웹 사이트 디버깅**</span>을 빠르게 할 수 있도록 도와준다.

  > **디버깅**이란, 문제를 캐치하고 문제의 원인을 파악하여 수정하는 것을 말한다.

- 프론트엔드 개발을 할 때 개발자 도구를 많이 사용한다.

맥에서는 `옵션+커맨드+i`를 누르고, 윈도우에서는 `F12`를 누른다.
아니면 `마우스 오른쪽 버튼` 눌러서 `검사`를 눌러줘도 확인할 수 있다.

<br />

---

## 개발자 도구의 다양한 패널

개발자 도구에는 다양한 기능 들이 있는데

1. `Elements` 패널: 웹 페이지 구성과 구성 요소들의 스타일을 확인
2. `Console` 패널: 자바스크립트 코드를 브라우저에서 즉시 실행
3. `Network` 패널: 네트워크 상으로 주고 받는 데이터를 확인
4. `Application` 패널: 브라우저의 저장소에 담긴 데이터를 확인

가 가장 자주 사용되는 패널들이다.

---

### `Elements` panel

- `Elements` 패널의 기능은?

  - 페이지의 스타일의 검사 및 편집

    - Select Element 버튼 클릭하면 원하는 요소를 바로 찾을 수 있다.
      ![](https://images.velog.io/images/april_5/post/55a8df6f-8caf-414a-9574-80fb7b32a969/%E1%84%8B%E1%85%AD%E1%84%89%E1%85%A9%20%E1%84%89%E1%85%A5%E1%86%AB%E1%84%90%E1%85%A2%E1%86%A8.png)

    - 요소에 적용된 CSS 효과를 바로 확인할 수 있다. 스타일은 실시간으로 수정할 수 있지만 저장이 되는 것은 아니다.
      ![](https://images.velog.io/images/april_5/post/097982a0-9a3d-4d27-9454-57eca310671e/%E1%84%80%E1%85%A2%E1%84%87%E1%85%A1%E1%86%AF%E1%84%8C%E1%85%A1%20%E1%84%83%E1%85%A9%E1%84%80%E1%85%AE%20%E1%84%89%E1%85%B3%E1%84%90%E1%85%A1%E1%84%8B%E1%85%B5%E1%86%AF%20%E1%84%87%E1%85%A7%E1%86%AB%E1%84%80%E1%85%A7%E1%86%BC.gif)
    - 요소의 박스 모델도 확인할 수 있다.
      ![](https://images.velog.io/images/april_5/post/0642a432-3b23-4e45-9e98-cb05e6030b8a/%E1%84%80%E1%85%A2%E1%84%87%E1%85%A1%E1%86%AF%E1%84%8C%E1%85%A1%20%E1%84%83%E1%85%A9%E1%84%80%E1%85%AE%20%E1%84%87%E1%85%A1%E1%86%A8%E1%84%89%E1%85%B3%E1%84%86%E1%85%A9%E1%84%83%E1%85%A6%E1%86%AF.gif)

- Styles 부분의 순서가 의미하는 것은?

  - 적용되는 CSS 우선 순위를 의미한다.
  - 스타일 속성이 밑줄 표시로 그어진 스타일들은 속성을 적용했지만 중복된다면 우선 순위에 따라 스타일이 적용되므로 반영되지 않는 스타일 속성이다.

- `user agent stylesheet` 란?
  - 웹브라우저별 스타일의 기본 속성값.
  - 이렇게 되면 내가 원하는 모습의 형태가 완성되지 않을 수 있으므로 개발 시작 단계에서 'reset.css' 파일에서 브라우저의 기본 스타일 값을 모두 초기화 시키기 때문에 브라우저 종류에 상관없이 동일하게 화면이 출력되므로 꼭 작업해주는 것이 좋다.

---

### `Console` panel

- `Console` 패널의 기능은?

  - console에서는 자바스크립트 코드가 즉시 실행이 가능하다.
  - 디버깅이 가능하다.

- 화면을 새로고침 해도 `console` 내용이 지워지지 않고 남게 하는 방법은?
  - 톱니바퀴 아이콘을 클릭
    - (1) 상단 오른쪽 톱니 바퀴 클릭 - 하단 오른쪽 톱니 바퀴를 눌러서 Preserve log upon navigation 체크
    - 또는 (2) 하단 오른쪽 톱니 바퀴 클릭 - Preserve log 체크
- 콘솔에 기록된 로그를 모두 지울 때 사용하는 메소드는?

  - console도 객체! object! 이기 때문에 메소드 사용이 가능하다. `clear()` 메소드를 사용해서 코드를 삭제할 수 있다.

- 다른 패널(ex. Elements panel)에서 Console Panel 같이 보는 방법은?
  - 개발자 도구를 연 상태에서 `esc`를 누르면 된다.

---

### `Network` panel

- `Network` 패널의 기능은?
  - 네트워크 통신을 모니터링 한다.
  - 클라이언트와 서버 사이에서의 데이터 통신을 일목요연하게 파악하고 분석할 수 있게 도와준다.
- `Network` 패널을 간단히 살펴보자.
  ![](https://images.velog.io/images/april_5/post/ffa4346d-fa5d-488a-a51d-a3f1fa58d802/%E1%84%82%E1%85%A6%E1%84%90%E1%85%B3%E1%84%8B%E1%85%AF%E1%84%8F%E1%85%B3.gif)

  > 개인적으로 fetch를 통해 받은 response, data 등을 콘솔을 통해 확인했었는데, 네트워크 패널에서도 확인 가능하다. ![](https://images.velog.io/images/april_5/post/495a60cc-e0fc-4ece-9352-e4f05da72c75/%E1%84%82%E1%85%A6%E1%84%90%E1%85%B3%E1%84%8B%E1%85%AF%E1%84%8F%E1%85%B3.png)

---

### `Application` panel

- `Application` 패널의 기능은?
  ![](https://images.velog.io/images/april_5/post/379c0e4c-af7a-4b7d-b4d6-fc6b37101ad1/%E1%84%80%E1%85%A2%E1%84%87%E1%85%A1%E1%86%AF%E1%84%8C%E1%85%A1%20%E1%84%83%E1%85%A9%E1%84%80%E1%85%AE%20%E1%84%8B%E1%85%A5%E1%84%91%E1%85%B3%E1%86%AF%E1%84%85%E1%85%B5%E1%84%8F%E1%85%A6%E1%84%8B%E1%85%B5%E1%84%89%E1%85%A7%E1%86%AB.png)

- `Local Storage`, `Session Storage`, `Cookie` 차이점은?

> **Storage**: 데이터를 브라우저 상에서 저장하기 위한 기술•공간. 데이터가 어떤 범위 내에서 얼마나 오래 보관할지에 따라 `Local Storage` 또는 `Session Storage`에 저장한다

- `web Storage`는 `Cookie`의 단점을 보완하기 위해 HTML5에서 탄생한 기술이다. `web Storage`에는 `Local Storage`, `Session Storage`가 있다.

| 종류              | 기능                                                                                                                                                   |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `Local Storage`   | 탭이나 창을 닫아도 브라우저에 데이터가 남아있다. 유효 기한이 없고, 필요할 때 언제든 사용 가능. key와 value로 셋트로 저장. 예시) 자동 로그인 등         |
| `Session Storage` | 브라우저가 닫히면 정보가 만료된다.(데이터가 삭제됨). refresh token 이용시 session에서 token 정보 유지 가능. 예시) 입력 폼 정보, 비로그인 장바구니 기능 |
| `Cookie`          | 서버 접속 시 자동 송신. 서버와 로컬에 정보 저장                                                                                                        |

- `Local Storage` 에 특정 데이터를 저장하고 가져오는 방법

![](https://images.velog.io/images/april_5/post/d63d2f55-f1a8-4604-a395-8b83990d8b2e/image.png)

![](https://images.velog.io/images/april_5/post/743d1af9-6a57-4c58-8db7-e38e84775187/image.png)
