# 타입스크립트(Typescript)

    우리가 사용하는 자바스크립트에 타입이라는 개념을 적용시킨 것
    타입을 추가해서 자바스크립트를 확장

    자바스크립트에 타입을 부여한 언어다. (확장된 언어)
    기존의 ES5, ES6 문법을 사용할 수 있다.

## 자바스크립트 vs 타입스크립트

    타입스크립트 : Static Types - 개발하는 중간에 타입을 체크
    자바스크립트 : Dynamic Types - 개발할땐 알 수가 없고 런타임에 들어가야 알수가 있다

- Typescript는 동적타입언어인 Javascript의 약점을 보완하기 위해서 타입을 지정해주는 것이다.

- 타입이 필요한 이유는 결론은 메모리를 절약하기 위해서다.

  - 메모리에 저장된 것을 읽어들일때, 값을 메모리에 저장할때, 값이저장되어있는 것을 참조할때의 크기들을 알아야 하기 때문이다.

- 에러를 잡기가 쉬워진다.
- 다른 동료와 협업 할때 코드의 예측도 가능해진다.
- 코드에디터의 도움을 더 받을 수 있다.
- 리액트의 경우 (브라우저는 javascript밖에 모르기떄문에) tsx파일을 javascript로 변환하는 트랜스파일링이 필요하다.
- 이 때 변환하는 과정에서 에러를 잡을 수 가있다. 런타임에 오류를 잡는 것보다 좋다.
  또한, Babel을 안써도 된다.

```js
// Javascript
function sum(a, b) {
  return a + b;
}

// Typescript
function sum(a: number, b: number) {
  return a + b;
}
sum(5, 10);
sum(5, "10"); // 숫자만 넣어야함

let name1 = "bong";
let name2: string = "bong";
```

### 자바스크립트 와의 차이점

    1. 타입을 설정 할 수 있다.
    2. OOP를 사용하기에 더 좋다.
    3. 자바스크립트를 호환하면서 더 많은 기능들과 방식을 이용 할 수 있다.
    4. 자바스크립트는 클라이언트 측 스크립팅 언어이다.
     - 사용자가 웹 브라우저를 열고 웹 페이지를 요청하면 해당 요청이 웹 서버로 이동
    5. 타입스크립트는 객체지향 컴파일 언어다.

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

## 타입 시스템 (Type System)
    1. 컴파일러에게 사용하는 타입을 명시적으로 지정하는 시스템
    2. 컴파일러가 자동으로 타입을 추론하는 시스템

## 타입스크립트의 타입 시스템
    - 타입을 명시적으로 지정할 수 있다.
    - 타입을 명시적으로 지정하지 않으면, 타입스크립트 컴파일러가 자동으로 타입을 추론

## 타입이란 해당 변수가 할 수 잇는 일을 결정합니다.
```js
// JavaScript
// f1 이라는 함수의 body 에서는 a를 사용할 것 입니다.
// a가 할 수 있는 일은 a의 타입이 결정합니다.

function f1(a) {
  return a;
}
```

## 함수 사용법에 대한 오해를 야기하는 자바스크립트
```js
// JavaScript
// (f2 실행의 결과가 NaN을 의도한 것이 아니라면)
// 이 함수의 작성자는 매개변수 a가 number 타입이라는 가정으로 함수를 작성했습니다.

function f2(a) {
  return a * 38;
}

// 사용자는 사용법을 숙지하지 않은채, 문자열을 사용하여 함수를 실행했습니다.
console.log(f2(10)); // 380
console.log(f2('Bong')); // NaN
```

## 타입스크립트의 추론에 의지하는 경우
```js
// 타입스크립트 코드지만,
// a의 타입을 명시적으로 지정하지 않은 경우이기 때문에, a는 any로 추론됩니다.
// 함수의 리턴 타입은 number로 추론됩니다. (NaN도 Number의 하나입니다.)

// 올바른 사용법을 사용자에게 전달하지 못해서 올바르지 못한 함수
function f3(a) {
  return a * 38;
}

// 사용하는 a가 any이기 때문에, 사용법에 맞게 문자열을 사용하여 함수를 실행했습니다.
console.log(f3(10)); // 380
console.log(f3('Bong') + 5); // NaN
```

### noImplicitAny 옵션을 켜면
    타입을 명시적으로 지정하지 않은 경우, 타입스크립트가 추론 중 'any'라고 판단하게 되면, 
    컴파일 에러를 발생시켜 명시적으로 지정하도록 유도한다.

### noImplicitAny에 의한 방어
```js
// error TS 7006: Parameter 'a' implicitly has an 'any' type.
function f3(a) {
  return a * 38;
}

// 사용자의 코드를 실행할 수 없습니다. 컴파일이 정상적으로 마무리 될 수 있도록 수정해야 합니다.
console.log(f3(10));
console.log(f3('Bong') + 5);
```

### number 타입으로 추론된 리턴타입

```js
// 매개변수의 타입은 명시적으로 지정했습니다.
// 명시적으로 지정하지 않은 함수의 리턴 타입은 number로 추론됩니다.

function f4(a: number) {
  if (a > 0) {
    return a * 38;
  }
}

// 사용자는 사용법에 맞게 숫자형을 사용하여 함수를 실행했습니다.
// 해당 함수의 리턴 타입은 number이기 때문에, 타입에 따르면 이어진 연산을 바로 할 수 있습니다.
// 하지만 실제 undefined + 5가 실행되어 NaN이 출력됩니다.

console.log(f4(5)); // 190
console.log(f4(-5) + 5); // NaN
```

### strickNullChecks 옵션을 켜면

    모든 타입에 자동으로 포함되어 있는 'null'과 'undefined'를 제거해줍니다.

### number | undefined 타입으로 추론된 리턴타입

```js
// 매개변수의 타입은 명시적으로 지정했습니다.
// 명시적으로 지정하지 않은 함수의 리턴 타입은 number | undefined로 추론됩니다.

function f4(a: number) {
  if (a > 0) {
    return a * 38;
  }
}

// 사용자는 사용법에 맞게 숫자형을 사용하여 함수를 실행했습니다.
// 해당 함수의 리턴 타입은 number | undefined 이기 때문에, 타입에 따르면 이어진 연산을 바로 할 수 없습니다.
// 컴파일 에러를 고쳐야하지 때문에 사용자와 작성자가 의논을 해야합니다.

console.log(f4(5));
console.log(f4(-5) + 5); // error TS2532: Object is possibly 'undefined'.
```

### 명시적으로 리턴 타입을 지정해야할까?
```js
// 매개변수의 타입과 함수의 리턴 타입을 명시적으로 지정했습니다.
// 실제 함수 구현부의 리턴 타입과 명시적으로 지정한 타입이 일치하지 않아 컴파일 에러가 발생합니다.

// error TS2366: Function lacks ending return statement and return type does not include 'undefined'.
function f5(a: number): number {
  if (a > 0) {
    return a * 38;
  }
}
```

### noInplicitReturns 옵션을 켜면
    함수 내에서 모든 코드가 값을 리턴하지 않으면, 컴파일 에러를 발생시킨다.

    모든 코드에서 리턴을 직접해야 한다.
    
    // if가 아닌경우 return을 직접하지 않고 코드가 종료된다.

    // error TS7030: Not all code paths return a value.
    function f5(a: number) {
      if (a > 0) {
        return a * 38;
      }
    }
    // if가 아닌경우 리턴을 하지 않을경우 undefined가 추론

### 매개변수에 object가 들어오는 경우
```js
// JavaScript
function f6(a) {
  return `이름은 ${a.name} 이고, 연령대는 ${Math.floor(a.age / 10) * 10} 대 입니다.`;
}

console.log(f6({ name: 'Bong', age: 29 })); // 이름은 Bong 이고, 연령대는 20대 입니다.
console.log(f6('Bong')); // 이름은 undefined 이고, 연령대는 NaN대 입니다.
```

### object literal type

```js
// JavaScript
function f7(a: { name: string; age: number }): string {
  return `이름은 ${a.name} 이고, 연령대는 ${Math.floor(a.age / 10) * 10} 대 입니다.`;
}

console.log(f7({ name: 'Bong', age: 29 })); // 이름은 Bong 이고, 연령대는 20대 입니다.
console.log(f7('Bong')); // error TS2345: Argument of type 'string' is not assignable to parameter to parameter of type '{ name: string; age: number; }'.
```

### 나만의 타입을 만드는 방법

```ts
interface Personinterface {
  name: string;
  age: number;
}

type PersonTypeAlias = {
  name: string;
  age: number;
};

function f8(a: PersonInterface): string {
  return `이름은 ${a.name} 이고, 연령대는 ${Math.floor(a.age / 10) * 10}대 입니다.`;
}

console.log(f8({ name: 'Bong', age: 29})); // 이름은 Bong 이고, 연령대는 20대 입니다.
console.log(f8('Bong')); // error TS2345: Argument of type 'string' is not assignable to parameter of type 'PersonInterface'.
```

### Structural Type System vs Nominal Type System
    타입스크립트는 structural type system을 따르고 있다.
    structural type system - 구조가 같으면, 같은 타입이다.
```ts
interface IPerson {
  name: string;
  age: number;
  speak(): string;
}

type PersonType = {
  name: string;
  age: number;
  speak(): string;
}

let personInterface: IPerson = {} as any;
let personType: PersonType = {} as any;

personInterface = personType;
personType = personInterface;
```
    nominal type system - 구조가 같아도 이름이 다르면 다른 타입이다.
    타입스크립트가 따르지 않음

```ts
type PersonID = string & { readonly brand: unique symbol };

function PersonID(id: string): PersonID {
  return id as PersonID;
}

function getPersonById(id: PersonID) {}

getPersonById(PersonId('id-aaaaaa'));
getPersonById('id-aaaaaa'); // error TS2345: Argument of type 'string' is not assignable to parameter of type 'PersonID'. Type 'string' is not assignable to type '{ readonly brand: unique symbol; }'.
```

    duck typing
    런타임에 발생하는 타이핑 방식
    만약 어떤 새가 오리처럼 걷고, 헤엄치고, 꽥꽥거리는 소리를 낸다면 나는 그 새를 오리라고 부를 것이다.
    타입스크립트는 duck typing이 아니다

```python
class Duck:
  def sound(self):
    print u"꽥꽥"

class Dog:
  def sound(self):
    print u"멍멍"

def get_sound(animal):
  animal.sound()

def main():
  bird = Duck()
  dog = Dog()
  get_sound(bird)
  get_sound(dog)
```

### 타입 호환성 (Type Compatibility)

#### 서브타입(1)
```ts
// sub1 타입은 sup1 타입의 서브 타입이다.
let sub1: 1 = 1;
let sup1: number = sub1; // sup1에는 sub1을 넣을 수 있고 그 반대는 에러가 난다.
sub1 = sup1; // error! Type 'number' is not assignable to type '1'.

// sub 타입은 sup2 타입의 서브 타입이다.
let sub2: number[] = [1];
let sup2: object = sub2;
sub2 = sup2; // error! Type '{}' is missing the following properties from type 'number[]': length, pop, push, concat, and 16 more. 
// sub2가 더 작기 때문에 에러

// sub3 타입은 sup3 타입의 서브 타입이다.
let sub3: [number, number] = [1, 2];
let sup3: number[] = sub3;
sub3 = sup3; // error! Type 'number[]' is not assignable to type '[number, number]'. Target requires 2 element(s) but source my have fewer.
```

#### 서브타입(2)
```ts
// sub4 타입은 sup4 타입의 서브 타입이다.
let sub4: number = 1;
let sup4: any = sub4;
sub4 = sup4;

// sub5 타입은 sup5 타입의 서브 타입이다.
let sub5: never = 0 as never;
let sup5: number = sub5;
sub5 = sup5; // error! Type 'number' is not assignable to type 'never'.

class Animal {}
class Dog extends Animal {
  eat() {}
}

// sub6 타입은 sup6 타입의 서브 타입이다.
let sub6: Dog = new Dog();
let sup6: Animal = sub6;
sub6 = sup6; // error! Property 'eat' is missing in type 'SubAnimal' but required in type 'subDog'.
```

1. 같거나 서브 타입인 경우, 할당이 가능하다. => 공변
```ts
// primitive type, 공변
let sub7: string = '';
let sup7: string | number = sub7;

// object - 각각의 프로퍼티가 대응하는 프로퍼티와 같거나 서브타입이어야 한다.
let sub8: { a: string; b: number } = { a: '', b: 1 };
let sup8: { a: string | number; b: number } = sub8;

// array - object 와 마찬가지
let sub9: Array<{ a: string; b: number }> = [{ a: '', b: 1 }];
let sup9: Array<{ a: string | number; b: number }> = sub8;
```

2. 함수의 매개변수 타입만 같거나 슈퍼타입인 경우, 할당이 가능하다. => 반병
```ts
class Person {}
// Person을 상속받은 Developer라는 클래스
class Developer extends Person {
  coding() {}
}
class StartupDeveloper extends Developer {
  burning() {}
}

function tellme(f: (d: Developer) => Developer) {}

// Developer => Developer 에다가 Developer => Developer를 할당하는 경우
tellme(function dToD(d: Developer): Developer) {
  return new Developer();
});

// Developer => Developer 에다가 Person => Developer를 할당하는 경우
tellme(function pToD(d: Person): Developer {
  return new Developer();
});

// Developer => Developer 에다가 StartipDeveloper => Developer를 할당하는 경우
tellme(function sToD(d: StartupDeveloper): Developer {
  return new Developer();
});
```

    strictFunctionTypes 옵션을 켜면
    함수를 할당할 시에 함수의 매개변수 타입이 같거나 슈퍼타입인 경우가 아닌 경우, 에러를 통해 경고한다.

### 타입 별칭 (Type Alias)
    타입 별칭 (별명)
    - interface랑 비슷해 보입니다.
    - Primitive, Union Type, Tuple, Function
    - 기타 직접 작성해야하는 타입을 다른 이름을 지정할 수 있습니다.
    - 만들어진 타입의 refer로 사용하는 것이지 타입을 만드는것은 아닙니다.

#### Aliasing Primitive
```ts
type MyStringType = string;
const str = 'world';
let myStr: MyStringType = 'hello';
myStr = str;
```

#### Aliasing Union Type - 제일 많이 쓰이는 형태
```ts
let person: string | number = 0;
person = 'Bong';

// string | number 라는 타입을 만든후 별칭을 StringOrNumber로 가르킴
type StringOrNumber = string | number;

let another: StringOrNumber = 0;
another = 'Anna';

// 1. 유니온 타입은 A도 가능하고 B도 가능한 타입
// 2. 길게 쓰는걸 짧게

```

#### Aliasing Tuple
```ts
let person: [string, number] = ['Bong', 29];

type PersonTuple = [string, number];

let another: PersonTuple = ['Anna', 25];

// 튜플 타입에 별칭을 줘서 여러군데서 사용할 수 있게 한다.
```

#### Aliasing Function
```ts
type EatType = (food: string) => void;
```

    어떤 타입이 그 타입으로써 목적이나 존재가치가 명확하면 interface
    어떠한 대상을 가르키거나 별명으로써만 존재한다면 type alias