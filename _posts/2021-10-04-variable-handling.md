---
title: "๐ก์ปดํจํฐ๊ฐ ๋ณ์๋ฅผ ์ฒ๋ฆฌํ๋ ๋ฐฉ๋ฒ"
tags:
  - [CS]
permalink: /cs/variable_handling

navigation: true
toc: true
toc_sticky: true

date: 2021-10-04
last_modified_at: 2021-10-04
---

![]()

`๊ฐ์ธ ๊ณต๋ถ ๊ณผ์ ์ ๊ธฐ๋กํฉ๋๋ค.`

ํ์์์ ์ผ ํ๊ณ  CS์ ์ค์์ฑ์ ๋๋ผ๋ฉด์ ๋ฐฐ์ฐ๊ฒ ๋ CS์ ๊ธฐ์ด๋ค..
๊ทธ ์ค ์ค๋์ <span style="color:dodgerblue">**์ปดํจํฐ๊ฐ ๋ณ์๋ฅผ ์ฒ๋ฆฌํ๋ ๋ฐฉ๋ฒ**</span>์ ๋ํด ์ ๋ฆฌํด ๋ณธ๋ค.

---

## ๐ What I Will Learn

1. C์ธ์ด์์ ์ฌ์ฉํ๋ ๋ค์ํ ๋ณ์๋ฅผ ์ฒ๋ฆฌํ๋ ๋ฐฉ๋ฒ ์ตํ๊ธฐ
2. ์ง์ญ ๋ณ์, ์ ์ญ ๋ณ์, ๋ ์ง์คํฐ ๋ณ์ ๋ฑ์ ๋ํด ์ดํดํ๊ธฐ
3. ํน์ ํ ํจ์์ ๊ฐ์ ์ ๋ฌํ๊ฑฐ๋ ์ฃผ์๋ฅผ ์ ๋ฌํ๋ ๋ฐฉ๋ฒ ์ดํดํ๊ธฐ

---

# ์ปดํจํฐ๊ฐ ๋ณ์๋ฅผ ์ฒ๋ฆฌํ๋ ๋ฐฉ๋ฒ

## โ๏ธ ํ๋ก๊ทธ๋จ ๋ฉ๋ชจ๋ฆฌ ์ฃผ์

- ์ปดํจํฐ์์ ํ๋ก๊ทธ๋จ์ด ์คํ๋๊ธฐ ์ํด์๋ _ํ๋ก๊ทธ๋จ์ด ๋ฉ๋ชจ๋ฆฌ์ ์ ์ฌ_(Load)๋์ด์ผ ํ๋ค

- (๋น์ฐํ) ํ๋ก๊ทธ๋จ ํฌ๊ธฐ๋ฅผ ์ถฉ๋นํ  ์ ์์ ๋งํผ์ *๋ฉ๋ชจ๋ฆฌ ๊ณต๊ฐ*์ด ์์ด์ผ ํ๋ค

  - ํํ, ์ปดํจํฐ๋ค์ ๋ฉ๋ชจ๋ฆฌ ์ฌ์์ 8GB, 16GB, 32GB ์ ๋ ๋๋๋ฐ
  - ํน์ ํ ํ๋ก๊ทธ๋จ์ ๋๋ธ ํด๋ฆญํด์ ์คํํ๋ฉด ๊ทธ ํ๋ก๊ทธ๋จ์ด ๋ฉ๋ชจ๋ฆฌ์ ์ ์ฌ๋์ด ์คํ๋๋ค

- ์ผ๋ฐ์ ์ธ <span style="color:dodgerblue">**์ปดํจํฐ์ ์ด์์ฒด์ ๋ ๋ฉ๋ชจ๋ฆฌ(RAM) ๊ณต๊ฐ์ ๋ค ๊ฐ์ง๋ก ๊ตฌ๋ถ**</span>ํ์ฌ ๊ด๋ฆฌํ๋ค.
  - `์ฝ๋ ์์ญ`: ์ฝ๋๋ฅผ ํ์ค์ฉ ์คํ์ํค๋ ์์ญ
  - `๋ฐ์ดํฐ ์์ญ`: ์ ์ญ๋ณ์ ํน์ ์ ์ ๋ณ์๋ฅผ ๋ด๊ณ  ์๋ค.
    <span style="color:blue">**ํ๋ก๊ทธ๋จ์ ์์๊ณผ ๋์์ ํ ๋น๋๊ณ , ํ๋ก๊ทธ๋จ์ด ์ข๋ฃ๋์ด์ผ ๋ฉ๋ชจ๋ฆฌ๊ฐ ์๋ฉธ๋๋ ์์ญ**</span>
  - `ํ ์์ญ`: ๊ฐ๋ฐ์๊ฐ ํ ๋น/ํด์ ํ๋ ๋ฉ๋ชจ๋ฆฌ ๊ณต๊ฐ์ด๋ค. ๊ฐ๋น์ง ์ปฌ๋ ํฐ๊ฐ ์๋์ผ๋ก ํด์ ํ๋ค.
    ์ด ๊ณต๊ฐ์ ๋ฉ๋ชจ๋ฆฌ ํ ๋นํ๋ ๊ฒ์ ๋์  ํ ๋น(Dynamic Memory Allocation)์ด๋ผ๊ณ ๋ ๋ถ๋ฅธ๋ค.
  - `์คํ ์์ญ`: ํ๋ก๊ทธ๋จ์ด ์๋์ผ๋ก ์ฌ์ฉํ๋ ์์ ๋ฉ๋ชจ๋ฆฌ ์์ญ.
    <span style="color:blue">**ํจ์ ํธ์ถ ์ ์์ฑ๋๋ ์ง์ญ ๋ณ์์ ๋งค๊ฐ๋ณ์๊ฐ ์ ์ฅ๋๋ ์์ญ์ด๊ณ ,
    ํจ์ ํธ์ถ์ด ์๋ฃ๋๋ฉด ์ฌ๋ผ์ง๋ค.**</span>
    | ์ฝ๋ ์์ญ | ๋ฐ์ดํฐ ์์ญ | ํ ์์ญ | ์คํ ์์ญ |
    | --------- | ----------- | -------------- | --------- |
    | ์์ค ์ฝ๋ | ์ ผ์ญ ๋ณ์ | ๋์  ํ ๋น ๋ณ์ | ์ง์ญ ๋ณ์ |
    | | ์ ์  ๋ณ์ | | ๋งค๊ฐ ๋ณ์ |

![](https://images.velog.io/images/april_5/post/e343beba-ba1c-45ee-9d3f-63f89fd4a721/image.png)

์ฐธ๊ณ ๋ก, `HEAP`๊ณผ `STACK`์์ญ์ ์ฌ์ค ๊ฐ์ ๊ณต๊ฐ์ ๊ณต์ ํ๋ค.
`HEAP`์ด ๋ฉ๋ชจ๋ฆฌ ์์ชฝ ์ฃผ์๋ถํฐ ํ ๋น๋๋ฉด `STACK`์ ์๋์ชฝ๋ถํฐ ํ ๋น๋๋ ์์ด๋ค. ๊ทธ๋์ ๊ฐ ์์ญ์ด ์๋ ๊ณต๊ฐ์ ์นจ๋ฒํ๋ ์ผ์ด ๋ฐ์ํ  ์ ์๋๋ฐ ์ด๋ฅผ ๊ฐ๊ฐ `HEAP OVERFLOW`, `STACK OVERFLOW`๋ผ๊ณ  ์นญํ๋ค.

`Stack` ์์ญ์ด ํฌ๋ฉด ํด ์๋ก `Heap` ์์ญ์ด ์์์ง๊ณ , `Heap` ์์ญ์ด ํฌ๋ฉด ํด์๋ก `Stack` ์์ญ์ด ์์์ง๋ค.

<br/>

---

## โ๏ธ ๋ณ์์ ์ข๋ฅ์ ๋ฉ๋ชจ๋ฆฌ ํ ๋น

### :: ์ ์ญ๋ณ์(Global Variable)

- ์ ์ญ๋ณ์๋ ํ๋ก๊ทธ๋จ์ ์ด๋์๋  ์ ๊ทผ ๊ฐ๋ฅํ ๋ณ์
- ํ๋ก๊ทธ๋จ์ ์์๊ณผ ๋์์ ๋ฉ๋ชจ๋ฆฌ์ ํ ๋น๋๊ณ 
- ํ๋ก๊ทธ๋จ์ ํฌ๊ธฐ๊ฐ ์ปค์ง์๋ก ์ ์ญ๋ณ์๋ก ์ธํด ํ๋ก๊ทธ๋จ์ด ๋ณต์กํด์ง ์ ์๋ค
- ๋ฉ๋ชจ๋ฆฌ์ <span style="color:green">**๋ฐ์ดํฐ(Data) ์์ญ**</span>์ ์ ์ฌ๋๋ค

<br />

### :: ์ง์ญ๋ณ์(Local Variable)

- ํ๋ก๊ทธ๋จ์ ํน์ ํ ๋ธ๋ก(block)/์ค์ฝํ(scope)์์๋ง ์ ๊ทผํ  ์ ์๋ ๋ณ์
- ํจ์๊ฐ ์คํ๋  ๋๋ง๋ค ๋ฉ๋ชจ๋ฆฌ์ ํ ๋น๋์ด ํจ์๊ฐ ์ข๋ฃ๋๋ฉด ๋ฉ๋ชจ๋ฆฌ์์ ํด์ ๋๋ค
- ๋ฉ๋ชจ๋ฆฌ์ <span style="color:hotpink">**์คํ(Stack) ์์ญ**</span>์ ๊ธฐ๋ก๋๋ค

<br />

### :: ์ ์ ๋ณ์(Static Variable)

์ ์ญ๋ณ์์ ์ง์ญ๋ณ์์ ํน์ง์ ๋ชจ๋ ๊ฐ์ง๊ณ  ์๋ค

- ํ๋ก๊ทธ๋จ์ ํน์ ํ ๋ธ๋ก(block)/์ค์ฝํ(scope)์์๋ง ์ ๊ทผํ  ์ ์๋ ๋ณ์
- ํ๋ก๊ทธ๋จ์ด ์คํ๋  ๋ ๋ฉ๋ชจ๋ฆฌ์ ํ ๋น๋์ด ํ๋ก๊ทธ๋จ์ด ์ข๋ฃ๋๋ฉด ๋ฉ๋ชจ๋ฆฌ์์ ํด์ ๋๋ค
- ๋ฉ๋ชจ๋ฆฌ์ <span style="color:green">**๋ฐ์ดํฐ(Data) ์์ญ**</span>์ ๊ธฐ๋ก๋๋ค

```c
#include <stdio.h>

void process() {
	static int a = 5;
    a = a + 1;
    printf("%d\n", a);
}

int main(void) {
	process();   // 6
	process();   // 7
	process();   // 8
	system("pause");
	return 0;
}
```

<br />

### :: ๋ ์ง์คํฐ ๋ณ์(Register Variable)

- ๋ฉ์ธ ๋ฉ๋ชจ๋ฆฌ ๋์  CPU์ ๋ ์ง์คํฐ๋ฅผ ์ฌ์ฉํ๋ ๋ณ์
  - ๋ฉ๋ชจ๋ฆฌ ๋ณด๋ค๋ ๋ ์ง์คํฐ๊ฐ CPU์ ๋ ๊ฐ๊น๊ธฐ ๋๋ฌธ์ ์ฒ๋ฆฌ ์๋๊ฐ ๋น ๋ฅด๋ค
  - ์ฆ, ๋ ์ง์คํฐ ๋ณ์๋ฅผ ์ฌ์ฉํ์ ๋ ์๋์ ์ผ๋ก ์ ๋ฆฌํ๋ค.
- ๋ค๋ง, ๋ ์ง์คํฐ๋ ๋งค์ฐ ํ์ ๋์ด ์์ผ๋ฏ๋ก ์ค์ ๋ก (ํญ์) ๋ ์ง์คํฐ์์ ์ฒ๋ฆฌ๋ ์ง๋ ์ฅ๋ดํ ์ ์๋ค;;;

```c
#include <stdio.h>

int main(void) {
	register int a = 10, i;
	for (i = 0; i < a; i++) {
		printf("%d\n", a);
	}
	system("pause");
	return 0;
}
```

<br />

### :: ํจ์์ ๋งค๊ฐ ๋ณ์๊ฐ ์ฒ๋ฆฌ๋  ๋

- ํจ์๋ฅผ ํธ์ถํ  ๋, ํจ์์ ํ์ํ ๋ฐ์ดํฐ๋ฅผ ๋งค๊ฐ๋ณ์๋ก ์ ๋ฌ
- ์ ๋ฌ ๋ฐฉ์์
  1. `๊ฐ์ ์ํ ์ ๋ฌ ๋ฐฉ์`๊ณผ
  2. `์ฐธ์กฐ์ ์ํ ์ ๋ฌ ๋ฐฉ์`์ด ์๋ค
  - `๊ฐ์ ์ํ ์ ๋ฌ ๋ฐฉ์`์ ๋จ์ง ๊ฐ์ ์ ๋ฌํ๋ฏ๋ก ํจ์ ๋ด์์ ๋ณ์๊ฐ ์๋กญ๊ฒ ์์ฑ๋๋ค โ ๋น์ ํ์๋ฉด ์ง์ญ๋ณ์์ ๊ฐ๋ค
  - `์ฐธ์กฐ์ ์ํ ์ ๋ฌ ๋ฐฉ์`์ ์ฃผ์๋ฅผ ์ ๋ฌํ๋ฏ๋ก ์๋์ ๋ณ์ ์์ฒด์ ์ ๊ทผํ  ์ ์๋ค โ ๋น์ ํ์๋ฉด ์ ์ญ๋ณ์์ ๊ฐ๋ค

#### ๐ ๊ฐ์ ์ํ ์ ๋ฌ ๋ฐฉ์(add ํจ์) ์์

- add ํจ์๋ก ๋ ๊ฐ์ ๊ฐ์ ๋ฃ์ผ๋ฉด ์๋กญ๊ฒ ๋ ๋ณ์๊ฐ ๋ฉ๋ชจ๋ฆฌ ๋ด์ ํ ๋น๋์ด ์ฒ๋ฆฌ
- ๋ฐ๋ผ์ ์๋ ๋ณ์์ ๊ฐ์๋ ์ํฅ์ ๋ฏธ์น์ง ๋ชปํ๋ค

```c
#include <stdio.h>

void add(int a, int b) {
	a = a + b;
	// system("pause"); ํจ์ ๋ด๋ถ์์ ์ถ๋ ฅํ๋ค๋ฉด ๊ฒฐ๊ณผ๊ฐ์ 17
}

int main(void) {
	int a = 7;
	add(a, 10);
	printf("%d\n", a);  // ๊ฐ์ ์ํ ์ ๋ฌ ๋ฐฉ์์ ์ฌ์ฉํ์ผ๋ฏ๋ก ๊ฒฐ๊ณผ๊ฐ์ 7
	system("pause");
	return 0;
}
```

#### ๐ ์ฐธ์กฐ์ ์ํ ์ ๋ฌ ๋ฐฉ์(add ํจ์) ์์

- ๋งค๊ฐ๋ณ์๋ก ๊ฐ์ ์ ๋ฌํ๋ ๊ฒ์ด ์๋, ๋ณ์์ ์ฃผ์ ์ฆ, ๐ํฌ์ธํฐ ๊ฐ์ ์ ๋ฌ
- ์๋ ๋ณ์์ ๊ฐ์ ์ ๊ทผํ์ฌ ๊ฐ์ ๋ณ๊ฒฝํ  ์ ์๋ค

```c
#include <stdio.h>

void add(int *a) {
	(*a) = (*a) + 10;
}

int main(void) {
	int a = 7;
	add(&a);
	printf("%d\n", a);  // 17
	system("pause");
	return 0;
}
```

<br />

---

## ๐ ํฌ์ธํฐ(Pointer)๋?

### ํฌ์ธํฐ์ ๊ฐ๋

- ํฌ์ธํฐ๋ ํน์ ํ ๋ณ์ ์์ฒด๊ฐ ์กด์ฌํ๋ <span style="color:dodgerblue">**๋ฉ๋ชจ๋ฆฌ์ ์ฃผ์์ ๊ฐ**</span>์ ๊ฐ์ง๋ค
  - ๋จ์ํ ์ฃผ์๊ฐ๋ง ์ ์ฅํ๋๊ฒ ์๋, ์ด๋ค ์๋ฃํ์ธ์ง๋ ํฌํจํ์ฌ ์ ์ฅ
    ![](https://images.velog.io/images/april_5/post/dee7f531-a83d-4170-a110-c937d4a113d3/image.png)
- ๋ฐ๋ผ์, ๊ธฐ์กด a๋ฅผ ์ด์ฉํด์๋ 5๋ผ๋ ๊ฐ์ ์ฐพ์ ์ ์์ง๋ง, ํฌ์ธํฐ ๋ณ์์ธ b๋ฅผ ์ด์ฉํด์๋ 5๋ผ๋ ๊ฐ์ ์ฐพ์ ์ ์๋ค.
  ![](https://images.velog.io/images/april_5/post/3bd2ebd6-88f5-4986-99df-8f6cdef6aefc/image.png)

| ์ด๋ฆ                 | ์ค๋ช                                               |
| -------------------- | -------------------------------------------------- |
| ์ฃผ์ ์ฐ์ฐ์(&)       | ๋ณ์ ์์ ๋ถ์ด์ ๋ณ์์ ๋ฉ๋ชจ๋ฆฌ ์์ ์ฃผ์ ๊ฐ์ ๊ตฌํจ |
| ํฌ์ธํฐ(\*)           | ํฌ์ธํฐ ๋ณ์๋ฅผ ์ ์ธํ  ๋ ์ฌ์ฉ                       |
| ๊ฐ์  ์ฐธ์กฐ ์ฐ์ฐ์(\*) | ์ ์ธ๋ ํฌ์ธํฐ ๋ณ์๊ฐ ๊ฐ๋ฆฌํค๋ ๋ณ์๋ฅผ ๊ตฌํจ          |

<br />

### ํฌ์ธํฐ์ ๊ฐ๋ ฅํ ๊ธฐ๋ฅ

- ํฌ์ธํฐ๋ ์ปดํจํฐ ์์คํ์ ํน์ ํ ๋ฉ๋ชจ๋ฆฌ์ ๋ฐ๋ก ์ ๊ทผํ  ์ ์๋ค
- ๋ฐ๋ผ์ ๊ธฐ์กด์ ์กด์ฌํ๋ ์ค์ํ ๋ฉ๋ชจ๋ฆฌ ์์ญ์ ์ ๊ทผํ์ง ์๋๋ก ํด์ผ ํ๋ค
- ์๋์ ์ฝ๋๋ ๊ต์ฅํ ์ํํ ์ฝ๋ ์์์ด๋ค... ๐ฑ๐ฑ

```c
int *a = 0x12345678;
*a = 0;
```

- ๋ค์ค ํฌ์ธํฐ์ ๊ฐ๋๋ ์๋ค. ์์) ํฌ์ธํฐ์ ํฌ์ธํฐ

```c
int *a = 5;
int *b = &a;
int **c = &b;
```

- ๋ฐฐ์ด๊ณผ ํฌ์ธํฐ๋ ์ฌ์ค ๋ด๋ฌด์ ์ผ๋ก ๊ฑฐ์ ๋์ผํ๋ค. ๋ฐฐ์ด์ ์ ์ธํ ์ดํ์๋ ๊ทธ ์ด๋ฆ ์์ฒด๋ฅผ ํฌ์ธํฐ ๋ณ์์ฒ๋ผ ์ฌ์ฉํ  ์ ์๋ค.

<br />

---

### โจ tl;dr

- C์ธ์ด์์๋ ์ ์ญ๋ณ์, ์ง์ญ๋ณ์ ๋ฑ ๋ค์ํ ์ข๋ฅ์ ๋ณ์๊ฐ ์ฌ์ฉ๋๋ค
- ํจ์์ ๋ฐ์ดํฐ๋ฅผ ์ ๋ฌํ๋ ๋ฐฉ๋ฒ์ ๋ ๊ฐ์ง๊ฐ ์๋๋ฐ
  - `๊ฐ์ ์ ๋ฌํ๋ ๋ฐฉ๋ฒ`๊ณผ
  - `์ฃผ์๋ฅผ ์ ๋ฌํ๋ ๋ฐฉ๋ฒ` ์ด๋ค
- ํฌ์ธํฐ๋ ํน์ ํ ๋ณ์๊ฐ ๋ฉ๋ชจ๋ฆฌ ์์ ์กด์ฌํ๋ ์์น ์ฃผ์๋ฅผ ์ ์ฅ.
  - ํน์ ํ ๋ฉ๋ชจ๋ฆฌ ์ฃผ์์ ๋ฐ๋ก ์ ๊ทผํ  ์ ์์ผ๋ฏ๋ก ์กฐ์ฌ์ค๋ฝ๊ฒ ์ฌ์ฉํ์!!
