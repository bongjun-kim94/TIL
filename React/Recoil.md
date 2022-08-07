# Recoil

    React를 위한 상태관리 라이브러리다.

    설치법
    - npm install recoil
    - yarn add recoil

### RecoilRoot

- recoil 상태를 사용하는 컴포넌트 부모트리에 RecoilRoot가 필요하다.
- 루트 컴포넌트가 RecoilRoot를 넣기의 최적의 장소이다.

```ts
import React from "react";
import { RecoilRoot } from "recoil";

function App() {
  return (
    <RecoilRoot>
      <Main />
    </RecoilRoot>
  );
}
```

### Atom

- Atom은 상태(state)의 일부를 나타낸다.
- Atoms는 어떤 컴포넌트에서나 읽고 쓸수 있다.
- atom의 값을 읽는 컴포넌트 들은 암묵적으로 atom을 구독
- atom에 변화가 있으면 atom을 구독하는 모든 컴포넌트 들이 재렌더링 된다.

```ts
const atomState = atom({
  key: "atomState",
  default: "",
});
```

### useRecoilState

- 컴포넌트가 atom을 읽고 쓰게 하기 위해선 `useRecoilState()`를 사용하면 된다.

```ts
const [atom, setAtom] = useRecoilState(atomState);
```

### selector

- Selector는 파생된 상태의 일부를 나타낸다.
- 파생된 상태는 상태의 변화다.
- 파생된 상태를 어떤 방법으로라도 주어진 상태를 수정하는 순수 함수에 전달된 상태의 결과물로 생각할 수 있다.
