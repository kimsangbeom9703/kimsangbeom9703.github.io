---
layout: single
title:  "[NestJS] 04.Typescript"
date:   2025-05-10 10:30:00 +0900
tags: NodeJS NestJS TypeScript
categories: 
- Study
- NodeJS
- NestJS

  
toc: true   #Table Of Contents 목차
toc_sticky: true
---

# [NestJs로 배우는 백엔드 프로그래밍 - 04.Typescript] 


## Typescript
```
TypeScript는 자바스크립트에 타입 시스템을 추가한 프로그래밍 언어로,
코드를 작성할 때 변수, 함수 등의 타입을 명시함으로써 런타임 에러를 줄이고 안정성을 높일 수 있다.

작성된 TypeScript 코드는 컴파일 시 표준 JavaScript 코드로 변환되며,
모든 JavaScript 환경(브라우저, Node.js 등)에서 실행할 수 있다.

정적 타입 검사 덕분에 코드 자동완성, 리팩토링, 협업이 수월해지고,
규모가 큰 프로젝트나 팀 개발에서 특히 효과를 발휘한다.
```

## Typescript 좋은 점

| 특징      | 설명                               |
| ------- | -------------------------------- |
| 타입 검사   | 변수/함수에 잘못된 값을 넣으면 컴파일 타임에 알려줌    |
| 자동 완성   | 어떤 타입인지 명확해서 VSCode에서 추천이 똑똑해짐   |
| 리팩토링 안전 | 변수명 바꾸기, 함수 옮기기 할 때 에러가 잘 잡힘     |
| 협업에 강함  | 어떤 데이터가 오가는지 명확해서 다른 사람이 이해하기 쉬움 |

## 변수 선언
```
[선언키워드] [변수명]: [타입]
```

변수를 선언할 때 const, let, var 세 가지 키워드를 사용할 수 있다

### 🟢 const
한 번 정해진 값을 바꿀 수 없다 (재할당 불가능)
- 값을 변경할 수 없는 "상수(Constant)"를 선언할 때 사용합니다.
- 단, 객체나 배열을 선언한 경우 그 안의 값은 바꿀 수 있어요.
```ts
const name = "Alice";
// name = "Bob"; ❌ 오류! const는 재할당 불가

const user = { age: 20 };
user.age = 21; // ✅ 객체 속성은 변경 가능
```
### 🟡 let
필요할 때 값을 바꿀 수 있어요 (재할당 가능)
- 블록 범위({} 안) 내에서만 유효한 변수를 선언할 때 사용합니다.
- 가장 일반적으로 많이 사용하는 방식입니다.
```ts
let age = 25;
age = 26; // ✅ 가능
```
### 🔴 var
과거 방식. 이제는 거의 쓰지 않아요.
- var는 **함수 범위(function scope)**를 가지며,
- 변수 선언 전에 사용해도 오류가 나지 않는 호이스팅(hoisting) 특징이 있어 예기치 않은 버그를 유발할 수 있어요.
```ts
console.log(msg); // undefined (❗ 선언 전에 사용 가능)
var msg = "Hello";

// let은 선언 전에 사용하면 오류 발생
console.log(title); // ❌ ReferenceError
let title = "Hi";
```
### 📌 호이스팅 차이
```ts
function test() {
  console.log(a); // undefined (var는 끌어올려짐)
  var a = 10;

  // console.log(b); // ❌ ReferenceError (let은 끌어올려지지 않음)
  let b = 20;
}
```
### ✅ 정리표

| 키워드     | 재할당  | 스코프    | 호이스팅            | 사용 권장       |
| ------- | ---- | ------ | --------------- | ----------- |
| `const` | ❌ 불가 | 블록 스코프 | ❌ 안 됨           | ✅ (가능하면 사용) |
| `let`   | ✅ 가능 | 블록 스코프 | ❌ 안 됨           | ✅ 일반 변수에 사용 |
| `var`   | ✅ 가능 | 함수 스코프 | ✅ 됨 (undefined) | ❌ (권장되지 않음) |

## ✅ TypeScript에서 지원하는 주요 타입들

🔹 1. 기본 타입 (Primitive Types)
| 타입          | 설명             | 예시                                  |
| ----------- | -------------- | ----------------------------------- |
| `number`    | 숫자 (정수, 소수 등)  | `let age: number = 30;`             |
| `string`    | 문자열            | `let name: string = "Alice";`       |
| `boolean`   | 참/거짓           | `let isDone: boolean = true;`       |
| `null`      | 값이 없음          | `let data: null = null;`            |
| `undefined` | 정의되지 않음        | `let value: undefined = undefined;` |
| `bigint`    | 큰 정수           | `let big: bigint = 123n;`           |
| `symbol`    | 고유하고 변경 불가능한 값 | `let sym: symbol = Symbol("id");`   |

🔹 2. 배열 (Array)
```ts
let numbers: number[] = [1, 2, 3];
let names: Array<string> = ["Alice", "Bob"];
```
🔹 3. 튜플 (Tuple)
- 고정된 개수와 타입의 배열
```ts
let person: [string, number] = ["Alice", 30];
```
🔹 4. 열거형 (Enum)
- 미리 정의된 상수 값 집합
```ts
enum Direction {
  Up,
  Down,
  Left,
  Right,
}

let dir: Direction = Direction.Up;
```
🔹 5. any
- 어떤 타입이든 가능 (타입 검사 안 함, 되도록 피할 것)
```ts
let anything: any = "hello";
anything = 10;
```
🔹 6. unknown
- any와 비슷하지만, 조작 전에 타입 체크 필요 → 더 안전
```ts
let input: unknown = "hello";
if (typeof input === "string") {
  console.log(input.toUpperCase());
}
```
🔹 7. void
- 주로 함수에서 리턴값이 없을 때 사용
```ts
function logMessage(): void {
  console.log("Hello");
}
```
🔹 8. never
- 절대 리턴하지 않는 함수
```ts
function error(message: string): never {
  throw new Error(message);
}
```
🔹 9. object
- 객체 타입 (단, 구체적 속성을 명시하지 않음)
```ts
let user: object = { name: "Alice" };
```
🔹 10. 유니언 타입 (Union)
- 여러 타입 중 하나
```ts
let id: string | number;
id = "abc";
id = 123;
```
🔹 11. 리터럴 타입 (Literal)
- 특정 값만 허용
```ts
let role: "admin" | "user" = "admin";
```
🔹 12. 타입 별칭 (Type Alias)
```ts
type User = {
  name: string;
  age: number;
};

let u: User = { name: "Alice", age: 30 };
```
🔹 13. 인터페이스 (Interface)
- 객체 타입 구조 정의
```ts
interface Product {
  name: string;
  price: number;
}

const item: Product = { name: "Bag", price: 100 };
```

🔷 제네릭 (Generic) 이란?
```
**"어떤 타입이 들어올지 모르지만, 나중에 정해지는 타입"**을 의미해요.
마치 함수의 매개변수처럼 타입에도 변수를 쓰는 거예요!
```

✅ 왜 필요할까?
- 같은 코드(예: 함수, 클래스)를 여러 타입에 대해 재사용하고 싶을 때
- 타입 안정성(Type Safety)을 유지하면서 재사용성을 높이기 위해 사용한다

🧱 기본 함수 vs 제네릭 함수
```ts
// 일반 함수 (any: 타입 체크 안 됨)
function echoAny(value: any): any {
  return value;
}

// 제네릭 함수
function echo<T>(value: T): T {
  return value;
}

const str = echo<string>("hello"); // str: string
const num = echo<number>(123);     // num: number
```
📦 제네릭 인터페이스
```ts
interface Box<T> {
  item: T;
}

const stringBox: Box<string> = { item: "text" };
const numberBox: Box<number> = { item: 123 };
```
🛠️ 제네릭 타입 제한 (extends 사용)
```ts
function printLength<T extends { length: number }>(value: T) {
  console.log(value.length);
}

printLength("hello");          // ✅ 문자열 (length 있음)
printLength([1, 2, 3]);        // ✅ 배열도 OK
// printLength(123);          // ❌ number에는 length 없음
```
🔧 제네릭 타입 제한 설명
```ts
function printLength<T extends { length: number }>(value: T) {
  console.log(value.length);
}    
```
✅ 1. T extends { length: number }
- T는 타입 변수입니다. (아직 정확한 타입은 모르지만, 나중에 전달됨)
- extends { length: number }는 타입 제한이에요.
    - 즉, T는 반드시 length 속성을 가진 타입이어야 한다는 뜻입니다.
    - 예를 들어 문자열, 배열, length 속성이 있는 객체 등이 이에 해당합니다.

🏗️ 제네릭 클래스
```ts
class DataStore<T> {
  private data: T[] = [];

  add(item: T) {
    this.data.push(item);
  }

  getAll(): T[] {
    return this.data;
  }
}

const store = new DataStore<number>();
store.add(1);
store.add(2);
console.log(store.getAll()); // [1, 2]
```

