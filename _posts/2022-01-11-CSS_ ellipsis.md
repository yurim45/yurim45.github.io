---
title: "🎨 CSS:: 말줄임 처리하기 ellipsis"
tags:
  - [CSS]
permalink: /study/CSS/ellipsis

navigation: true
toc: true
toc_sticky: true

date: 2022-01-11
last_modified_at: 2022-01-11
---

![](https://images.velog.io/images/april_5/post/4c054428-11d4-4099-a4d3-e4752b47eb4e/image.png)

`Lorem ipsum dolor sit amet` ➔ `Lorem ipsum dol...`

글 등록, 댓글 등의 기능 구현할 때
생각보다 꽤 자주 사용하게 되었던 CSS 속성 중 하나인,
넘치는 글 제어하기?

<br />

---

## 한 줄로 줄이기

```css
.review {
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
  word-break: break-all;
}
```

`overflow: hidden;`: 박스에서 넘쳐난 텍스트 숨기기
`white-space: nowrap;`: 줄바꿈이 없어짐
`text-overflow: ellipsis;`: ... 말줄임 효과
`word-break: break-all;`: 어절이 유지되지 않고 끊어져서 줄바꿈 됨

<br />

---

## 여러 줄로 바꾸기

```css
.review {
  overflow: hidden;
  white-space: normal;
  text-overflow: ellipsis;
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
}
```

`-webkit-line-clamp`: 글의 최대 라인수를 결정

> `-webkit`은 크로스브라우징을 위해 필요한데, <br />`-webkit`은 구글, 사파리 브라우저에서 사용 가능하다
> 적용할 때 브라우저 지원 범위를 확인하고 사용하기!!

<br />
<br />
