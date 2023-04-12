### Typescript Generic

- 제네릭(Generic)이란?

  - 제네릭(Generics)은 클래스 또는 함수에서 사용할 타입(Type)을, 그
  - 클래스나 함수를 사용할 때 결정하는 프로그래밍 기법을 말한다.
  - JavaScript와 같은 동적 타입 언어만 주로 다루던 개발자에게는 생소한 개념이다.
  - TypeScript는 정적 타입 언어라 제네릭을 지원한다.

- 제네릭(Generic) 사용이유
  - 한 가지 타입보다 여러 가지 타입에서 동작하는 컴포넌트를 생성하는 데 사용된다.
  - 재사용성이 높은 함수와 클래스를 생성할 수 있다.
  - 여러 타입에서 동작이 가능하다. (한 번의 선언으로 다양한 타입에 재사용할 수 있다.)
  - 코드의 가독성이 향상된다.
  - 오류를 쉽게 포착할 수 있다.
  - any타입을 사용하면 컴파일 시 타입을 체크하지 않는다.
  - 타입을 체크하지 않아 관련 메서드의 힌트를 사용할 수 없다.
  - 컴파일 시에 컴파일러가 오류를 찾지 못한다.
  - generic도 any처럼 타입을 지정하지 않지만, 타입을 체크해 컴파일러가 오류를 찾을 수 있다.

```ts
"use client";

import React, { useState } from "react";

interface IObj {
  lg: string;
  samsung: string;
}

interface Fruits {
  apple: string;
  grape: string;
  orange: string;
  mandarin: string;
}

const TestComp = () => {
  const [count, setCount] = useState<number>(0);

  const cower: IObj | any = {
    lg: "gram",
    samsung: "galaxy",
  };

  if (cower) {
    for (const key in cower) {
      const value = cower[key];
      const value2 = Object.keys(cower);
      const value3 = Object.values(cower);

      console.log("key", key);
      console.log("value", value);
      console.log("value2", value2);
      console.log("value3", value3);
    }
  }

  function hello2<T>(msg: T): T {
    console.log("msg", msg, typeof msg);
    return msg;
  }

  hello2("hi");
  hello2(123);

  // <> 심볼이 jsx가 아니라는 확신을 주면 된다.
  const hello3 = <T>(x: T): T => {
    console.log("x", x, typeof x);
    return x;
  };

  hello3("hi");

  const hello4 = <T extends {}>(x: T): T => {
    console.log("x", x, typeof x);
    return x;
  };

  hello4("hi");

  // T는 항상 Fruits을 포함하고 있어야 한다.
  function helloFruits<T extends Fruits>(fruit: T): T {
    console.log("fruit", fruit);
    return fruit;
  }

  // keyof 옵션을 사용하면 apple, grape, orange, mandarin
  function helloFruits2<T extends keyof Fruits>(fruit: T): T {
    console.log("fruit", fruit);
    return fruit;
  }

  const fruits = {
    apple: "apple",
    grape: "grape",
    orange: "orange",
    mandarin: "mandarin",
  };

  helloFruits(fruits);
  helloFruits2("apple");

  const handleAlertClick = () => {
    console.log("경고창 노출하는 이벤트");
    alert("Warning!");
  };

  const handleCountClick = () => {
    console.log("숫자가 증가하는 이벤트");
    setCount((prev) => prev + 1);
  };

  const handleResetClick = () => {
    setCount(0);
  };

  return (
    <>
      <div>
        <button onClick={() => handleAlertClick()}>경고노출</button>
        <p>{count}</p>
        <button onClick={() => handleCountClick()}>숫자증가</button>
        <button onClick={() => handleResetClick()}>리셋</button>
      </div>
    </>
  );
};

export default TestComp;
```
