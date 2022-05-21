---
published: true
title: "Next.js with-styled-components (2)"
tags:
  - [NextJs]
permalink: /study/nextjs/with-styled-components

navigation: true
toc: true
toc_sticky: true

date: 2022-05-21
last_modified_at: 2022-05-21
---

![](https://velog.velcdn.com/images/april_5/post/0f369ede-c857-43b6-a8e7-e0faaed96d53/image.png)

[Github web-template](https://github.com/yurim45/web-template)

> [공식문서](https://github.com/vercel/next.js/tree/master/examples/with-styled-components)로 `css-in-js` 방식인 `styled-component`를 적용하기

# with-styled-components

## 1️⃣ `_documents.tsx` 설정

`_documents.tsx` 파일은

- Next.js 에서 제공하는 document를 커스터마이징 할 수 있다
- Next.js 페이지들은 마크업 정의를 건너뛰기 때문에 `<html>`, `<body>`, `<head>` 등을 필수적으로 작업해야 할 때는 `_documents.tsx` 파일을 필수적으로 사용해야 한다

  - 예시) `<Html lang='kr'>`

- SSR시에 실행되는 파일인 `_documents.tsx`에
  `styled-components`의 스타일 코드를 추출하는 로직을 추가한다
  - [공식문서](https://github.com/vercel/next.js/tree/master/examples/with-styled-components)를 참고해서 아래와 같이 `getInitialProps method`를 작성

```tsx
// pages/_documents.tsx

import React from "react";
import Document, {
  DocumentContext,
  Html,
  Head,
  Main,
  NextScript,
} from "next/document";
import { ServerStyleSheet } from "styled-components";

export default class MyDocument extends Document {
  static async getInitialProps(ctx: DocumentContext) {
    const sheet = new ServerStyleSheet();
    const originalRenderPage = ctx.renderPage;

    try {
      ctx.renderPage = () =>
        originalRenderPage({
          enhanceApp: (App) => (props) =>
            sheet.collectStyles(<App {...props} />),
        });

      const initialProps = await Document.getInitialProps(ctx);
      return {
        ...initialProps,
        styles: (
          <>
            {initialProps.styles}
            {sheet.getStyleElement()}
          </>
        ),
      };
    } finally {
      sheet.seal();
    }
  }

  render() {
    return (
      <Html lang='kr'>
        <Head />
        <body>
          <Main />
          <NextScript />
        </body>
      </Html>
    );
  }
}
```

<br />

---

## 2️⃣ styled-components 설치

```bash
npm i styled-components @types/styled-components
npm install styled-reset
npm i --save-dev @types/styled-components
// or
yarn add typescript-plugin-styled-components
yarn add @types/styled-components
```

![](https://images.velog.io/images/april_5/post/f19365d2-7862-4966-883b-bcdeb97cd31b/image.png)

<br />

---

## 3️⃣ babel 설정

Next.js는 최초 SSR 이후 내부 라우팅을 통해 페이지가 이동되면서 CSR을 하게되는데
이때, 서버에서 생성하는 해시값과 브라우저에서 생성하는 해시값이 서로 달라서 문제가 발생하게 된다.

> <Prop className did not match. 에러 발생 >

styled-components를 사용하다 보면 문자열 안에 스타일이 들어가기 때문에 처리를 위해 별도로 babel이 필요하다.

이러한 점으로 인해 `babel-plugin 패키지`를 설치

```bash
npm install --save-dev babel-plugin-styled-components
```

그리고 `root`에 `.babelrc` 파일을 생성

```tsx
{
  "presets": ["next/babel"],
  "plugins": [["styled-components", { "ssr": true }]]
}
```

<br />

[Github web-template](https://github.com/yurim45/web-template)
