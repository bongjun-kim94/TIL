# TypeScript Generics

    제네릭이란 타입을 마치 함수의 파라미터처럼 사용하는 것을 의미합니다.

- 제네릭(Generic)이란? -타입을 마치 함수의 파라미터처럼 사용하는 것

  - 제네릭(Generics)은 클래스 또는 함수에서 사용할 타입(Type)을, 그
  - 클래스나 함수를 사용할 때 결정하는 프로그래밍 기법을 말한다.
  - JavaScript와 같은 동적 타입 언어만 주로 다루던 개발자에게는 생소한 개념이다.
  - TypeScript는 정적 타입 언어라 제네릭을 지원한다.

- 제네릭(Generic) 사용이유
  - 함수의 인자로 어떤 타입이 들어갔고 어떤 값이 반환되는지는 알 수가 없습니다.
  - 한 가지 타입보다 여러 가지 타입에서 동작하는 컴포넌트를 생성하는 데 사용된다.
  - 재사용성이 높은 함수와 클래스를 생성할 수 있다.
  - 여러 타입에서 동작이 가능하다. (한 번의 선언으로 다양한 타입에 재사용할 수 있다.)
  - 코드의 가독성이 향상된다.
  - 오류를 쉽게 포착할 수 있다.
  - any타입을 사용하면 컴파일 시 타입을 체크하지 않는다.
  - 타입을 체크하지 않아 관련 메서드의 힌트를 사용할 수 없다.
  - 컴파일 시에 컴파일러가 오류를 찾지 못한다.
  - generic도 any처럼 타입을 지정하지 않지만, 타입을 체크해 컴파일러가 오류를 찾을 수 있다.

## Generics, Any와 다른점

```ts
function heeloString(message: string): string {
  return message;
}

function helloNumber(message: number): number {
  return message;
}

// 더 많은 반복된 함수들...

function hello(message: any): any {
  return message;
}

console.log(hello("Bong").length); // 4

//                                   결과물을 T로 리턴
function helloGeneric<T>(message: T): T {
  return message; // T로 들어온 message를 리턴하기 때문에 리턴타입은 T라고 해도 지장없음
}

console.log(helloGeneric("Bong").length); // 4
console.log(helloGeneric(29)); // 29
console.log(helloGeneric(true)); // true
```

## Generics Basic

```ts
function helloBasic<T, U>(message: T, comment: U): T {
  return message;
}

// 직접 지정할때는 지정된 타입으로 체킹
helloBasic<string, number>("Bong", 29);
// 지정하지 않으면 각각 추론된다.
helloBasic(29, 29);
```

## Generics Array & Tuple

```ts
// T를 받고 T[] - 배열로 받겠다는 표시, 리턴 타입도 T
function helloArray<T>(message: T[]): T {
  return message[0];
}

helloArray(["Hello", "World"]);
helloArray(["Hello", 5]);

function helloTuple<T, K>(message: [T, K]): T {
  return message[0];
}

helloTuple(["Hello", "World"]);
helloTuple(["Hello", 5]);
```

## Generics Function

```ts
// type alias
type HelloFunctionGeneric1 = <T>(message: T) => T;

const helloFunction1: HelloFunctionGeneric1 = <T>(message: T): T => {
  return message;
};

// interface
interface HelloFunctionGeneric2 {
  <T>(message: T): T;
}

const helloFunction2: HelloFunctionGeneric2 = <T>(message: T): T => {
  return message;
};
```

## Generics Class

```ts
class Person<T, K> {
  private _name: T;
  private _age: K;

  constructor(name: T, age: K) {
    // 생성자에 들어온 name으로 할당
    this._name = name;
    this._age = age;
  }
}

new Person("Bong", 29);
// new Person<string>(29); // Error!
new Person<string, number>("Bong", "age"); // number 자리에 문자열이 들어와서 Error!
```

## Generics with extends

제네릭으로 사용할때는 상속이라는 개념보다는 다른 특별한 의미로 사용됨

```ts
// extends라는 키워드를 통해서 제네릭을 제한
class PersonExtends<T extends string | number> {
  private _name: T;

  constructor(name: T) {
    this._name = name;
  }
}

new PersonExtends("Bong");
new PersonExtends(29);
new PersonExtends(true);
```

## keyof & type lookup system

keyof 키워드와 generic을 이용해서 타입을 적절히 찾아내고 활용할 수 있는 시스템(컴파일 타임에 타입을 찾아낼 수 있는 방식)

```ts
interface IPerson {
  name: string;
  age: number;
}

// 이 변수는 IPerson 타입을 표현
const person: IPerson = {
  name: "Bong",
  age: 29,
};

// keyof 키워드는 type 앞에 붙여서 새로운 type을 만들어냄
// type Keys = keyof IPerson;

// const Keys: Keys = "name";

// 특정한 개체를 받기위해 obj라 지정,
// obj에 해당하는 name 이라는 것 혹은 age라 하는 것을 key로 받도록한다
// function getProp(obj: IPerson, key: "name" | "age"): string | number {
// IPerson[keyof IPerson]
// => IPerson["name" | "age"]
// => IPerson["name"] | IPerson["age"]
// => string | number
// function getProp(obj: IPerson, key: keyof IPerson): IPerson[keyof IPerson] {
//   return obj[key];
// }
function getProp<T, K extends keyof T>(obj: T, key: K): T[K] {
  return obj[key];
}

// key는 IPerson으로 추론
getProp(person, "name");

function setProp<T, K extends keyof T>(
  obj: T,
  key: keyof T,
  value: T[keyof T]
): void {
  // 유니온 타입이 아니기 떄문에 에러가 나지 않음
  obj[key] = value;
}

setProp(person, "name", "Lee");
```
