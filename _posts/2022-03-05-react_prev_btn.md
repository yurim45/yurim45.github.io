---
title: "🚀React:: React로 Prev/Next Btn 기능 구현✨"
tags:
  - [React]
permalink: /study/react/prev_btn

navigation: true
toc: true
toc_sticky: true

date: 2022-03-05
last_modified_at: 2022-03-05
---

![](https://images.velog.io/images/april_5/post/707c8c3b-7893-4776-890a-bd897bb78728/React.png)

무한스크롤 기능 구현하며 배운 `documentElement.clientWidth`를 활용하여 만든 페이지 넘기기 버튼!

화면 사이즈를 구해와서 각 카드의 데이터를 몇 개씩 가져와야 하는지 계산 한 후 Prev/Next Btn 클릭할 때 마다 해당 데이터 가져오는 방법으로 구현.

---

## ○ 완성된 코드

```jsx
handleNextBtn = (e) => {
  const { giftData, cnt, target } = this.state;
  if (giftData.length <= cnt) {
    this.setState({
      cnt: cnt - target,
    });
    e.preventDefault();
  } else {
    let dataToChange = giftData.slice(cnt, cnt + target);
    this.setState({
      cnt: cnt + target,
      items: dataToChange,
    });
  }
};
```

<br />

#### ● pageSize: 카드가 보여야 할 화면의 크기 가져오기

#### ● target: width가 230인 카드가 화면에 몇개 들어갈 수 있는지 계산

```jsx
pageSize: Math.round(document.documentElement.clientWidth * 0.8),
target: Math.ceil(this.pageSize / 230) - 1,
```

<br />

---

## 결과물

![](https://images.velog.io/images/april_5/post/0a493e6f-9ade-479a-8274-670f585c6387/PrevNextBtn.gif)

생각보다 시간이 오래걸렸던 기능이다. 솔직히 너무 어렵다고 생각해서 포기할 뻔 했던 기능인데, 멘토님께서 꼭 했으면 좋겠다하여.. 정말 울며 겨자먹기로 겨우 구현한 기능😅
돌아보니 그래도 나에게 남는 경험이 되었다! 멘토님 감사합니다ㅎㅎㅎㅎㅎㅎㅎㅎ👍👍👍

<br /><br />
