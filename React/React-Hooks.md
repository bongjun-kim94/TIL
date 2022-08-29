# 리액트 훅(React Hooks) 개념 정리

    리액트의 새로운 기능으로 React 16.8버전에 새로 추가된 기능
    React hook을 사용하면 class component, render 등을 안해도 된다.

### useState

    가장 대표적인 Hook 컴포넌트에 의지하지 않고 state를 가질 수 있게 해줌
    함수형 컴포넌트에서 가변적인 상태를 지닐 수 있게 해준다. 상태를 관리해야 할 때 사용

#### setState()

- setState는 비동기적으로 동작한다.
- setState는 항상 즉시 컴포넌트를 업데이트 하지 않음
- 두 번째 파라미터에 callback func 넣는게 불가능해져서, useEffect() 사용
- 비동기적으로 작동하기 떄문에 setState()를 호출하고 바로 다음에 state를 읽으려하면 원하는 결과가 나오지 않는다.
- 함수형 컴포넌트 일 때는, useEffect를 사용하면 해결할 수 있다.
- state가 발생하면 리렌더링이 계속 발생하여 리액트가 렌더링만 하기 때문에 렌더링을 줄이고자 배치(Batch) 기능을 사용해 비동기로 작동하는 것 이다.

```javascript
// class component
class test extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      count: 0,
    };
  }

  render() {
    return (
      <div>
        <p>{this.state.count}</p>
        <button onClick={() => this.setState({ count: this.state.count + 1 })}>
          Click
        </button>
      </div>
    );
  }
}

// function component
import React, { useState } from "react";

function test() {
  const [state, setState] = useState(0);

  return (
    <div>
      <p>{state}</p>
      <button
        onClick={() => {
          setState(state + 1);
        }}
      >
        Click
      </button>
    </div>
  );
}
```

## useEffect

    리액트 컴포넌트가 렌더릴 될 때마다 특정 작업을 수행하도록 설정할 수 있는 Hook이다.

    useEffect를 통해서 함수형 컴포넌트에서 *사이드 이펙트(side effect)를 수행 할 수 있다

    *데이터 가져오기, 구독 설정, 수동으로 DOM 조작 등을 말함

    기본적으로 React는 매 렌더링 이후에 effects를 실행한다.

```javascript
import React, { useState, useEffect } from "react";

function Example() {
  const [count, setCount] = useState(0);

  // componentDidMount, componentDidUpdate와 비슷합니다
  useEffect(() => {
    // 브라우저 API를 이용해 문서의 타이틀을 업데이트합니다
    document.title = `You clicked ${count} times`;
  });

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>Click me</button>
    </div>
  );
}
```

### componentDidMount()

- 컴포넌트를 처음 렌더링한 후에 실행

### componentDidUpdate()

- 컴포넌트가 갱신되었을 때 DOM을 조작하기 위하여 이 메서드를 활용하면 좋다.
- setState()를 즉시 호출할 수도 있지만, 조건문으로 감싸지 않으면 무슨 반복이 발생할 수 있다.
- 컴포넌트를 최초로 렌더링한 후에 아래 조건이 발생하면 실행
  - props가 변경되는 시점
  - state가 변경되는 시점
  - 부모 컴포넌트 리렌더링 시
  - 강제로 렌더링되는 시점
  - 두 번째 파라미터로 아무 값도 전달하지 않음
  - 위 상황이 발생하면 useEffect 훅에 전달한 콜백함수가 실행

### componentWillUnMount()

- 컴포넌트가 DOM에서 제거될 떄 실행(페이지에서 사라질 때)
- componentDidMount 메소드에서 등록한 이벤트가 있다면 여기서 제거하는 작업을 수행해야 한다.

### useEffect Clean-Up function

- - Clean-Up 함수란 useEffect()에서 파라미터로 넣은 함수의 return 함수
- useEffect 훅의 콜백 함수가 반환한 componentWillUnMount 함수가 useEffect hook의 Clean-Up 함수다.
- 반환하는 함수의 이름은 중요하지 않아서 화살표함수( () => {} ) 를 반환해도 상관없다
  - 다음 세 가지는 Clean-Up 기능이 필요하지 않다.
  - API 요청을 통한 데이터 가져오기
  - 수동으로 Rect 컴포넌트 DOM 조적하기
  - 로깅(logging)
- 이벤트를 등록한 경우에는 메모리 누수가 발생하지 않도록 정리 해야한다.

### useEffect Clean-Up 함수 실행순서

- useEffect 훅의 두 번째 파라미터로 빈 배열이 들어갔기 때문에 리액트 컴포넌트가 제거되는 시점에 Clean-Up 함수가 실행
- componentWillUnMount 메소드가 호출되는 동일한 시점에 Clean-Up 함수가 실행

- 반면에 useEffect 훅의 두 번째 파라미터에 아무것도 넣어주지 않으면 이러한 순서로 실행된다.
  - props/state 업데이트
  - 컴포넌트 리렌더링
  - 이전 이펙트의 Clean-Up 함수
  - 새로운 이펙트 실행

```ts
// componentDidMount
useEffect(() => {
  console.log("componentDidMount");
}, []);

// componentDidUpdate
useEffect(() => {
  console.log("componentDidUpdate");
});

// componentWillUnmount
useEffect(() => {
  console.log("componentDidMount");
  return function componentWillUnMount() {
    console.log("componentWillUnMount");
  };
}, []);
```

## useReducer

    useState보다 더 다양한 컴포넌트 상황에 따라 다양한 상태를 다른 값으로 업데이트 해주고 싶을때 사용

```javascript
// 형태
function reducer(state, action) {}
```

## useMemo

    함수형 컴포넌트 내부에서 발생하는 연산을 최적화,
    의존성이 변경되었을 때만 메모이제이션 된 값을 반환한다.

- 메모이즈된 값을 return하는 hook
- hook이기 때문에 함수형 컴포넌트 에서만 사용가능

### React.memo

- HOC(High Order Components) - 컴포넌트를 인자로 받아 새로운 컴포넌트를 다시 return
- 클래스, 함수형 컴포넌트에서 사용

## useCallback

    주로 렌더링 성능을 최적화 해야 하는 상황에서 사용,
    이벤트 핸들러 함수를 필요할 때만 생성할 수 있다.

- 메모이제이션된 콜백을 반환
- react에 함수를 저장하여 매 실행마다 재생성 하지 않도록 한다.

```ts
// useCallback(() => {...},[dependencies])
// - 저장할 함수
// - useCallback 함수의 dependencies (useEffect 와 동일)
const memoization = useCallback(() => {
  todo(a, b);
}, [a, b]);
```

## useRef

    함수형 컴포넌트에서 ref를 쉽게 사용할 수 있도록 해준다.

## useContext
