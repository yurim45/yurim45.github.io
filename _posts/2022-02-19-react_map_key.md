---
title: "🚀React:: map()과 Key💡"
tags:
  - [React]
permalink: /study/react/map_key

navigation: true
toc: true
toc_sticky: true

date: 2022-02-19
last_modified_at: 2022-02-19
---

![](https://images.velog.io/images/april_5/post/707c8c3b-7893-4776-890a-bd897bb78728/React.png)

westagram project 중 react로 댓글 기능을 구현할 때 `map()`를 사용하여 구현하게 되었는데, 실행시켜 보니 작동하는 데에 문제는 없으나 에러가 발생했다.
에러의 내용은 `각 항목에 key를 넣어야 한다`는 내용쓰....😂

![](https://images.velog.io/images/april_5/post/fc92fd61-9fd8-4205-a6ee-bf8f5250251e/image.png)

작동에는 문제가 없으나 성능적으로 문제가 발생하니.. 해결해야 했다. 그렇게 해서 알게된 map()과 Key💡의 내용을 정리해본다.

<br />

---

## ○ Key💡

> `key`는 element list를 만들 때 포함해야 하는 **특수한 문자열 attribute**

- `key`는 react가 어떤 항목을 변경, 추가 또는 삭제할지 식별하는 데에 도움을 준다
- `key`는 element에 안정적인 고유성을 부여하기 위해 **array 내부의 element에** 지정해야 한다

<br />

#### 🔘 `key`를 선택하는 가장 좋은 방법은?

- 리스트의 다른 항목들 사이에서 해당 항목을 고유하게 식별할 수 있는 **문자열**을 사용하는 것
- 대부분의 경우 **데이터의 ID**를 `key`로 사용
- 렌더링 한 항목에 대한 안정적인 ID가 없다면 최후의 수단으로 `index`를 `key`로 사용할 수는 있으나, **항목의 순서가 바뀔 수 있는 경우** key에 index를 사용하는 것은 **지양!**
  - ✨참고✨ 만약 리스트 항목에 명시적으로 key를 지정하지 않으면 React는 기본적으로 인덱스를 key로 사용하니 참고!

<br />

#### 🔘 `key`적용 방법

- (`key`는 주변 배열의 context에서만 의미가 있으므로) **배열 안에 key를 지정**
- Key는 형제 사이에서만 고유한 값이어야 한다
  - Key는 배열 안에서 형제 사이에서 고유해야 하고
  - 전체 범위에서 고유할 필요는 없다
  - 두 개의 다른 배열을 만들 때 동일한 key를 사용할 수 있다

<br />

### ● JSX에 `map()` 포함시키기

- 실제 작성한 코드에 key를 포함시켰다

```jsx
 render() {
  const { content, addComment } = this.state;
    return (
      <>
        <div className="commentList">
          {addComment.map((el, index) => {
            return <AddComment addComment={(addComment, el)} key={index} />;
          })}
        </div>
```

<br />

---

💬 원래 작성했던 코드는 아래였으나.. 무언가 눈에 익은? 맞는? 코드가 아닌것 같아 고민하다가 수정했다....;;

- 원래 작성했던 코드는 자식 component에서 map() 사용하고, key값을 상위 element에 적용시켰으나
- 최종 제출한 코드는 부모 component에서 map() 사용하고 key 적용
- 과연 코드 리뷰 시 어떤 코멘트가 달릴지...
  ![](https://images.velog.io/images/april_5/post/6bddf3db-c3c3-4318-b1f8-64f3eb417c45/image.png)
  ![](https://images.velog.io/images/april_5/post/0eb4579c-808d-4852-9d0a-e01ab5d1dcbd/image.png)

[React_doc 리스트와 Key]
(https://ko.reactjs.org/docs/lists-and-keys.html/)

<br /><br />
