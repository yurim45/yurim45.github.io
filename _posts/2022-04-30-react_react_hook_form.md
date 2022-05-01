---
published: true
title: "React Hook Form | 기본"
tags:
  - [React]
permalink: /study/react/react-hook-form

navigation: true
toc: true
toc_sticky: true

date: 2022-04-30
last_modified_at: 2022-04-30
---

![](https://velog.velcdn.com/images/april_5/post/bac21d08-a97b-458b-9d40-472c50f6bf42/image.png)

## [React Hook Form](https://react-hook-form.com/get-started) 기본 사용법 익히기

<br />

### ✔️ React Hook Form 설치

```bash
npm install react-hook-form
```

<br />

---

## useForm() 살펴보기

<span style='color:fuchsia'>**React Hooks Form**</span>을 적용하고 싶다면 먼저 `useForm()`이라는 hook을 불러와야한다

> <span style='color:violet'>**React Hooks Form**</span>의 거의 모든 기능은 이 hook에서 나오는데,
> 그 중 몇 가지만 알아도 React Hooks Form의 대부분의 기능을 사용할 수 있

```tsx
import { useForm } from "react-hook-form";

const {
  register, // input에서 값을 불러오기 위한 함수
  handleSubmit, // React-Hook-Form에서 Submit을 관리하기 위해 만든 함수
  watch, // input에서 입력하는 값을 실시간으로 확인하기 위한 함수
} = useForm<InputType>();
```

<br />

### ✔️ `register`

> input에서 값을 불러오기 위한 함수

`input` 태그에 `{...register('사용하고 싶은 이름')}`을 입력한다.
`사용하고 싶은 이름`은 `input` 태그의 `name`의 역할과 비슷하다?!

```tsx
<input
  type='text'
  placeholder='Todo 제목을 입력해보세요!'
  {...register("title")}
/>
```

<br />

### ✔️ `watch`

> input에서 입력하는 값을 실시간으로 확인하기 위한 함수

입력한 값을 불러올 땐 `watch` 함수를 사용.

```tsx
console.log(watch()); // 콘솔에서 실시간으로 확인 가능
```

<br />

### ✔️ `handleSubmit`

> React-Hook-Form에서 Submit을 관리하기 위해 만든 함수

`handleSubmit`은 함수를 인자로 받으며 그 함수에 `data`를 인자를 넘겨준다.

- `handleSubmit`이 넘겨주는 데이터는 `watch` 함수가 <span style='color:fuchsia'>**가장 마지막으로 출력하는 데이터**</span>

<br />

---

## 예제) 코드 살펴보기

```tsx
const TodoCreator: NextPage = (): JSX.Element => {
  const [todos, setTodos] = useRecoilState<TodosTypes[]>(todosState);
  const { register, handleSubmit, watch } = useForm<InputType>();

  const addItem = () => {
    const nextId: number =
      todos.length > 0 ? todos[todos.length - 1].id + 1 : 0;

    const result = watch();
    const todo: TodosTypes = {
      id: nextId,
      title: result.title,
      body: result.body,
    };

    mutate(todo);
    setTodos([...todos, todo]);
  };

  return (
    <form onSubmit={handleSubmit(addItem)}>
      <div className='inputWrap'>
        <input
          type='text'
          placeholder='Todo 제목을 입력해보세요!'
          {...register("title")}
        />
        <input
          type='text'
          placeholder='Todo 내용을 입력해보세요!'
          {...register("body")}
        />
      </div>
      <input className='button' type='submit' value='등록' />
    </form>
  );
};
```

<br />
<br />

---

## validation

- required
  - 예시) `<input {...register("firstName", { required: true, maxLength: 20 })} />`
- min
  - 예시) `<input type="number" {...register("age", { min: 18, max: 99 })} />`
- max
- minLength
- maxLength
- pattern
  - 예시) `<input {...register("lastName", { pattern: /^[A-Za-z]+$/i })} />`
- validate

<br />

### ✔️ 예시 코드

```tsx
<input
  type='text'
  placeholder='Todo 제목을 입력해보세요!'
  {...(register("title"), { required: true })}
/>
```

![](https://images.velog.io/images/april_5/post/dab7cf4e-fa49-495a-9bfb-9609a01b9511/image.png)

<br /><br />
