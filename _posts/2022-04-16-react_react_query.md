---
published: true
title: "axios와 react-query 기본"
tags:
  - [React]
permalink: /study/react/react-query

navigation: true
toc: true
toc_sticky: true

date: 2022-04-16
last_modified_at: 2022-04-16
---

![](https://velog.velcdn.com/images/april_5/post/130db741-40c6-49c4-b78b-520c68e1aa25/image.png)

프로젝트 전, `axios`와 `react-query` 사용해보기 연습!
`react-query`의 세세한 설정 등이 많아서 차근차근 연습해야겠... 😅😅

---

# `axios`와 `react-query` 기본 익히기

기존의 데이터 페칭에는 로딩 상태 관리 및 페칭한 데이터 관리 등을 위해 여러 hooks을 사용해야 했으나, `react-query`를 사용하면 훨씬 간결하게 로직을 작성할 수 있다.

### ✔️ 코드 비교

- ❌ as-is

![](https://images.velog.io/images/april_5/post/d15216b2-6f8b-4888-b27c-9e2da201f916/image.png)

- 👌 to-be

![](https://images.velog.io/images/april_5/post/ac383491-d5e5-4b25-b0d5-357f18756e97/image.png)

<br />

![](https://images.velog.io/images/april_5/post/560857ca-0ccd-41d8-a896-a504458665c3/image.png)

## [axios](https://axios-http.com/kr/docs/api_intro)

### ✔️ 설치

- npm 사용하기:

```bash
npm install axios
```

### ✔️ 참고: 기본 사용법 ⬇️

🔹 기본 사용법 ➡️ [Axios-사용법](https://velog.io/@april_5/TIL43-Axios-%EC%82%AC%EC%9A%A9%EB%B2%95)

<br />

---

![](https://images.velog.io/images/april_5/post/181e7505-1d96-4a11-9280-fbcf797ead02/image.png)

## [react-query](https://react-query.tanstack.com/guides/important-defaults)

## ✅ 기본 설정

### ✔️ 설치

- npm 사용하기:

```bash
npm i react-query
```

<br />

### ✔️ App.js 설정

```jsx
import React from "react";
import ReactDOM from "react-dom";
import { QueryClient, QueryClientProvider } from "react-query";

const queryClient = new QueryClient();

export default function App() {
  return (
    <QueryClientProvider client={queryClient}>
      <Example />
    </QueryClientProvider>
  );
}
```

### | 타입스크립트

```ts
type Group = {
  name?: string;
  age: number;
};
function useGroups() {
  return useQuery<Group[], Error>("groups", fetchGroups);
}
```

<br />

---

## ✅ Query Basics

- 쿼리는 고유키 (예시에서 todos) 에 연결된 비동기 데이터 소스 단위로 작동.
- 쿼리는 서버에서 데이터를 가져오기 위해 모든 `Promise` 기반 메서드(GET 및 POST 메서드 포함) 에 대해 사용이 가능.
  - SWR 은 GET요청

```jsx
import { useQuery } from "react-query";

function App() {
  const info = useQuery("todos", fetchTodoList);
}
```

<br />
