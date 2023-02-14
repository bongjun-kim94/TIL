# Recoil
- React를 위한 상태관리 라이브러리다.
- recoil 상태를 사용하는 컴포넌트는 부모 트리 어딘가에 나타나는 `RecoilRoot`가 필요하다.
- 루트 컴포넌트가 `RecoilRoot`를 넣기에 가장 좋다.
- React 프로젝트를 위한 전역 상태관리 라이브러리들 중 하나도, 2020년 5월 Facebook에서 출시(React 전용)

- 설치
```ts
npm install recoil
yarn add recoil
```

```ts
import React from 'react';
import { RecoilRoot } from 'recoil';

const App = () => {
    return (
        <>
            <RecoilRoot>
                <Test />
            </RecoilRoot>
        </>
    )
}
```

### Atom
- Atom은 상태(state) 의 일부를 나타낸다.
- Atoms는 어떤 컴포넌트 에서나 읽고 쓸 수 있다.
- atom의 값을 읽는 컴포넌트는 암묵적으로 atom을 구독한다.
- atom에 변화가 있으면 그 atom 을 구독하는 모든 컴포넌트들이 재 렌더링 된다.

```ts
import { atom, useRecoilState } from 'recoil';

const testState = atom({
    key:'textState',
    default: '',
})
const [test, setTest] = useRecoilState(testState);
```

### state만 정의

- const [state] = useRecoilState(초기값);

### setState만 정의

- setState만 사용할 경우, 쉼표를 넣어줘야 한다.
- const [, setState] = useRecoilState(초기값);

### useRecoilState
- 전역으로 useState를 설정하게 해줌
- 선언을 하는 것이 아니고, 전역적으로 선언된 atom을 가져오는 역할

```ts
const [a ,b] = useRecoilState();
```
