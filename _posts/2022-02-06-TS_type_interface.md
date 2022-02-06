---
title: "💫TS:: ✨강력한 Interface!"
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

TypeScript의 핵심 원칙 중 하나는 타입 검사가 <span style='color:dodgerblue'>**값의 형태에 초점**</span>을 맞추고 있다는 것인데, TypeScript에서, [인터페이스](https://www.typescriptlang.org/docs/handbook/interfaces.html)(`interface`)는

- 이런 타입들의 이름을 짓는 역할을 하고
- 코드 안의 계약을 정의하는 것뿐만 아니라
- 프로젝트 외부에서 사용하는 코드의 계약을 정의하는 강력한 방법이다.

<br />

---

## 첫 번째 인터페이스 (Our First Interface)

어떻게 인터페이스가 동작하는지 확인하는 가장 쉬운 방법은 간단한 예제로 확인하기!

```ts
// interface 사용 전
// printLabel 함수는 string 타입 label을 갖는 객체를 하나의 매개변수를 갖는다
function printLabel(labeledObj: { label: string }) {
  console.log(labeledObj.label);
}

let myObj = { size: 10, label: "Size 10 Object" };
printLabel(myObj);

// interface 사용 후
// 문자열 타입의 프로퍼티 label을 가진 인터페이스로 작성
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

인터페이스의 모든 프로퍼티가 필요한 것은 아니다. <span style='color:mediumslateblue'>**어떤 조건에서만 존재하거나 아예 없을 수**</span>도 있다.

선택적 프로퍼티들은 객체 안의 몇 개의 프로퍼티만 채워 함수에 전달하는 "option bags" 같은 패턴을 만들 때 유용하다!

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

일부 프로퍼티들은 <span style='color:mediumseagreen'>**객체가 처음 생성될 때만 수정 가능**</span>해야 할 때 사용.

```ts
interface Point {
  readonly x: number;
  readonly y: number;
}

let p1: Point = { x: 10, y: 20 };
p1.x = 5; // 오류!
```

<br />

---

## 인덱스 타입 (Index Types)

인터페이스에서 <span style='color:blueviolet'>**속성 이름을 구체적으로 정의하지 않고 값의 타입만 정의하는 것**</span>을 인덱스 타입이라 한다.

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

클래스처럼, 인터페이스들도 <span style='color:lightseagreen'>**확장(extend)이 가능**</span>하다.

확장(extend)은 <span style='color:mediumseagreen'>**한 인터페이스의 멤버를 다른 인터페이스에 복사**</span>하는 것을 가능하게 해주는데, 재사용성 높은 컴포넌트로 쪼갤 때 유연하게 할 수 있다.

```ts
// 예제 1
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

// 예제 2
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

## Intersection Types

`interfaces`를 사용하면 <span style='color:mediumseagreen'>**다른 유형을 확장하여 다른 유형에서 새 유형을 구축**</span>할 수 있다. Intersection Types은 `&`연산자를 사용하여 정의한다.

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

참고 자료: [typescript-kr.github.io](https://typescript-kr.github.io/pages/interfaces.html)

<br /><br />
