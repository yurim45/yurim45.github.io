---
published: true
title: "useMutation 사용해보기"
tags:
  - [React]
permalink: /study/react/react-query/use-mutation

navigation: true
toc: true
toc_sticky: true

date: 2022-04-24
last_modified_at: 2022-04-24
---

![](https://velog.velcdn.com/images/april_5/post/0fe285b0-b5e6-4efe-8fa2-be9798cb5732/image.png)

> 서버에서 데이터를 <span style='color:fuchsia'>**가져오는 것**</span>은 단순히 <span style='color:fuchsia'>**useQuery**</span>를 사용하면 될테지만,
> 서버의 데이터를 <span style='color:mediumslateblue'>**업데이트 하는 경우**</span>에는 동일한 방식을 사용하는 것이 적절치 않다. 데이터의 <span style='color:mediumslateblue'>**생성/수성/삭제 (CRUD)**</span> 시에는 <span style='color:mediumslateblue'>**useMutation**</span> hook을 사용하면 된다.

<br />

## [공식문서](https://react-query.tanstack.com/reference/useMutation)로 확인하기

```js
const {
  data,
  error,
  isError,
  isIdle,
  isLoading,
  isPaused,
  isSuccess,
  mutate,
  mutateAsync,
  reset,
  status,
} = useMutation(mutationFn, {
  mutationKey,
  onError,
  onMutate,
  onSettled,
  onSuccess,
  retry,
  retryDelay,
  useErrorBoundary,
  meta,
});

mutate(variables, {
  onError,
  onSettled,
  onSuccess,
});
```

- `useMutation()`의 첫번째 인자인 `mutationFn`는 <span style='color:tomato'>**필수!**</span>
- `useMutation()`의 옵션과 리턴하는 데이터의 종류는 매우 다양하다. 공식문서 꼭 확인해보기!

<br />

---

## `useMutation` 써보기

<br />

### ✔️ 작업하기

```ts
import { useMutation } from "react-query";
import { getApi } from "@apis/index";

const useTodoCreator = () => {
  const mutation = useMutation((newTodo: TodosTypes) =>
    getApi.post("/todos", newTodo)
  );

  return mutation;
};

export default useTodoCreator;
```

<br />

### ✔️ 사용하기

```ts
import useTodoCreator from "@hooks/todos/useTodoCreator";

const TodoCreator: NextPage = (): JSX.Element => {
  const { mutate } = useTodoCreator();
  // ...

  const addItem = () => {
    // ...
    mutate(todo);
  };

  return (
    <InputWrap>
      // ...
      <button type='button' onClick={addItem}>
        등록
      </button>
    </InputWrap>
  );
};

export default TodoCreator;
```
