# Recoil
- React를 위한 상태관리 라이브러리다.
- recoil 상태를 사용하는 컴포넌트는 부모 트리 어딘가에 나타나는 `RecoilRoot`가 필요하다.
- 루트 컴포넌트가 `RecoilRoot`를 넣기에 가장 좋다.

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

### state만 정의

- const [state] = useRecoilState(초기값);

### setState만 정의

- setState만 사용할 경우, 쉼표를 넣어줘야 한다.
- const [, setState] = useRecoilState(초기값);
