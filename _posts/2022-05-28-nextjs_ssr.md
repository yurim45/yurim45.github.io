---
published: true
title: "서버사이드 렌더링(Server-side Rendering/SSR)(4)"
tags:
  - [NextJs]
permalink: /study/nextjs/ssr

navigation: true
toc: true
toc_sticky: true

date: 2022-05-28
last_modified_at: 2022-05-28
---

# 서버사이드 렌더링 SSR

## ✔️ 사전 렌더링(pre-rendering)이란?

Next.js는 모든 페이지를 사전 렌더링(pre-rendering)을 하는데

- 더 좋은 퍼포먼스를 내고
- 검색엔진최적화(SEO)에도 효율적이다.
  - **SEO**: Search Engine Optimization의 약자로 검색 엔진 최적화를 의미한다.
    메타 태그를 이용해 `description`, `keywords`, `author`, `subject`, `classification` 등의 정보를 표기할 수 있으며, 검색엔진은 이런 정보를 적극적으로 활용한다.

> **pre-rendering**: 미리 HTML들을 만들어 두는 것?!

<br />

---

## ✔️ 사전 렌더링(pre-rendering)의 종류

> 📌 **정적 생성**과 **SSR**의 차이점은, <u>언제 `HTML`을 생성</u>하는가?

- 유저가 요청하기 전에 미리 페이지를 만들어도 상관없다면 정적 생성을 적용
  - 예시) 마케팅 페이지, 블로그 게시물, 도움말 문서 등

### 1) 정적 생성

- 프로젝트가 <span style='color:dodgerblue'>**빌드하는 시점**</span>에 `HTML` 파일들이 생성됨
- (생성된 `HTML`을) 모든 요청에 재사용
- 퍼포먼스 이유로, `Next.js`는 정적 생성을 권고
- 정적 생성된 페이지들은 CDN에 캐시된다
- `getStaticProps` / `getStaticPaths`

<br />

#### ✔️ Custom Error Page 404

> next.js는 자주 사용하는, 서버에서 렌더링 할 필요가 없는
> 에러 페이지인 <u>404, 500 페이지를 기본적으로 제공</u>한다
> 하지만 디자인 또는 정보를 추가하고 싶을 경우 수정 가능하다

- pages > `404.ts` 파일 생성
- 빌트 타임에 정적 생성된다.

```tsx
import type { NextPage } from "next";
import { Icon } from "semantic-ui-react";
import styled from "styled-components";

const Error404: NextPage = () => {
  return (
    <ErrorWrap>
      <img alt='logo' src='/images/web_logo.png' />
      <Icon name='warning circle' color='red' />
      404: 페이지를 찾을 수 없습니다!
    </ErrorWrap>
  );
};

export default Error404;
```

![](https://images.velog.io/images/april_5/post/8ffede60-2c12-4a53-8922-af98083e7978/image.png)

<br />

#### ✔️ Custom Error Page 500

- [공식문서](https://nextjs.org/docs/advanced-features/custom-error-page#500-page)
- pages > `_error.ts` 파일 생성
  - 이 페이지는 정적으로 최적화되어 있진 않다
  - 에러 발생 시 **에러의 로그 등을 서버쪽으로 보내야 하는 경우가 필요**하기 떄문
- `npm build && npm start`

```tsx
function Error({ statusCode }) {
  return (
    <p>
      {statusCode
        ? `An error ${statusCode} occurred on server`
        : "An error occurred on client"}
    </p>
  );
}

Error.getInitialProps = ({ res, err }) => {
  const statusCode = res ? res.statusCode : err ? err.statusCode : 404;
  return { statusCode };
};

export default Error;
```

<br />

---

### 2) Server-side Rendering(SSR, Dynamic Rendering)

- <span style='color:dodgerblue'>**매 요청 마다**</span> `HTML`을 생성<span style='color:grey'>(되기 때문에 퍼포먼스가 떨어질 순 있다)</span>
- CDN에 캐시되지 않기 때문에 조금 느릴 순 있지만,
- 서버를 통해 프리 렌더링이 된 페이지는 **항상 최신 상태**를 유지한다.
- `getServerSideProps`

```tsx
import type { NextPage } from "next";
import Head from "next/head";
import { getProduct } from "../api/api";

const ProductItem: NextPage = ({ item }: any) => {
  return (
    item && (
      <>
        <Head>
          <title>{item.name}</title>
          <meta name='descriprion' content={item?.description} />
        </Head>
        // ... 생략
      </>
    )
  );
};

export default ProductItem;

export async function getServerSideProps(context: any) {
  const id = context?.params.id;
  const data = await getProduct(Number(id));

  return {
    // ProductItem 컴포넌트의 props로 전달된다
    props: {
      item: data,
    },
  };
}
```

![](https://images.velog.io/images/april_5/post/7edadef1-0dcf-48cc-866e-4ce90e535608/image.png)

<br />
