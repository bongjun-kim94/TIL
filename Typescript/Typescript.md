# 타입스크립트(Typescript)

    우리가 사용하는 자바스크립트에 타입이라는 개념을 적용시킨 것
    타입을 추가해서 자바스크립트를 확장


## 자바스크립트 vs 타입스크립트

    타입스크립트 : Static Types - 개발하는 중간에 타입을 체크
    자바스크립트 : Dynamic Types - 개발할땐 알 수가 없고 런타임에 들어가야 알수가 있다

```js
// Javascript
function add(n1, n2) {
  if (typeof n1 !== 'number' || typeof n2 !== 'number') {
    throw new Error('Incorrect input!');
  }
  return n1 + n2;
}

const result = add(39, 28);

// Typescript
function add(n1: number, n2: number) {
  return n1 + n2;
}

const result = add(29, 28);
```

- TypeScript에서 프로그램 작성을 위해 기본 제공하는 데이터 타입
- 사용자가 만든 타입은 결국 이 기본 자료형들로 쪼개집니다.
- JavaScript 기본 자료형을 포함(*superset)
  - ECMAScript 표준에 따른 기본 자료형은 6가지
    - Boolean
    - Number
    - String
    - Null
    - Undefined
    - Symbol (ECMAScript 6에 추가)
    - Array: object형

<br />

- 프로그래밍을 도울 타입 제공
  - Any, Void, Never, Unknown
  - Enum
  - Tuple: object형

*superset - A>=B 일때, A는 B의 수퍼셋

## Primitive Type
    오브젝트와 레퍼런스 형태가 아닌 실제 값을 저장하는 자료형
    Primitive의 내장 함수를 사용 가능한것은 자바스크립트 처리 방식 덕분
    (ES2015 기준) 6가지 - boolean, number, string, symbol, null, undefined

// primitive type x object o
new Boolean(false); // typeof new Boolean(false) : 'object';
new String('World'); // typeof new String('World') : 'object';
new Number(42); // typeof new Number(42) : 'object';

TypeScript의 핵심 primite types는 모두 소문자

```js
function reverse(s: String): String {
  return s.split("").reverse().join("");
}

reverse("hello world");

function reverse(s: string): string {
  return s.split("").reverse().join("");
}

reverse("hello world");
```