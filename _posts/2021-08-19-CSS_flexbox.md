---
title: "🎨 CSS:: FLEXBOX FROGGY🐸"
tags:
  - [CSS]
permalink: /study/CSS/flexbox

navigation: true
toc: true
toc_sticky: true

date: 2021-08-19
last_modified_at: 2021-08-19
---

![]()

`주니어 개발자의 개인 공부 과정을 기록합니다.`

# Flexbox 란?

> 일명 flexbox라 불리는 Flexible Box module은 flexbox 인터페이스 내의 아이템 간 **공간 배분**과 **강력한 정렬 기능**을 제공하기 위한 1차원 레이아웃 모델.
> flexbox를 1차원이라 칭하는 것은, 레이아웃을 다룰 때 **한 번에 하나의 차원(행이나 열)만을 다룬다**는 뜻이다.

✨참고✨ **2차원 모델**: 행과 열을 함께 조절하는 _CSS 그리드 레이아웃_

🚩**집중!** flexbox를 적용하려면, 적용하려는 요소에 `display: flex;`를 적용시킨다

## ○ justify-content

- 요소의 **가로 정렬**
- 5개의 값으로 가로로 정렬 시킬 수 있다

  - `flex-start` 요소들을 컨테이너의 왼쪽으로 정렬.
  - `flex-end` 요소들을 컨테이너의 오른쪽으로 정렬.
  - `center` 요소들을 컨테이너의 가운데로 정렬.
  - `space-between` 요소들 사이에 동일한 간격을 둔다.
  - `space-around` 요소들 주위에 동일한 간격을 둔다.

- 예시

```css
#pond {
  display: flex;
  justify-content: flex-end;
}
```

![](https://images.velog.io/images/april_5/post/068d5965-9b1f-4d1d-8f23-bd23ba3efa90/image.png)

<br />

- 예시2

```css
#pond {
  display: flex;
  justify-content: center;
}
```

![](https://images.velog.io/images/april_5/post/03b29aae-eda9-4f4f-99b1-65c9ae40a8eb/image.png)

<br />

- 예시3

```css
#pond {
  display: flex;
  justify-content: space-around;
}
```

![](https://images.velog.io/images/april_5/post/89a75b6c-2e7b-4dc0-a572-268e6a3d227a/image.png)

<br />

- 예시4

```css
#pond {
  display: flex;
  justify-content: space-between;
}
```

![](https://images.velog.io/images/april_5/post/4c88ba68-f557-4f20-96ff-e9f6d4e27fe5/image.png)

<br />

---

## ○ align-items

- 요소의 **세로 정렬**
- 5개의 값으로 가로로 정렬 시킬 수 있다

  - `flex-start` 요소들을 컨테이너의 꼭대기로 정렬.
  - `flex-end` 요소들을 컨테이너의 바닥으로 정렬.
  - `center` 요소들을 컨테이너의 세로선 상의 가운데로 정렬.
  - `baseline` 요소들을 컨테이너의 시작 위치에 정렬.
  - `stretch` 요소들을 컨테이너에 맞도록 늘린다.

- 예시

```css
#pond {
  display: flex;
  align-items: flex-end;
}
```

![](https://images.velog.io/images/april_5/post/0c755544-8579-446e-b516-ba2f2d63e3cf/image.png)

<br />

### ● justify-content+align-items

```css
#pond {
  display: flex;
  align-items: center;
  justify-content: center;
}
```

![](https://images.velog.io/images/april_5/post/b7a9440c-a016-4edf-90de-6f4b4ca2ed32/image.png)

<br />

---

## ○ flex-direction

- 요소의 정렬 방향을 지정
- 4개의 값으로 지정할 수 있다

  - `row` 요소들을 텍스트의 방향과 동일하게 정렬.
  - `row-reverse` 요소들을 텍스트의 반대 방향으로 정렬.
  - `column` 요소들을 위에서 아래로 정렬.
  - `column-reverse` 요소들을 아래에서 위로 정렬.

- 예시

```css
#pond {
  display: flex;
  flex-direction: column;
}
```

![](https://images.velog.io/images/april_5/post/8b5ad9ce-55f0-4a76-ac7e-0a917bff30e5/image.png)

<br />

### ● flex-direction+justify-content

#### FROGGY 단계 10

```css
#pond {
  display: flex;
  flex-direction: row-reverse;
  justify-content: flex-end;
}
```

![](https://images.velog.io/images/april_5/post/9ce10b3f-9212-41bc-b7f5-714a20707975/image.png)

<br />

#### FROGGY 단계 12

```css
#pond {
  display: flex;
  flex-direction: column-reverse;
  justify-content: space-between;
}
```

![](https://images.velog.io/images/april_5/post/0b369cb2-0d2c-4dbb-bec7-f9c13235de03/image.png)

<br />

#### FROGGY 단계 13

```css
#pond {
  display: flex;
  flex-direction: row-reverse;
  justify-content: center;
  align-items: flex-end;
}
```

![](https://images.velog.io/images/april_5/post/0bd05c11-ca5e-4906-a9f0-095551bb148a/image.png)

<br />

---

## ○ order

- 각 요소의 개별 순서 적용
- order의 기본 값은 0이며, 양수나 음수로 바꿀 수 있다
- 예시

```css
#pond {
  display: flex;
}

.yellow {
  order: 1; /* 노란 개구리의 순서를 뒤로 바꾼다 */
}
```

![](https://images.velog.io/images/april_5/post/a1795479-c740-4711-850f-c50c166cd1b7/image.png)

<br />
  
- 예시2

```css
#pond {
  display: flex;
}

.red {
  order: -1;
}
```

![](https://images.velog.io/images/april_5/post/3c676eaa-d851-4a08-b9e3-ceaa73b13ce3/image.png)

<br />

---

## ○ align-self

- 개별 요소에 적용하는 속성
- **align-items(세로 정렬)**의 값들로 지정한다

  - `flex-start` 요소들을 컨테이너의 꼭대기로 정렬.
  - `flex-end` 요소들을 컨테이너의 바닥으로 정렬.
  - `center` 요소들을 컨테이너의 세로선 상의 가운데로 정렬.
  - `baseline` 요소들을 컨테이너의 시작 위치에 정렬.
  - `stretch` 요소들을 컨테이너에 맞도록 늘린다.

- 예시

```css
#pond {
  display: flex;
  align-items: flex-start;
}

.yellow {
  align-self: flex-end;
}
```

![](https://images.velog.io/images/april_5/post/04602147-a876-4f6e-8c7a-90eb8f02e414/image.png)

<br />

### ●border+align-self

#### FROGGY 단계 17

```css
#pond {
  display: flex;
  align-items: flex-start;
}

.yellow {
  order: 1;
  align-self: flex-end;
}
```

![](https://images.velog.io/images/april_5/post/9590cc4e-35af-4d2c-8149-d85f2606e892/image.png)

<br />

---

## ○ flex-wrap

- 줄 바꿈
- 3개의 값으로 지정할 수 있다

  - `nowrap` 모든 요소들을 한 줄에 정렬.
  - `wrap 요소들을 여러 줄에 걸쳐 정렬.
  - `wrap-reverse 요소들을 여러 줄에 걸쳐 반대로 정렬.

- 예시

```css
#pond {
  display: flex;
  flex-wrap: wrap;
}
```

![](https://images.velog.io/images/april_5/post/e3d879ee-25de-47f1-bed3-954176015c30/image.png)

<br />

### ●bflex-direction+flex-wrap

#### FROGGY 단계 19

```css
#pond {
  display: flex;
  flex-direction: column;
  flex-wrap: wrap;
}
```

![](https://images.velog.io/images/april_5/post/739eaeb2-10cf-4a38-902f-a6cf67ea6f50/image.png)

<br />

---

## ○ flex-flow

- flex-direction+flex-wrap
- 예시

```css
#pond {
  display: flex;
  flex-flow: column wrap;
}
```

![](https://images.velog.io/images/april_5/post/9b122b0b-3222-47db-b1e9-44efae052659/image.png)

<br />

---

## ○ align-content

- 여러 줄 사이의 간격을 지정
- 5개의 값으로 지정할 수 있다
  - `flex-start` 여러 줄들을 컨테이너의 꼭대기에 정렬.
  - `flex-end` 여러 줄들을 컨테이너의 바닥에 정렬.
  - `center` 여러 줄들을 세로선 상의 가운데에 정렬.
  - `space-between` 여러 줄들 사이에 동일한 간격을 둔다.
  - `space-around` 여러 줄들 주위에 동일한 간격을 둔다.
  - `stretch` 여러 줄들을 컨테이너에 맞도록 늘린다.
- 🚩**집중!** `align-content`는 여러 줄들 사이의 간격을 지정하며, `align-items`는 컨테이너 안에서 어떻게 모든 요소들이 정렬하는지를 지정한다.
- 한 줄만 있는 경우, `align-conten`t는 효과를 보이지 않는다

- 예시

```css
#pond {
  display: flex;
  flex-wrap: wrap;
  align-content: flex-end;
}
```

![](https://images.velog.io/images/april_5/post/e1b3b1d5-ccd0-4da5-a224-d063dbdc0a34/image.png)

<br />

### ● flex-direction+align-content

#### FROGGY 단계 23

```css
#pond {
  display: flex;
  flex-wrap: wrap;
  flex-direction: column-reverse;
  align-content: center;
}
```

![](https://images.velog.io/images/april_5/post/fef47509-4121-4224-a190-ee2f9acd2ac7/image.png)

<br />

### ● FROGGY 단계 24

```css
#pond {
  display: flex;
  flex-flow: column-reverse wrap-reverse;
  justify-content: center;
  align-content: space-between;
}
```

![](https://images.velog.io/images/april_5/post/d0e03349-17a3-4958-b40c-8721b07f1b94/image.png)
