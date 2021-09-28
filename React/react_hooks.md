# 리액트 훅(React Hooks) 개념 정리

    리액트의 새로운 기능으로 React 16.8버전에 새로 추가된 기능
    React hook을 사용하면 class component, render 등을 안해도 된다.

### useState
    가장 대표적인 Hook 컴포넌트에 의지하지 않고 state를 가질 수 있게 해줌

```javascript
// class component
class test extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      count: 0
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
import React, { useState } from 'react';

function test() {
    const [state, setState] = useState(0);

    return (
        <div>
            <p>{state}</p>
            <button onClick={() => { setState(state + 1)}}>
                Click
            </button>
        </div>
    );
}
```