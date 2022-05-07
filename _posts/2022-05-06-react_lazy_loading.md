---
published: true
title: "Intersection Observer API로 lazy loading의 무한 스크롤 구현하기!"
tags:
  - [React]
permalink: /study/react/lazy-loading

navigation: true
toc: true
toc_sticky: true

date: 2022-05-06
last_modified_at: 2022-05-06
---

![](https://velog.velcdn.com/images/april_5/post/b0fcefa7-0669-4a41-8dd1-c880ec2f1c4b/image.png)

`infinite scroll`에서 <span style='color:dodgerblue'>**`scroll`이 특정 포지션을 지나갈 때, 아이템을 추가로 로드**</span>하기 위해 필요한 `Intersection Observer API`.

---

## [Intersection_Observer_API](https://developer.mozilla.org/ko/docs/Web/API/Intersection_Observer_API) 공식문서

> `Intersection Observer`: 타겟 엘리먼트와, 타겟 엘리먼트의 부모나 뷰포트가 교차하는 부분의 변화를 비동기적으로 관찰하는 API이다.

공식문서에서 말하는,
`Intersection Observer API`는

- 타겟 요소와 상위 요소 또는 최상위 `document`에서의
- `viewport` 사이의 `intersection` 내의 변화를
- 비동기적으로 관찰하는 방법이다.

`Intersection Observer API`는

- 그들이 감시하고자 하는 요소가
- 다른 요소(viewport)에 들어가거나 나갈때 또는
- 요청한 부분 만큼 두 요소의 교차 부분이 변경될 때 마다
- 실행될 콜백 함수를 등록할 수 있게 한다.

<br />

### 🤔 왜 생겨났을까?

웹이 발전함에 따라 이러한 변화를 체크하는 것의 필요성이 높아졌고 그래서 나오게 된 API.

- 과거에는 `getBoundingClientRect()`로 실제 엘리먼트의 `offset`등을 측정하는 방식으로 이루어졌는데,
- <span style='color:tomato'>**가장 큰 문제점**</span>😱😱은 이러한 작업이 메인쓰레드에서 이루어진다는 점이다!
  - 들어오는 엘리먼트마다 체크해주는 작업을 해야하는데 이를 전부 메인쓰레드에서 진행한다.
- 한 페이지 `view` 안에 인터섹션을 확인해줘야 하는 요소가 있다고 생각했을 때, 성능상의 문제를 가져올 수 있다. 😱😱

<br />

### 🤔 언제 사용하는가?

- 페이지가 스크롤 되는 도중에 발생하는 이미지나 다른 컨텐츠의 지연 로딩.
- <span style='color:dodgerblue'>**스크롤 시에, 더 많은 컨텐츠가 로드 및 렌더링되어 사용자가 페이지를 이동하지 않아도 되게 하는 infinite-scroll 을 구현.**</span>
- 광고 수익을 계산하기 위한 용도로 광고의 가시성 보고.
- 사용자에게 결과가 표시되는 여부에 따라 작업이나 애니메이션을 수행할 지 여부를 결정.

<br />

### ✔️ 예제 코드

```js
function App() {
    const [inView, setInView] = useState(false);
	const observe = useRef(null);

	const handleObserver = useCallback(([entry], observer) => {
		if (entry.isIntersecting) {
			setInView(true);
		}
	}, []);

	useEffect(() => {
		let observer;
		if (observe) {
			observer = new IntersectionObserver(handleObserver, { threshold: 0 });
			observer?.observe(observe);
		}

		return () => observer?.disconnect();
	}, [observe, inView, handleObserver]);

// ...

  return (
      ...
      <div ref={observe} />
  );
}
```

<br />

---

## [`react-cool-inview`](https://www.npmjs.com/package/react-cool-inview)

> 라이브러리로 좀 더 깔끔하고 쉽게.. 적용해보기!

<br />

### ✔️ 설치

```bash
yarn add react-cool-inview
# or
npm install --save react-cool-inview
```

<br />

### 예제 코드

```jsx
import useInView from "react-cool-inview";

const App = () => {
  const { observe, unobserve, inView, scrollDirection, entry } = useInView({
    threshold: 0.25, // Default is 0
    onChange: ({ inView, scrollDirection, entry, observe, unobserve }) => {
      // Triggered whenever the target meets a threshold, e.g. [0.25, 0.5, ...]

      unobserve(); // To stop observing the current target element
      observe(); // To re-start observing the current target element
    },
    onEnter: ({ scrollDirection, entry, observe, unobserve }) => {
      // Triggered when the target enters the viewport
    },
    onLeave: ({ scrollDirection, entry, observe, unobserve }) => {
      // Triggered when the target leaves the viewport
    },
    // More useful options...
  });

  return <div ref={observe}>{inView ? "Hello, I am 🤗" : "Bye, I am 😴"}</div>;
};
```

<br />

### 실제 코드

```jsx
import useInView from "react-cool-inview";

const App = () => {
  const { observe, inView } = useInView({
    onEnter: ({ unobserve }) => unobserve(),
  });

  return <div ref={observe}>{inView ? "Hello, I am 🤗" : "Bye, I am 😴"}</div>;
};
```

<br />
