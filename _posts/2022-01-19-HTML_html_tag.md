---
title: "π HTML:: μ λ°ν HTML νκ·Έ"
tags:
  - [HTML]
permalink: /study/html/tag1

navigation: true
toc: true
toc_sticky: true

date: 2022-01-19
last_modified_at: 2022-01-19
---

![](https://images.velog.io/images/april_5/post/6db3c337-496a-407c-a24c-3c121ca5c330/html5.png)

μμλλ©΄ μ μ©ν, HTML νκ·Έ!

## progress bar

### βοΈ `<progress>`

![](https://images.velog.io/images/april_5/post/2f30c9df-ac74-47c4-92e7-5a8cad8e77d9/progress%20bar.gif)

```html
<progress max="100" value="70"></progress>
```

[MDN HTML `<progress>`](https://developer.mozilla.org/ko/docs/Web/HTML/Element/progress)

<br />

### βοΈ `<meter>`

![](https://images.velog.io/images/april_5/post/7832c3b6-56a5-474b-bf07-0f8f20d63073/image.png)

```html
<meter min="0" max="100" low="33" high="66" optimum="80" value="30"></meter>
```

---

![](https://images.velog.io/images/april_5/post/5ae67d3c-69e7-45bf-b32d-7ec7cc722592/image.png)

```html
<meter min="0" max="100" low="33" high="66" optimum="80" value="50"></meter>
```

---

![](https://images.velog.io/images/april_5/post/289668a3-5b01-40ff-87da-c17414792111/image.png)

```html
<meter min="0" max="100" low="33" high="66" optimum="80" value="85"></meter>
```

<br />

[MDN HTML `<meter>`](https://developer.mozilla.org/ko/docs/Web/HTML/Element/meter)

---

## ν κΈ λ²νΌ?!

### βοΈ `<details>`

> `<summary>` μ ν¨κ» μ¬μ©ν΄μΌ νλ€

![](https://images.velog.io/images/april_5/post/9cc2708d-b751-4a6f-8ab3-fe005b8bd4b9/image.png)

```html
<details>
  <summary>ν΄λ¦­!!β¨</summary>
  λ λ§μ λ΄μ©μ λ³Ό μ μμ΄μ! π
</details>
```

<br />

[MDN HTML `<details>`](https://developer.mozilla.org/ko/docs/Web/HTML/Element/details)

---

## λ€μν `<input>`

### βοΈ `<input type='date'>`

<input type='date'>

```html
<input type="date" />
```

<br />

### βοΈ `<input type='month'>`

<input type='month'>

```html
<input type="month" />
```

<br />

### βοΈ `<input type='time'>`

<input type='time'>

```html
<input type="time" />
```

<br />

### βοΈ `<input type='color'>`

<input type='color'>

```html
<input type="color" />
```

<br />

### βοΈ `<input type='number'>`

<input type='number'>

```html
<input type="number" />
```

<br />

### βοΈ `<input type='range'>`

<input type='range'>

```html
<input type="range" />
```

<br />

[MDN HTML `<input>`](https://developer.mozilla.org/ko/docs/Web/HTML/Element/Input)

---

## λ·°ν¬νΈμ λ°μνλ `<picture>`

> `<source>` μ ν¨κ» μ¬μ©ν΄μΌ ν¨

<picture>
    <source media="(min-width: 1200px)" srcset="https://picsum.photos/800/600" />
    <source media="(min-width: 900px)" srcset="https://picsum.photos/800/600" />
    <source media="(min-width: 500px)" srcset="https://picsum.photos/800/600" />
    <img src="https://picsum.photos/800/600" alt="photos" />
</picture>

```html
<picture>
  <source media="(min-width: 1200px)" srcset="https://picsum.photos/800/600" />
  <source media="(min-width: 900px)" srcset="https://picsum.photos/800/600" />
  <source media="(min-width: 500px)" srcset="https://picsum.photos/800/600" />
  <img src="https://picsum.photos/800/600" alt="photos" />
</picture>
```

<br />

---

## μλ μμ± `<datalist>`

> `<input>` tagμ `id`μ λμΌν `id`λ₯Ό `<datalist>` tagμ μΆκ°ν΄μΌ ν¨

<label for="ice-cream-choice">Choose a flavor:</label>
<input list="ice-cream-flavors" id="ice-cream-choice" name="ice-cream-choice" />

<datalist id="ice-cream-flavors">
    <option value="Chocolate">
    <option value="Coconut">
    <option value="Mint">
    <option value="Strawberry">
    <option value="Vanilla">
</datalist>

```html
<label for="ice-cream-choice">Choose a flavor:</label>
<input list="ice-cream-flavors" id="ice-cream-choice" name="ice-cream-choice" />
<datalist id="ice-cream-flavors">
  <option value="Chocolate"></option>
  <option value="Coconut"></option>
  <option value="Mint"></option>
  <option value="Strawberry"></option>
  <option value="Vanilla"></option>
</datalist>
```

<br />

[MDN HTML `<datalist>`](https://developer.mozilla.org/ko/docs/Web/HTML/Element/datalist)

<br /><br />
