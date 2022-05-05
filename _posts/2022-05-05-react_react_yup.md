---
published: true
title: "React Hook Form | yup 사용해서 유효성 검사하기"
tags:
  - [React]
permalink: /study/react/yup

navigation: true
toc: true
toc_sticky: true

date: 2022-05-05
last_modified_at: 2022-05-05
---

![](https://velog.velcdn.com/images/april_5/post/53deafba-1879-4bdb-9c4d-f82190c7ab7c/image.png)

## React Hook Form 유효성 검사

### ✔️ @hookform/resolvers yup 설치

```shell
yarn add @hookform/resolvers yup
// or
npm install @hookform/resolvers yup
```

<br />

---

## [Schema Validation](https://react-hook-form.com/get-started#SchemaValidation)

<br />

### ✔️ schema 설정하기

```tsx
import { useForm } from "react-hook-form";
import { yupResolver } from "@hookform/resolvers/yup";
import * as yup from "yup";

const schema = yup
  .object({
    title: yup
      .string()
      .required("제목을 입력해주세요 😰")
      .min(2, "2자 이상 입력해주세요!"),
    body: yup.string().required("내용을 입력해주세요 😦"),
  })
  .required();
```

<br />

### ✔️ `useForm`에 `yupResolver`로 `schema` 적용하기

![](https://images.velog.io/images/april_5/post/228d2d83-bc4e-4e39-941d-6f85b4b4380b/validation.gif)

```tsx
import { useForm } from "react-hook-form";
import { yupResolver } from "@hookform/resolvers/yup";
import * as yup from "yup";

const schema = yup
  .object({
    title: yup
      .string()
      .required("제목을 입력해주세요 😰")
      .min(2, "2자 이상 입력해주세요!"),
    body: yup.string().required("내용을 입력해주세요 😦"),
  })
  .required();

export default function App() {
  const {
    register,
    handleSubmit,
    formState: { errors },
  } = useForm<IFormInputs>({
    resolver: yupResolver(schema),
  });

  const addItem = () => {
    // ...
  };

  return (
    <InputWrap onSubmit={handleSubmit(addItem)}>
      <div className='inputWrap'>
        <div className='input'>
          <input
            type='text'
            placeholder='Todo 제목을 입력해보세요!'
            {...register("title")}
          />
          <p className='message'>{errors.title?.message}</p>
        </div>
        <div className='input'>
          <input
            type='text'
            placeholder='Todo 내용을 입력해보세요!'
            {...register("body")}
          />
          <p className='message'>{errors.body?.message}</p>
        </div>
      </div>
      <input className='button' type='submit' value='등록' />
    </InputWrap>
  );
}
```

<br />

---

## [yup](https://www.npmjs.com/package/yup) ??

> **Yup**은 <span style='color:lightseagreen'>**Form validation**</span>을 위한 <span style='color:goldenrod'>**라이브러리**</span>이다.

<br />

### ✔️ yup 기본

```ts
import * as yup from "yup";

let schema = yup.object().shape({
  name: yup.string().required(),
  age: yup.number().required().positive().integer(),
  email: yup.string().email(),
  website: yup.string().url(),
  createdOn: yup.date().default(function () {
    return new Date();
  }),
});
```

<br /><br />
