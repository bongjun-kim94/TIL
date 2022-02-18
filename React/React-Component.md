# React Component

React Shadow - html 에서 쉐도우 돔을 이용해서 완전히 요염될 수 없도록 하는 기술

Ant Design

- import 'antd/dist/antd.css'; // 전역 스타일 추가 in index.js
- import { DatePicker } from 'antd'; // 리액트 컴포넌트 in App.js

# 리액트 실전 활용

## HOC - High Order Component (고차 컴포넌트)

    고차 컴포넌트는 컴포넌트를 가져와 새 컴포넌트를 반환하는 함수
    HOC = fuction(컴포넌트) { return 새로운 컴포넌트; }

- 비슷한 역할을 할수 있는 훅이 나와서 사용량이 줄어드는중
- withRouter() - 보통 with가 붙은 함수가 HOC인 경우가 많다.

- 주의할점
  - 사용할때 HOC를 렌더 메소드 안에서 사용하지마라
  - 인자로 들어간 컴포넌트의 static methods는 copy되지 않기 때문에 따로 새로 만들어진 컴포넌트에
    static methods로 복사해서 넣어줘
  - refs는 passed through되지 않음

## Controlled Component & Uncontrolled Component

상태를 가지고 있는 엘리먼트

- input
- select
- textarea
- ...

엘리먼트의 '상태'를 누가 관리하느냐

- 엘리먼트를 가지고 있는 컴포넌트가 관리
  - Controlled
- 엘리먼트의 상태를 관리하지 않고, 엘리먼트의 참조만 컴포넌트가 소유
  - Uncontrolled

## Hooks & Context

Basic Hooks

- useState
- useEffect
- useContext(Contexrt API에서 다룹니다)

Functional Component = Stateless Component = Stateless Functional Component

useState가 나오면서 Functional Component != Stateless Component (becaouse state hook)

클래스 컴포넌트에서 state 에서 잘 사용했었는데, 갑자기 useState가 나타나서 함수형 컴포넌트에서 상태를 처리하려는 이유

- 컴포넌트 사이에서 상태와 관련된 로직을 재사용하기 어렵습니다.
  - 컨테이너 방식 말고, 상태와 관련된 로직
- 복잡한 컴포넌트들은 이해하기 어렵습니다.
- Clas는 사람과 기계를 혼동시킵니다.
  - 컴파일 단계에서 코드를 최적화하기 어렵게 만든다.
- this.state는 로직에서 레퍼런스를 공유하기 때문에 문제가 발생할 수 있다.

- useState
  - state를 대체 할 수 있다.
- useEffect
  - 라이프 사이클 훅을 대체 할 수 있다.
    - componentDidMount
    - componentDidUpdate
    - componentWillUnmount

## Custom Hooks

마운티드 됐을때 알려줄수있는, 인자로 넣어진 컴포넌트에 hasmounted라는 프롭스가들어감

- useHasMounted vs withHasMounted

useSomething

Additional Hooks

- useReducer (useState의 확장판)
  - 다수의 하윗값을 포함하는 복잡한 정적 로직을 만드는 경우
  - 다음 state가 이전 state에 의존적인 경우
  - Redux를 안다면 쉽게 사용 가능
- useCallback
- useMemo
- useRef

React Router Hooks

- useParams()

컴포넌트간 통신

- A의 button을 클릭하여 E를 변경하려면

```js
// A 컴포넌트
<div>
  <B />
  <button>클릭</button>
</div>

// B 컴포넌트
<div>
  <C />
</div>

// C 컴포넌트
<div>
  <D />
</div>

// D 컴포넌트
<div>
  <E />
</div>

// E 컴포넌트
<div>
  {props.value}
</div>
```

1. `<A />` 컴포넌트에서 button에 onClick 이벤트를 만들고,
2. button을 클릭하면, `<A />`의 state를 변경하여, `<B />`로 내려주는 props를 변경
3. `<B />` 의 props가 변경되면, `<C />`의 props에 전달
4. `<C />` 의 props가 변경되면, `<D />`의 props에 전달
5. `<D />` 의 props가 변경되면, `<E />`의 props에 전달

- E의 button을 클릭하여 A의 p를 변경하려면

```js
// A 컴포넌트
<div>
  <B />
  <p>{state.value}</p>
</div>

// B 컴포넌트
<div>
  <C />
</div>

// C 컴포넌트
<div>
  <D />
</div>

// D 컴포넌트
<div>
  <E />
</div>

// E 컴포넌트
<div>
  <button>클릭</button>
</div>
```

1. `<A />` 에 함수를 만들고, 그 함수 안에 state를 변경하도록 구현, 그 변경으로 인해 p안의 내용을 변경
2. 만들어진 함수를 props에 넣어서, `<B />`로 전달
3. `<B />` 의 props의 함수를 `<C />`의 props로 전달
4. `<C />` 의 props의 함수를 `<D />`의 props로 전달
5. `<D />` 의 props의 함수를 `<E />`의 props에 전달, `<E />`에서 클릭하면 props로 받은 함수를 실행

## Context API

하위 컴포넌트 전체에 데이터를 공유하는 법

- 데이터를 Set 하는 놈
  - 가장 상위 컴포넌트 => 프로바이더
- 데이터를 Get 하는 놈
  - 모든 하위 컴포넌트에서 접근 가능
    - 컨슈머로 하는 방법
    - 클래스 컴포넌트의 this.context로 하는 방법
    - functional 컴포넌트의 useContext로 하는 방법

데이터를 Set 하기

1. 일단 컨텍스트를 생성한다.
2. 컨텍스트, 프로바이더를 사용한다.
3. value를 사용

데이터를 Get 하기(1) - Consumer

1. 컨텍스트를 가져온다.
2. 컨텍스트, 컨슈머를 사용한다.
3. value를 사용

데이터를 Get 하기(2) - class

1. static contextType에 컨텍스트를 설정한다.
2. this.context => value이다.

데이터를 Get 하기(3) - functional

1. useContext로 컨텍스트를 인자로 호출한다.
2. useContext의 리턴이 value이다.

React Testing

JavaScript Unit Test
Jest 사용하기
React Component Test
testing-library/react 활용하기
enzyme 활용하기

## jest (facebook 오픈소스)

    npm i jest -D

- 리액트의 영향이 크겠지만 가장 핫한 테스트 도구
- Easy Setup
- Instant Feedback
  - 고친 파일만 빠르게 테스트 다시 해주는 기능 등
- Snapshot Testing
  - 컴포넌트 테스트에 중요한 역할을 하는 스냅샷
