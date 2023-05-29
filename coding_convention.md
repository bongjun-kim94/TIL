# official-page

    *PR 올리기 전에 pnpm run build 해서 에러 체크하기*

- 실행방법

```
pnpm i
repo=<repo name> pnpm run dev
```

## 홈페이지

- 실행방법

```
npm run dev
```

## 코딩 컨벤션

- 코딩 컨벤션이란?
  - 코딩 컨벤션은 읽고, 관리하기 쉬운 코드를 작성하기 위한 일종의 코딩 스타일 규약

## 공통 코딩 컨벤션

- 카멜 케이스(camel case)
  - 컴포넌트 파일명, 폴더명, 변수명, 함수명, 속성명
  - inline style (ex. `<div style={{ fontSize: '1rem', fontWeight: '500'}} />`)

```ts
const camelCase;
```

- 파스칼 케이스(pascal case)
  - 컴포넌트 사용, 상수, interface, type, enum

```ts
const PascalCase;
```

- null 이나 undefined 일 수 있는 값은 Optional chaining (?.) 사용

```ts
data?.props;
arr?.[index];
```

- 함수명은

  - props 의 경우 `onClick`과 같이 `on*` 접두사 사용
  - 함수 이름의 경우 `on*`을 `handle*`로 변경하여 `handleClick`같은 이름으로 사용 (ex. `onSubmit` -> `handleSubmit`)

- 하나의 함수는 하나의 기능만을 수행

```ts
"use client";

import React, { useState } from "react";

const TestComp = () => {
  const [count, setCount] = useState<number>(0);

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
