---
published: true
title: "Next.js + Typescript 프로젝트 생성하기(1)"
tags:
  - [NextJs]
permalink: /study/nextjs/create-project

navigation: true
toc: true
toc_sticky: true

date: 2022-05-08
last_modified_at: 2022-05-08
---

![](https://velog.velcdn.com/images/april_5/post/48015068-4591-4135-80d0-9df2587dda6d/image.png)

[Github web-template](https://github.com/yurim45/web-template)

> Next.js + Typescript web template 만들기

---

![](https://images.velog.io/images/april_5/post/ed0c0e6c-1e8d-4b42-bae5-fa9dc7431082/image.png)

# 프로젝트 생성

### ✔️ Why Next.js

- Next.js는 React 기반 Framework이다
- 폴더 및 파일 기반 Routing 지원하고
- Server Side Rendering 을 지원한다
  - 즉, SEO 적용이 수월하다

[SSR과 CSR의 차이](https://velog.io/@april_5/SSR%EA%B3%BC-CSR%EC%9D%98-%EC%B0%A8%EC%9D%B4)

> 📌 **참고** next.js를 통해 보는 SSR Cycle
> 페이지 요청이 오면 수행하는 순서가 다음과 같다 <br />

1. `Frontend Server`에서 `GET` 요청을 받는다
2. 요청에 맞는 `page`를 찾는다
3. `_app.tsx`(next.js 사용시 최초로 실행되는 파일)의 `getInitialProps`가 있다면 실행
4. `Page Component` 안에 `getInitialProps`가 있다면 실행
5. `_document.tsx`의 `getInitialProps`가 있다면 실행
6. 모든 `props`를 구성하고 `_app.tsx` > `Page Component` 순으로 렌더링
7. 모든 콘텐츠를 구성하고 `_document.tsx`를 실행하여 `html`형태로 출력

<br />

---

## 1️⃣ 프로젝트 생성하기

### ✔️ [공식문서](https://nextjs.org/docs/basic-features/typescript)에 따라서 설치하기

```bash
npx create-next-app@latest --ts
# or
yarn create next-app --typescript
```

![](https://images.velog.io/images/april_5/post/d273de4b-4e82-4441-b958-3ac195eae63d/image.png)

💬 열심히 설치 중..

![](https://images.velog.io/images/april_5/post/366ad0a1-58b1-42ed-ba97-545dc4a8b969/image.png)

💬 성공!!! http://localhost:3000

```bash
npm run dev
# 자동 리프레시 가능
```

![](https://images.velog.io/images/april_5/post/36027f63-089a-4315-8757-4218d9e046f3/image.png)

> 📌 **참고!!** <br /> create-next-app 으로 설치하면 <br /> 1. 컴파일과 번들링이 자동으로 된다(webpack 과 barbel) <br /> 2. 자동 리프레시 기능으로, 수정 시 화면에 바로 반영된다 <br /> 3. 서버사이드 렌더링(Server Side Rendering)이 지원된다 <br /> 4. [Static File](https://nextjs.org/docs/basic-features/static-file-serving) 을 지원한다

<br />

---

## 2️⃣ routing 기능 알아보기

### ✔️ 기본 라우팅 기능

- pages 폴더 안에 페이지를 만들면 별도의 라우팅 처리를 하지 않아도 routing 기능이 제공된다

![](https://images.velog.io/images/april_5/post/dbafa109-9730-457b-8a43-8055e5ad8b7b/image.png)

<br />

### ✔️ Dynamic routing 기능

- [Dynamic routing](https://nextjs.org/docs/routing/dynamic-routes) 기능도 제공된다

![](https://images.velog.io/images/april_5/post/9f1e6a83-f9b7-4a69-b8b3-5b12387f5868/image.png)

<br />

---

# Style: Semantic UI React 적용

![](https://images.velog.io/images/april_5/post/3db2bfee-801c-49e7-a3af-a785e2ef2630/image.png)

## 1️⃣ Semantic UI React 설치

![](https://images.velog.io/images/april_5/post/3eea71d6-01d0-408f-b851-c62fce15ad4b/image.png)

```bash
npm install semantic-ui-react semantic-ui-css
# or
yarn add semantic-ui-react semantic-ui-css
```

```tsx
// _app.tsx
import "semantic-ui-css/semantic.min.css";
```

- 모든 페이지는 \_app.tsx 을 통한다

> 📌 **참고!!** <br /> \_app.tsx 을 이용하면 <br /> 1. 페이지 전환 시 레이아웃을 유지할 수 있다 <br /> 2. 페이지 전환 시 상태값을 유지할 수 있다 <br /> 3. componentDidCatch를 이용해서 커스텀 에러 핸들링을 할 수 있다 <br /> 4. 추가적인 데이터를 페이지로 주입시키는 것이 가능하다 <br /> 5. 글로벌 CSS를 이곳에 선언한다

<br />

---

📌 참고로 \_app.tsx 를 좀 더 설명하자면,

- `Component`: 현재 페이지를 의미
  - 페이지 전환 시에 이 Component Props가 변경된다
- `pageProps`: 데이터 패칭 메서드를 통해 미리 가져온 초기 객체
  - 이 메서드를 사용하지 않는다면 빈 객체가 전달되고 SSR 시

```tsx
function MyApp({ Component, pageProps }: AppProps) {
  // Props로 넘어온 Component는 현재 페이지를 의미.
  // 페이지 전환 시에 이 Component Props가 변경된다
  // pageProps는 데이터 패칭 메서드를 통해 미리 가져온 초기 객체.
  // 이 메서드를 사용하지 않는다면 빈 객체가 전달되고 SSR 시
  return <Component {...pageProps} />;
}

export default MyApp;
```

---

### ✔️ Semantic UI React 사용하기

![](https://images.velog.io/images/april_5/post/3bfed618-9f36-4571-960b-21f14105b265/image.png)

- Semantic UI React의 [공식문서](https://react.semantic-ui.com/elements/header/#types-users-icon) 참고해서 적용해보기!!👍👍

![](https://images.velog.io/images/april_5/post/d8745bdc-d93a-4393-877e-d9f172c4d22d/image.png)
