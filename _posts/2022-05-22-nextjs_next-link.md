---
published: true
title: "Next.js Dynamic Routes, next/link (3)"
tags:
  - [NextJs]
permalink: /study/nextjs/next-link

navigation: true
toc: true
toc_sticky: true

date: 2022-05-22
last_modified_at: 2022-05-22
---

Github: https://github.com/yurim45/web-template

# Dynamic Routes, next/link

![](https://images.velog.io/images/april_5/post/738bfe32-0fc3-4ef3-91cf-6eeab0fd3a82/nextjs_dynamic_routes.gif)

<br />

## 1️⃣ Dynamic Routes: `useRouter()`

> [공식문서](https://nextjs.org/docs/routing/dynamic-routes)로 동적 라우팅 구현하기

- Next.js에서 페이지( `[param]` )에 대괄호를 추가 하여 동적 경로를 생성 할 수 있다

```tsx
import React, { useState, useEffect } from "react";
import type { NextPage } from "next";
import { useRouter } from "next/router";

const Product: NextPage = () => {
  const route = useRouter();
  const { id } = route.query;

  console.log(route);

  return <p>Product: {id}</p>;
};

export default Product;
```

<br />

![](https://images.velog.io/images/april_5/post/0dd7427e-3e77-4028-b67a-9a921c6f0088/image.png)

<br />

---

## 2️⃣ next/link: `Link`

> [공식문서](https://nextjs.org/docs/api-reference/next/link)로 `<Link href="/">` 구현하기

- 클라이언트 사이드에서 `Link` 로 경로간의 이동이 가능하다.

<br />

### `Link`의 props

- `href`: 탐색할 경로 또는 URL. 필수!
  - 필수이기 때문에 `href`를 안 적으면 에러난다
- `as`: 브라우저 URL 표시줄에 표시될 경로를 입력. 선택 사항
  - Next.js 9.5.3 이전에는 동적 경로에 사용되었으므로 이전 문서 에서 작동 방식을 확인
- `passHref`: `href` property를 `Link` 자식에게 강제로 전달하게 한다. 기본값은 `false`.
- `prefetch`: 백그라운드에서 페이지를 미리 가져온다. 기본값은 `true`.
  - `<Link />` 뷰 포트에 있는 모든 항목(초기에 혹은 스크롤을 통해)이 미리 로드(정적 페이지를 만든다) 된다.
  - `prefetch = { false }`를 통해 `prefetch`를 비활성화할 수 있다.
  - 정적 생성을 사용하는 페이지는 더 빠른 페이지 전환을 위해 데이터가 포함된 JSON파일을 미리 로드한다.
- `replace`: history 스택(방문 기록)에 새 `url`을 추가하는 대신 현재 상태를 변경한다. 기본값은 `false`.
- `scroll`: 페이지 전환 후 페이지 상단으로 스크롤할지 여부. 기본값은 `true`.
- `shallow`: `getStaticProps`, `getServerSideProps`, `getInitialProps`을 다시 실행하지 않고 현재 경로를 업데이트. 기본값은 `false`.

<br />

```tsx
import Link from "next/link";

function Home() {
  return (
    <Link href={`/product/${item.id}`}>
      <a>
        <img alt={item.name} src={item.image_link} />
        <strong className='title'>{item.name}</strong>
        <div className='info'>
          {item.category} {item.product_type}
        </div>
        <strong className='price'>${item.price}</strong>
      </a>
    </Link>
  );
}
```

<br /><br />
