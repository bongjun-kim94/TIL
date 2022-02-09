# TypeScript Classes

## What are Classes
- 클래스 === 객체
- object를 만드는 blueprint (청사진, 설계도)
- 클래스 이전에 object를 만드는 기본적인 방법은 function
- JavaScript에도 class는 es6 부터 사용 가능
- OOP을 위한 초석
- TypeScript 에서는 클래스도 사용자가 만드는 타입의 하나

## Quick Start - Class

- class 키워드를 이용하여 클래스를 만들 수 있다.
- class 이름은 보통 대문자를 이용한다.
- new를 이용하여 class를 통해 object를 만들 수 있다.
- constructor를 이용하여 object를 생성하면서 값을 전달할 수 있다.
- this를 이용해서 만들어진 object를 가리킬 수 있다.
- JS로 컴파일되면 es5의 경우 function으로 변경된다.

## constructor & initialize

- 생성자 함수가 없으면, 디폴트 생성자가 불린다.
- 프로그래머가 만든 생성자가 하나라도 있으면, 디폴트 생성자는 사라진다.
- strict 모드에서는 프로퍼티를 선언하는 곳 또는 생성자에서 값을 할당해야 한다.
- 프로퍼티를 선언하는 곳 또는 생성자에서 값을 할당하지 않는 경우에는 !를 붙여서 위험을 표현한다.
- 클래스의 프로퍼티가 정의되어 있지만, 값을 대입하지 않으면 undefined 이다.
- 생성자에는 async를 설정할 수 없다.

## 접근 제어자 (Access Modifiers)

    클래스 내부에는 생성자, 프로퍼티, 메소드의 접근 제어자를 붙여서 외부에서 접근할 수 있는지, 상속간에 접근할 수 있는지, 내부에서 만 접근할 수 있는지 설정

- 접근 제어자에는 public, private, protected가 있다.
- 설정하지 않으면 public이다.
- 클래스 내부의 모든 곳에 (생성자, 프로퍼티, 메소드) 설정 가능하다.
- private으로 설정하면 클래스 외부에서 접근할 수 없다.
- 자바스크립트에서 private 지원하지 않아 오랫동안 프로퍼티나 메서드 이름 앞에 _를 붙여서 표현했다.

```ts
class Person {
  public name: string = "Bong";
  private _age!: number;

  public constructor(age?: number) {
    if (age === undefined) {
      this.age = 20;
    } else {
      this.age = age;
    }
  }
  public async init() {
  }
}

const p1: Person = new Person(29);
console.log(p1);
console.log(p1.age);
```

## initialization in constructor parameters
    생성자의 파라미터를 받아서 그 클래스의 프로퍼티로 초기화하는 방법

```ts
class Person {
  // public constructor(public name: string, private age: number) {}
  // this.name, this.age 이렇게 사용 대신 대체 가능
  public constructor(public name: string, private age: number) {}
}

const p1: Person = new Person("Bong",29);
console.log(p1); // Person { name: 'Bong', age: 29 }
console.log(p1.name);
```

## Getters & Setters

```ts
class Person {
  public constructor(private _name: string, private age: number) {}

  get name() {
    // 
    // console.log("get");
    return this._name + "Kim";
  }

  // set name(n: string) {
  //   console.log("set");
  //   this._name = n;
  // }
}

const p1: Person = new Person("Bong", 29);
console.log(p1.name); // get을 하는 함수를 getter
p1.name = "Bongjun"; // set - 설정해주는 일, set을 하는 함수를 setter
// p1.name = "Bongjun"; // 이 데이터는 읽기만 가능해! 같은 상황을 연출할 수 있음
console.log(p1.name);
```

## readonly properties

    setting은 할수없고 get만 할수 있는 형태

    readonly가 키워드가 달려있는 경우에는 퍼블릭이던 프라이빗이던 초기화 되는 영역에서만 값을 세팅가능 다른곳에서는 다른값으로 변경 불가

```ts
class Person {
  public readonly name: string = "Bong";
  private readonly country: string;

  public constructor(private _name: string, private age: number) {
    this.country = "Korean";
  }

  hello() {
    this.country = "USA";
  }
}

const p1: Person = new Person("Bong", 29);
console.log(p1.name); // get을 하는 함수 getter
p1.name = "Bongjun"; // set을 하는 함수 setter
console.log(p1.name);
```

## Index Signatures in class

    class => object
    {bong: 'male', jade: 'male'}
    {chloe: 'female', alex: 'male', anna: 'female'}

```ts
class Students {
  // 어떤 프로퍼티 이름인진 모르지만 항상 male이나 female값이 있어야 한다
  [index: string]: "male" | "female";

  bong: "male" = "male";
}

const a = new Students();
a.bong = "male";
a.jade = "male";

console.log(a); // Students { bong: 'male', jade: 'male' }

const b = new Students();
b.chloe = "female";
b.alex = "male";
b.anna = "female";

console.log(b); // {chloe: 'female', alex: 'male', anna: 'female'}

```

## Static Properties & Methods

```ts
class Person {
  private static CITY = "Seoul";
  public hello() {
    console.log("안녕하세요", Person.CITY);
  }
  public change() {
    Person.CITY = 'LA';
  }
}

const p1 = new Person();
p1.hello();

const p2 = new Person();
p2.hello();
p1.change();
p2.hello();

Person.hello();
```

## Singletons

    어플리케이션이 실행되는 중간에 클래스로부터 단 하나의 오브젝트만 생성해서 사용하는 패턴

```ts
class ClassName {
  private static instance: ClassName | null = null;
  public static getInstance(): ClassName {
    // ClassName으로 부터 만든 object가 있으면 그걸 리턴
    // 없으면 만들어서 리턴

    if (ClassName.instance === null) {
      ClassName.instance = new ClassName();
    }
    return ClassName.instance;
  }
  // private new를 직접 호출할 수 없는 상태로 만듬 
  private constructor() {}
}

// 각각 다른 오브젝트 생성
const a = ClassName.getInstance();
const b = ClassName.getInstance();
console.log(a === b); // true
```

## 상속(Inheritance)

    클래스가 다른 클래스를 가져다가 자신만의 기능을 추가하여 사용하는것

```ts
class Parent {
  // protected - 접근 제어자, public 처럼 외부에서 접근할 수 없지만 상속관계에 있는 관계에서만 접근 가능
  constructor(protected _name: string, private _age: number) {}

  // public - 외부에서 사용가능
  public print(): void {
    console.log(`이름은 ${this._name}  이고, 나이는 ${this._age} 입니다.`);
    // 이름은 Bong  이고, 나이는 29 입니다.
    // 이름은 Bong jun.  이고, 나이는 1 입니다.
  }

  protected printName(): void {
    console.log(this._name, this._age); // Bong jun. 1
  }
}

// const p = new Parent('Bong', 29);
// p.print();

// Parent라는 클래스를 상속받을때 extends라는 키워드를 사용, Parent의 생성자를 그대로 가져옴, 생성자가 있다면 Child에서도 같은 형태로 불러줘야함
class Child extends Parent {
  public gender = "male";

  constructor(age: number) {
    // 자식의 생성자에서는 무조건 super를 먼저 호출
    super('Bong jun.', age);

    // constructor 안에서 this.무엇을 호출하려면 무조건 super을 먼저 호출해야함
    this.printName();

  }
}

const c = new Child(1);
c.print();
```

## Abstract Classes

    Abstract키워드를 사용하면 완전하지 않은 클래스를 표현할 수 있고, 완전하지 않은 클래스는 new를 이용해서 개체로 만들어 낼수 없습니다. 그렇기 때문에 완전하지 않은 개체를 상속과 같은 기능을 이용해서 완전하게 만든다음 사용할 수 있도록 안내

```ts
abstract class AbstractPerson {
  protected _name: string = "Bong";

  // abstract 키워드를 붙였기 때문에 구현하지 않음 - {} x 
  abstract setName(name: string): void;
}

// abstract가 붙어있는 class는 기능이 완전하지 않기 때문에, new로 무언가를 할 수가 없습니다.
// new AbstractPerson();

class Person extends AbstractPerson {
  setName(name: string): void {
    this._name = name;
  }
}

const p = new Person();
p.setName();

// abstract 키워드가 사용된 class는 new로 생성할 수 없고, 
// abstract 키워드가 사용된 클래스를 상속하면, 
// abstract 키워드가 붙은 함수를 구현해야한다.
```