---
title: "πReact:: Reactλ‘ λ¬΄νμ€ν¬λ‘€ κ΅¬νβ¨"
tags:
  - [React]
permalink: /study/react/infinite_scroll

navigation: true
toc: true
toc_sticky: true

date: 2022-03-01
last_modified_at: 2022-03-01
---

![](https://images.velog.io/images/april_5/post/707c8c3b-7893-4776-890a-bd897bb78728/React.png)

1μ°¨ νλ‘μ νΈλ₯Ό νλ©΄μ λ©μΈ νμ΄μ§μ μ μ²΄ μνμ κ°μ Έμ€λ κΈ°λ₯ κ΅¬ν μ€, <span style="color:dodgerblue">μ±λ₯μ ν λ²μ λ§μ μνμ΄ μ λΆ λΈμΆλκΈ° λ³΄λ¨ μ€ν¬λ‘€μ λ°λΌ μΌμ  λ°μ΄ν°μ μ λ§νΌ νΈμΆλλλ‘ κΈ°λ₯ κ΅¬νμ΄ νμ</span>νλ€. κ·Έλ΄ λ μκ² λ λ¬΄νμ€ν¬λ‘€ κΈ°λ₯ κ΅¬ννλ λ΄μ©μ μ λ¦¬ν΄λ³Έλ€.

<br />

# λ¬΄νμ€ν¬λ‘€ Infinite Scroll

> λ¬΄νμ€ν¬λ‘€μ νλ©΄μ λ§¨ μλκΉμ§ μ€ν¬λ‘€μ νλ©΄ μλ‘μ΄ μ»΄ν¬λνΈκ° λλλλ ννμ΄λ€. νμ΄μ€λΆ, μΈμ€νκ·Έλ¨ λ± λ€μν μ¬μ΄νΈκ° μ΄λ¬ν λ¬΄ν μ€ν¬λ‘€ νμμ λκ³  μλ€. λΆνμνκ² μλ§μ λ°μ΄ν°λ₯Ό κΈμ΄μ€κΈ°λ³΄λ€λ, νλ²μ 10-20κ° μ λμ ν¬μ€νΈλ§ κ°μ Έμμ μ€ν¬λ‘€ λ  λλ§λ€ μλ°μ΄νΈ λλ νμμ΄λ€.

ν΄λΉ κΈ°λ₯ κ΅¬νμ λ κ°μ§ ννλ‘ ν΄λ³΄μλλ°,
μ²« λ²μ§Έλ λ°±μλλ‘ λΆν° 100κ°μ λ°μ΄ν°λ₯Ό ν λ²μ λ°μμμ ν΄λΌμ΄μΈνΈμμ 8κ°μ© λλμ΄ λΏλ €μ£Όλ ννμ,
λ λ²μ§Έλ μ²μ λ‘λ©νλ μκ°, APIλ‘ λΆν° 10κ°μ© λ°μ΄ν°λ₯Ό νΈμΆνλ ννλ‘ κ΅¬ννλ€.

νμ€ν λ λ²μ§Έλ‘ κΈ°λ₯ κ΅¬νμ νμ λμ μλκ° λ λΉ¨λλ€π

<br />

---

## β μμ±λ μ½λ

```jsx
componentDidMount() {
  this.getData();
  window.addEventListener('scroll', this.infiniteScroll);
}

componentWillUnmount() {
  window.removeEventListener('scroll', this.infiniteScroll);
}

getData = () => {
  const { num } = this.state;
  fetch(`${GET_CATEGORY_API}/categories?size=10&page=${num}`)
    .then(response => response.json())
    .then(productsdata => {
    this.setState({
      productsData: productsdata.message,
      num: num + 1,
    });
  });
};

infiniteScroll = () => {
  const { documentElement, body } = document;
  const { num } = this.state;
  const scrollHeight = Math.max(documentElement.scrollHeight,body.scrollHeight);
  const scrollTop = Math.max(documentElement.scrollTop, body.scrollTop);
  const clientHeight = documentElement.clientHeight;

  if (scrollTop + clientHeight >= scrollHeight) {
    fetch(`${GET_CATEGORY_API}/categories?size=10&page=${num}`)
      .then(response => response.json())
      .then(productsdata => {
      this.setState({
        productstData: [
          ...this.state.productsData,
          ...productsdata.message,
        ],
      });
    });
    this.getData();
  }
};

  render() {
    const { productstData } = this.state;
    return (
      <section className="mainProducts mainMiddleCards">
        <article className="mainGoods">
          <h2 className="title">λ§μκ» λλ¬λ³΄μΈμ</h2>
          <MainMediumCard data={productstData} />
        </article>
      </section>
    );
  }

```

<br />

---

## β νλμ© μ΄ν΄λ³΄λ©΄,

### β componentDidMountλ  λ λ°μ΄ν° λ°μμ€λ©° μ΄λ²€νΈ μ€ν, componentWillUnmountλ  λ μ΄λ²€νΈ μ κ±°

- `componentDidMount`λ  λ `API`λ‘ λΆν° 10κ°μ© λ°μμ€κΈ°

```jsx
componentDidMount() {
    this.getData();
    window.addEventListener('scroll', this.infiniteScroll);
  }

componentWillUnmount() {
  window.removeEventListener('scroll', this.infiniteScroll);
}

getData = () => {
  const { num } = this.state;
  fetch(`${GET_CATEGORY_API}/categories?size=10&page=${num}`)
    .then(response => response.json())
    .then(productsdata => {
    this.setState({
      productsData: productsdata.message,
      num: num + 1,
    });
  });
};
```

<br />

### β μ€ν¬λ‘€μ΄ λμ λ€λ€λ₯΄λ©΄ API νΈμΆν΄μ λ°μ΄ν° λ°μμ€κΈ°

```jsx
infiniteScroll = () => {
  const { documentElement, body } = document;
  const { num } = this.state;
  const scrollHeight = Math.max(
    documentElement.scrollHeight,
    body.scrollHeight
  );
  const scrollTop = Math.max(documentElement.scrollTop, body.scrollTop);
  const clientHeight = documentElement.clientHeight;

  if (scrollTop + clientHeight >= scrollHeight) {
    fetch(`${GET_CATEGORY_API}/categories?size=10&page=${num}`)
      .then((response) => response.json())
      .then((productsdata) => {
        this.setState({
          productstData: [...this.state.productsData, ...productsdata.message],
        });
      });
    this.getData();
  }
};
```

<br />

- `document.documentElement`μ μ κ·Όν΄μ documentμ μ€ν¬λ‘€ λμ΄μ μ κ·Όν  μ μλ€.
- λ¬΄νμ€ν¬λ‘€ κΈ°λ₯μ κ΅¬ννλ©° μλ‘­κ² μκ² λ λ΄μ©μ΄λ€.
  ![](https://images.velog.io/images/april_5/post/9f910b32-306d-48f8-9fc0-2b9c4269689e/image.png)

- **offsetTop**: μΌμͺ½ λ λ§¨ μλ₯Ό κΈ°μ€μΌλ‘ ν μμΉκ°. containerμ μμΉκ°μ λ°λ‘ λΆμ¬νμ§ μμΌλ©΄ 0μΌλ‘ κ³ μ λμ΄ μλ€.
- **clientTop**: clientμ offsetμ μ¬μ΄μ μλ κ²½κ³μ μ΄λ€.
- **scrollHeight**: νλ©΄μ λ³΄μ΄μ§ μλ κ³³κΉμ§μ μ΄ κΈΈμ΄λ₯Ό μλ―Ένλ€. μ€ν¬λ‘€λ‘ μ§λμ¨ κ³³, νμ¬μ λ³΄κ³  μλ κ³³, μμΌλ‘ λ΄λ €κ° κ³³μ λͺ¨λ ν©μΉ μ¬μ΄νΈμ μ΄ κΈΈμ΄.
- **scrollTop**: μ€ν¬λ‘€ν΄μ μ¬λ¦¬λ©΄ ν΄λΌμ΄μΈνΈμλ λ³΄μ΄μ§ μλ μ¬λΌκ°λ²λ¦° κ΅¬κ°

μ€ν¬λ‘€ λμ΄λ₯Ό κ²μ¬ν΄μ λμ λ€λ€λ₯Ό λ λ°μ΄ν°λ₯Ό μ£Όλ¬Έν  μ μκ³ , μ΄λ κ²νλ©΄ ν¨μλ₯Ό νλ² λ°μ μ€ννμ§ μλλ€. μΆκ°λ‘ λ°μ΄ν°κ° λΆλ¬μμ§λ©΄ μ€ν¬λ‘€μ μ΄ κΈΈμ΄κ° λ³νκΈ° λλ¬ΈμΈλ°, κ³μ λ³νλ μ΄ κΈΈμ΄λ₯Ό κ³μ°ν΄μ λ°μ΄ν°λ₯Ό λΆλ¬μ€λ λ°©λ²μ μ°ΎμμΌνλ€.

`if (scrollTop + clientHeight >= scrollHeight)`

μ€ν¬λ‘€ νκ³Ό ν΄λΌμ΄μΈνΈ λμ΄μ κ°μ΄ μ€ν¬λ‘€ λμ΄λ³΄λ€ ν¬κ±°λ κ°μ λ, λΌλ μ‘°κ±΄μ λ°μλ€.

<br />

---

# κ²°κ³Όλ¬Ό

### μ€μ€μ€μ€μ€μ€μ€μ€μ€!!!!! +\_ + λλ€!!!!!!!!!!!!!!!!

![](https://images.velog.io/images/april_5/post/c61e8378-5e7f-4084-8a9c-2fa2b4db94d2/%E1%84%86%E1%85%AE%E1%84%92%E1%85%A1%E1%86%AB%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%A9%E1%86%AF.gif)

[μμ ν¬κΈ° λ° μ€ν¬λ‘€](https://javascript.info/size-and-scroll)
[Reactλ‘ λ¬΄ν μ€ν¬λ‘€ κ΅¬ννκΈ°1](https://medium.com/@ghur2002/react%EC%97%90%EC%84%9C-infinite-scroll-%EA%B5%AC%ED%98%84%ED%95%98%EA%B8%B0-128d64ea24b5)
[Reactλ‘ λ¬΄ν μ€ν¬λ‘€ κ΅¬ννκΈ°2](https://velog.io/@hyounglee/TIL-56)
