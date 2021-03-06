---
title: "π«TS:: β¨κ°λ ₯ν Interface!"
tags:
  - [Typescript]
permalink: /study/TS/interface

navigation: true
toc: true
toc_sticky: true

date: 2022-02-06
last_modified_at: 2022-02-06
---

![](https://images.velog.io/images/april_5/post/fef3266f-5808-4e74-a394-3cc0c8bd35a3/typescript.png)

TypeScriptμ ν΅μ¬ μμΉ μ€ νλλ νμ κ²μ¬κ° <span style='color:dodgerblue'>**κ°μ ννμ μ΄μ **</span>μ λ§μΆκ³  μλ€λ κ²μΈλ°, TypeScriptμμ, [μΈν°νμ΄μ€](https://www.typescriptlang.org/docs/handbook/interfaces.html)(`interface`)λ

- μ΄λ° νμλ€μ μ΄λ¦μ μ§λ μ­ν μ νκ³ 
- μ½λ μμ κ³μ½μ μ μνλ κ²λΏλ§ μλλΌ
- νλ‘μ νΈ μΈλΆμμ μ¬μ©νλ μ½λμ κ³μ½μ μ μνλ κ°λ ₯ν λ°©λ²μ΄λ€.

<br />

---

## μ²« λ²μ§Έ μΈν°νμ΄μ€ (Our First Interface)

μ΄λ»κ² μΈν°νμ΄μ€κ° λμνλμ§ νμΈνλ κ°μ₯ μ¬μ΄ λ°©λ²μ κ°λ¨ν μμ λ‘ νμΈνκΈ°!

```ts
// interface μ¬μ© μ 
// printLabel ν¨μλ string νμ labelμ κ°λ κ°μ²΄λ₯Ό νλμ λ§€κ°λ³μλ₯Ό κ°λλ€
function printLabel(labeledObj: { label: string }) {
  console.log(labeledObj.label);
}

let myObj = { size: 10, label: "Size 10 Object" };
printLabel(myObj);

// interface μ¬μ© ν
// λ¬Έμμ΄ νμμ νλ‘νΌν° labelμ κ°μ§ μΈν°νμ΄μ€λ‘ μμ±
interface LabeledValue {
  label: string;
}

function printLabel(labeledObj: LabeledValue) {
  console.log(labeledObj.label);
}

let myObj = { size: 10, label: "Size 10 Object" };
printLabel(myObj);
```

<br />

## Optional Properties

μΈν°νμ΄μ€μ λͺ¨λ  νλ‘νΌν°κ° νμν κ²μ μλλ€. <span style='color:mediumslateblue'>**μ΄λ€ μ‘°κ±΄μμλ§ μ‘΄μ¬νκ±°λ μμ μμ μ**</span>λ μλ€.

μ νμ  νλ‘νΌν°λ€μ κ°μ²΄ μμ λͺ κ°μ νλ‘νΌν°λ§ μ±μ ν¨μμ μ λ¬νλ "option bags" κ°μ ν¨ν΄μ λ§λ€ λ μ μ©νλ€!

```ts
interface PaintOptions {
  shape: Shape;
  xPos?: number;
  yPos?: number;
}

function paintShape(opts: PaintOptions) {
  // ...
}

const shape = getShape();
paintShape({ shape });
paintShape({ shape, xPos: 100 });
paintShape({ shape, yPos: 100 });
paintShape({ shape, xPos: 100, yPos: 100 });
```

<br />

---

## Readonly properties

μΌλΆ νλ‘νΌν°λ€μ <span style='color:mediumseagreen'>**κ°μ²΄κ° μ²μ μμ±λ  λλ§ μμ  κ°λ₯**</span>ν΄μΌ ν  λ μ¬μ©.

```ts
interface Point {
  readonly x: number;
  readonly y: number;
}

let p1: Point = { x: 10, y: 20 };
p1.x = 5; // μ€λ₯!
```

<br />

---

## μΈλ±μ€ νμ (Index Types)

μΈν°νμ΄μ€μμ <span style='color:blueviolet'>**μμ± μ΄λ¦μ κ΅¬μ²΄μ μΌλ‘ μ μνμ§ μκ³  κ°μ νμλ§ μ μνλ κ²**</span>μ μΈλ±μ€ νμμ΄λΌ νλ€.

```ts
interface SquareConfig {
  color?: string;
  width?: number;
  [propName: string]: any;
}

let squareOptions = { color: "red", width: 100 };
let mySquare = createSquare(squareOptions);
```

<br />

---

## Extending Types

ν΄λμ€μ²λΌ, μΈν°νμ΄μ€λ€λ <span style='color:lightseagreen'>**νμ₯(extend)μ΄ κ°λ₯**</span>νλ€.

νμ₯(extend)μ <span style='color:mediumseagreen'>**ν μΈν°νμ΄μ€μ λ©€λ²λ₯Ό λ€λ₯Έ μΈν°νμ΄μ€μ λ³΅μ¬**</span>νλ κ²μ κ°λ₯νκ² ν΄μ£Όλλ°, μ¬μ¬μ©μ± λμ μ»΄ν¬λνΈλ‘ μͺΌκ°€ λ μ μ°νκ² ν  μ μλ€.

```ts
// μμ  1
interface BasicAddress {
  name?: string;
  street: string;
  city: string;
  country: string;
  postalCode: string;
}

interface AddressWithUnit extends BasicAddress {
  unit: string;
}

// μμ  2
interface Colorful {
  color: string;
}

interface Circle {
  radius: number;
}

interface ColorfulCircle extends Colorful, Circle {}

const cc: ColorfulCircle = {
  color: "red",
  radius: 42,
};
```

<br />

---

## κ΅μ°¨ νμ (Intersection Types)

`interfaces`λ₯Ό μ¬μ©νλ©΄ <span style='color:mediumseagreen'>**λ€λ₯Έ μ νμ νμ₯νμ¬ λ€λ₯Έ μ νμμ μ μ νμ κ΅¬μΆ**</span>ν  μ μλ€. Intersection Typesμ `&`μ°μ°μλ₯Ό μ¬μ©νμ¬ μ μνλ€.

```ts
interface Colorful {
  color: string;
}
interface Circle {
  radius: number;
}

type ColorfulCircle = Colorful & Circle;
```

<br /><br />

μ°Έκ³  μλ£: [typescript-kr.github.io](https://typescript-kr.github.io/pages/interfaces.html)

<br /><br />
