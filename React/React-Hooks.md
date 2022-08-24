# 리액트 훅(React Hooks) 개념 정리

    리액트의 새로운 기능으로 React 16.8버전에 새로 추가된 기능
    React hook을 사용하면 class component, render 등을 안해도 된다.

### useState

    가장 대표적인 Hook 컴포넌트에 의지하지 않고 state를 가질 수 있게 해줌
    함수형 컴포넌트에서 가변적인 상태를 지닐 수 있게 해준다. 상태를 관리해야 할 때 사용

#### setState()
- setState() 는 비동기적으로 동작한다.
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

#

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

## useRef

    함수형 컴포넌트에서 ref를 쉽게 사용할 수 있도록 해준다.

## useContext
