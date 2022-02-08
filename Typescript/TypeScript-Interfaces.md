# Interfacas

## What are Interfaces
    어떤 타입을 만들어내는 방식

```ts
interface Person1 {
  name: string,
  age: number,
} // 컴파일 타임에 사용 문제가 있는지 관계를 규명해서 체크해 주는 역할

function hello1(person: Person1): void {
  console.log(`안녕하세요! ${person.name} 입니다.`);
}

const p1: Person1 = {
  name: 'Bong',
  age: 29,
};

hello1(p1);
```

## optional property (1) (선택적 프로퍼티)
    항상 꼭 필요한 프로퍼티가 아니고, 상황에 따라서 있을수도 없을수도 있는 프로퍼티

```ts
interface Person2 {
  name: string;
  age?: number; // age는 있을수도 없을수도 있다.
}

function hello2(person: Person2): void {
  console.log(`안녕하세요! ${person.name} 입니다.`);
}

hello2({ name: 'Bong', age: 29 });
hello2({ name: 'Leo' });
```

## optional property (2) (선택적 프로퍼티)
    인덱서블타입(indexable type) - 색인 가능 타입

```ts
interface Person3 {
  name: string;
  age?: number;
  [index: string]: any;
}

function hello3(person: Person3): void {
  console.log(`안녕하세요! ${person.name} 입니다.`);
}

const p31: Person3 = {
  name: 'Bong',
  age: 29,
};

const p32: Person3 = {
  name: 'Leo',
  systers: ['Kim', 'Song'],
};

const p33: Person3 = {
  name: 'Bongjun',
  father: p31,
  mother: p32,
};

hello3(p33);
```

## function in interface

```ts
interface Person4 {
  name: string,
  age: number,
  hello(): void;
}

const p41: Person4 = {
  name: 'Bong',
  age: 29,
  hello: function(): void {
    console.log(`안녕하세요! ${this.name} 입니다.`);
  },
}

const p42: Person4 = {
  name: 'Bong',
  age: 29,
  hello(): void {
    console.log(`안녕하세요! ${this.name} 입니다.`);
  },
}

// const p43: Person4 = {
//   name: 'Bong',
//   age: 29,
//   hello: (): void => {
//     //            error! - typeof globalThis
//     console.log(`안녕하세요! ${this.name} 입니다.`);
//   },
// }

p41.hello(); // 안녕하세요! Bong 입니다.
p42.hello(); // 안녕하세요! Bong 입니다.
```

## class implements interface

```ts
// 컴파일이 되면 사라짐, 컴파일 타임에만 사용
interface IPerson1 {
  name: string;
  age?: number;
  hello(): void;
}

// oop에서 많이 사용
// interface를 class로 사용, IPerson1 내용을 바탕으로 Person이라는 클래스를 만들어냄
class Person implements IPerson1 {
  name: string;
  age?: number | undefined;

  constructor(name: string) {
    this.name = name;
  }

  hello(): void {
    console.log(`안녕하세요! ${this.name} 입니다.`);
  }
}

const person = new Person('Bong');
person.hello();
```

## interface extends interface
    인터페이스들 끼리 상속
```ts
interface IPerson2 {
  name: string;
  age?: number;
}

interface IKorean extends IPerson2 {
  city: string;
}

const k: IKorean = {
  name: '김봉준',
  city: '인천',
};
```

## function interface

```ts
interface HelloPerson {
  (name: string, age?: number): void;
}

const helloPerson: HelloPerson = function(name: string, age: number) {
  console.log(`안녕하세요! ${name} 입니다.`);
} 

helloPerson('Bong', 29);
```

## Reaconly Interface Properties   
    readolny - interface를 만들때 어떤 프로퍼티가 만들어지도 바뀌지 않는 값이라면 readonly를 붙이는 습관 중요
    class 에서도 readonly를 받아다가 유용하게 이용

```ts
interface Person8 {
  name: string;
  age?: number;
  readonly gender: string;
}

const p81: Person8 = {
  name: 'Bong',
  gender: 'male',
}

p81.gender = 'female'; // Cannot assign to 'gender' because it is a read-only property.ts(2540)
```

## type alias vs interface

### function
```ts
// type alias
type EayType = (food: string) => void;

// interface
interface IEat {
  (food: string): void;
}
```

### array
```ts
// type alias
type PersonList = string[];

// interface
interface IPersonList {
  [index: number]: string;
}
```

### intersection
```ts
interface ErrorHandling {
  success: boolean;
  error?: { message: string };
}

interface ArtistsData {
  artists: { name: string } [];
}

// type alias
type ArtistsResponseType = ArtistsData & ErrorHandling;

// interface
interface IArtistsResponse extends ArtistsData, ErrorHandling {}

let art: ArtistsResponseType;
let iar: IArtistsResponse;
```

### union types
```ts
interface Bird {
  fly(): void;
  layEggs(): void;
}

interface Fish {
  swim(): void;
  layEggs(): void;
}

type PetType = Bird | Fish;

interface IPet extends PetType {} // error TS2312: An interface can only extend an object type or intersection of object types with statically known members.

class Pet implements PetType {} // error TS2422: A class can only implement an object type or intersection of object types with statically known members.
```

### Declaration Merging - interface
```ts
interface MergingInterface {
  a: string;
}

interface MergingInterface {
  b: string;
}

let mi: MergingInterface;
mi. // a
    // b
```

### Declaration Merging - type alias
```ts
type MergingType = {
  a: string;
};

type MergingType = { // Duplicate identifier 'MergingType'. ts(2300)
  b: string;
};
```
