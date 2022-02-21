# 리액트란?

    자바스크립트 라이브러리로 사용자 인터페이스를 만들기위해 사용

- \*싱글 페이지 애플리케이션(SPA)의 UI(User Interface)를 생성하는데 집중한 라이브러리다.

  - 하나의 HTML페이지와 애플리케이션 실행에 필요한 Javascript와 CSS같은 모든 자산을 로드하는 애플리케이션,
    서버로부터 새로운 페이지를 불러오지 않으므로 페이지가 다시 로드되지 낳음.

- 자바스크립트에 HTML을 포함하는 \*JSX(Javascript XML)이라는 문법을 사용

  - 자바스크립트 확장 문법으로, Javascript의 기능들을 사용할 수 있다.

- 리액트는 \*단방향 데이터 바인딩을 사용한다.

- 컴포넌트(Component) 기반의 구조이다.

- Vitual DOM을 사용한다.

  - 이벤트가 발생할 때마다 Virtual DOM을 만들고, 리로드될 때마다 실제 DOM과 비교하고 변경되는 부분만 실제 DOM에 반영하여, 앱의 효율성과 속도를 개선

- Props & State

  - Props란 부모 컴포넌트에서 자식 컴포넌트로 전달해주는 데이터
  - 읽기 전용 데이터로, props를 전달해준 최상위 컴포넌트만 변경가능

  - state란 컴포넌트 내부에서 선언하고 내부에서 값을 변경할 수 있다.

  - 컴포넌트의 상태를 나타냄

```javascript
    // 클래스형 컴포넌트
    import React from 'react';

    class App extends Component {
        render() {
            return (
                //JSX
            );
        }
    }

    export default App;

    // 함수형 컴포넌트
    import React from 'react';

    function App() {
        return (
            //JSX
        );
    }

    export deafult App;
```

## React Getting Started - React Comcept

### Keyword

- Angular vs React vs Vue
- View를 다루는 라이브러리
- Only Rendering & Update - 렌더링과 업데이트만 관련
  - NOT included another functionality (ex. http client, ...)
- Component Based Development
  - 독립적인 코드 블럭(HTMl + CSS + JavaScript)
  - 작업의 단위
- Virtual DOM
  - 이제는 DOM을 직접 다루지 않음
- JSX
  - NOT Templates
  - transpile to JS (Babel, TypeScript) - 순수한 js로 트랜스파일되는 문법
- CSS & SSR

---

- ## Angular vs React vs Vue

- **Angular** - 풀 프레임워크

  크로스 플랫폼, 어떤 플랫폼에서던지 하나의 코드 베이스로 결과물을 낼 수 있게 도와줌
  모든 기능이 프레임워크 안에서 하나를 이루고있음

- **view** - 라이브러리 & 프레임워크로도 쓸 수 있다.

  프로그레시브 JavaScript 프레임워크

- **React** - 라이브러리
  user interfaces를 만들기 위한 자바스크립트 라이브러리

### Component

```html
<!-- HTMLElement -->
<img src="이미지 주소" />
<button class="클래스 이름">버튼</button>

<!-- 내가 만든 컴포넌트 -->
<내가지은이름1 name="Bong" />
<내가지은이름2 prop={false}>내용</내가지은이름2>

<!--
- src, class, name, props 밖에서 넣어주는 데이터
- 문서(HTML), 스타일(CSS), 동작(JS)를 합쳐서 내가 만든 일종의 태그
-->
```

### Why Virtual DOM?

- DOM을 직접 제어하는 경우
  - 바뀐 부분만 정확히 바꿔야 한다.
- DOM을 직접 제어하지 않는 경우
  - 가상의 돔 트리를 사용해서,
  - 이전 상태화 이후 상태를 비교하여,
  - 바뀐 부분을 찾아내서 자동으로 바꾼다.
- State Change => Compute Diff => Re-render

### CSR vs SSR

- CSR

  - JS가 전부 다운로드 되어 리액트 애플리케이션이 정상 실행되기 전까지는 화면이 보이지 않음.
  - JS가 전부 다운로드 되어 리액트 애플리케이션이 정상 실행된 후, 화면이 보이면서 유저가 인터렉션 가능

- SSR
  - JS가 전부 다운로드 되지 않아도, 일단 화면은 보이지만 유저가 사용할 수 없음.
  - JS가 전부 다운로드 되어 리액트 애플리케이션이 정상 실행된 후, 유저가 사용가능

### 개발환경

- Node.js - 개발환경
  - installer
  - nvm
- Browser (Chrome)
- Git
- VSCode

### 리액트가 하는 일 - 리액트의 핵심 모듈 2개로 리액트가 하는 일 알아보기

```js
// 1. 리액트 컴포넌트 => HTMLElement 연결하기
import ReactDOM from "react-dom";

// 2. 리액트 컴포넌트 만들기
import Reacrt from "react";
```

"만들어진 리액트 컴포넌트"를 실제 HTMLElement에 연결할 때 ReactDOM 라이브러리를 이용합니다.

### ~~고전~~ 프론트엔드 - 리액트 이전

    HTML로 문서 구조를 잡고,
    CSS로 스타일을 입히고,
    JavaScript로 DOM을 조작합니다.

컴포넌트를 활용한 프론트엔드
컴포넌트를 정의하고, 실제 DOM에 컴포넌트를 그려준다.

브라우저 지원
React는 Internet Explorer 9과 상위 버전을 포함한 모든 주요 브라우저를 지원합니다. 그러나 IE 9과 IE 10과 같은 구형 브라우저는 폴리필(polyfill)이 필요합니다.

## React Component

Hooks 이전

- 컴포넌트 내부에 상태가 있다면?
  - class
- 컴포넌트 내부에 상태가 없다면?
  - 라이프사이클을 사용해야 한다면?
    - class
  - 라이프사이클에 관계 없다면?
    - function

Hooks 이후

- class
- function

## JSX

JSX 문법으로 작성된 코드는 순수한 JavaScript로 컴파일 하여 사용한다.
누가 해주나요?? => babel

왜 JSX를 쓰나요??

- React.createElement VS JSX
  - 가독성 완승
- babel과 같은 컴파일 과정에서 문법적 오류를 인지하기 쉬움

JSX문법

- 최상위 요소가 하나여야 합니다.
- 최상위 요소 리턴하는 경우,()로 감싸야합니다.
- 자식들을 바로 렌더링 하고 싶으면 <>자식들</>를 사용합니다. => Fragment
- 자바스크립트 표현식을 사용하려면, {표현식}을 이용합니다.
- if문은 사용할 수 없습니다.
  - 삼항 연산자 혹은 &&를 사용합니다.
- style을 잉요해 인라인 스타일링이 가능합니다.
- class 대신 className을 사용해 class를 적용할 수 있습니다.
- 자식요소가 있으면, 꼭 닫아야하고, 자식요소가 없으면 열면서 닫아야 합니다.
  - <p>어쩌구</p>
  - `<br />`

Props와 State
Props는 컴포넌트 외부에서 컴포넌트에게 주는 데이터
State는 컴포넌트 내부에서 변경할 수 있는 데이터
둘 다 변경이 발생하면, 렌더가 다시 일어날 수 있습니다.

Render 함수
Props와 State를 바탕으로 컴포넌트를 그립니다.
그리고 Props와 State가 변경되면, 컴포넌트를 다시 그립니다.
컴포넌트를 그리는 방법을 기숭하는 함수가 렌더함수 입니다.

## Event Handling

- HTML DOM에 클릭하면 이벤트가 발생하고, 발생하면 그에 맞는 변경이 일어나도록 해야합니다.
- JSX에 이벤트를 설정할 수 있습니다.

<br />

- camelCase로만 사용할 수 있습니다.
  - onClick, onMouseEnter
- 이벤트에 연결된 자바스크립트 코드는 함수입니다.
  - 이벤트={함수}와 같이 씁니다.
- 실제 DOM 요소들에만 사용 가능합니다.
  - 리액트 컴포넌트에 사용하면, 그냥 props로 전달합니다.

```js
class Comp extends React.Component {
  render() {
    return (
      <>
        <button
          onClick={() => {
            console.log("clicked");
          }}
        >
          클릭
        </button>
      </>
    );
  }
}
```

## Component Lifecycle

    리액트 컴포넌트는 탄생부터 죽음까지 여러지점에서 개발자가 작업이 가능하도록
    메서드를 오버라이딩 할 수 있게 해준다.

### Component 생성 및 마운트 (< v16.3)

1. constructor
2. componentWillMount - Mount되기 직전
3. render(최초렌더) - Mount
4. componentDidMount - Mount된 직후

### Component props, state 변경 (< v16.3)

1. componentWillRecieveProps
2. shouldComponentUpdate
3. componentWillUpdate
4. render
5. componentDidUpdate

### componentWillReceiveProps

- props를 새로 지정했을때 바로 호출됩니다.
- 여기는 state의 변경에 반응하지 않습니다.
  - 여기서 props의 값에 따라 state를 변경해야 한다면,
    - setState를 이용해 state를 변경합니다.
    - 그러면 다음 이벤트로 각각 가는것이 아니라 한번에 변경됩니다.

### shouldComponentUpdate

- props만 변경되어도
- state만 변경되어도
- props & state 둘다 변경되어도
- newProps와 newState를 인자로 해서 호출
- return type이 boolean입니다.
  - true면 render
  - false면 render가 호출되지 않습니다.
  - 이 함수를 구현하지 않으면, 디폴트는 true

### componentWillUpdate

- 컴포넌트가 재 렌더링 되기 직전에 불립니다.
- 여기선 setState 같은 것을 쓰면 아니됩니다.

### componentDisUpdate

- 컴포넌트가 재 렌더링을 마치면 불립니다.

### component 언마운트 (< v16.3) (componentWillUnmount)

### Component 라이프사이클 변경 (v16.3)

- constructor
- ~~componentWillMount~~ => getDerivedStateFromProps
- render
- componentDidMount

<br />

- ~~componentWillReceiveProps~~ => getDerivedStateFromProps
- shouldComponentUpdate
- render
- ~~componentWillUpdate~~ => getSnapshotBeforeUpdate
- (dom에 적용)
- componentDidUpdate

- componentWillUnmount

### Component 에러 캐치

- componentDidCatch
  - 단점은 자기 자신에게 에러가 있을땐 캐치를 하지못함

--- 0216

npx - npm 5.2.0 이상부터 함께 설치된 커맨드라인 명령어
라이브러리를 현재 최신 버전의 라이브러리를 확인해서 최신이면 새로 받아서 실행해주는 커맨드라인 명령어

npm start - 개발 모드로 로컬에서 띄울 수 있는 기능, 개발 도중 소스코드 수정 가능
npm run build - 배포할 준비, 소스코드를 작고 못생기게 만들어줌, 최적화

- npm start
  - react-scripts start
  - Starting the development server...
- npm run build
  - react-scripts build
  - Creating on optimized production build...
  - project 폴더 바로 아래 build라는 폴더가 만들어지고, 그 안에 production 배포를 위한 파일들이 생성됨
- npm test
  - react-scripts test
  - Creating an optimized production build...
- npm run eject
  - react-scripts eject
  - eject를 이용하면, cra로 만든 프로젝트에서 cra를 제거합니다.
  - 이는 돌이킬 수 없기 때문에 결정하기 전에 신중해야 합니다.
  - 보통 cra 내에서 해결이 안되는 설정을 추가해야 할 때 합니다.
    - 결과
      - react-scripts는 사라집니다.
      - 드러내지 않고 cra에 의해 사용되던 각종 패키지가 package.json에 나타납니다.
      - jest, Babel, ESLint 설정이 추가됩니다.
      - 각종 설정 파일이 config 폴더에 생성됩니다.

<br />

    npm install serve -g
    serve -s build

- serve 라는 패키지를 전역으로 설치합니다.
- serve 명령어를 -s 옵션으로 build 폴더를 지정하여 실행합니다.
  - -s 옵션은 어떤 라우팅으로 요청해도 index.html을 응답하도록 합니다.

<br />

자동으로 추적해서 테스트 코드로 사용

- _tests_ 폴더안의 .js 파일
- .test.js로 끝나는 파일
- .spec.js로 끝나는 파일

Prettier (An opinionated code formatter)
eslint보다 많진 않지만 좀 더 단순하고 정확한 몇가지 중요한 인자들을 바탕으로 포맷팅을 할 수 있는 툴

```js
// Prettier에서 불필요하거나, Prettier와 출동할 수 있는 모든 규칙을 끕니다.
// 이 구성은 규칙을 끄기만 하기 때문에 다른 설정과 함께 사용하는것이 좋습니다.
{
  ...
  "eslintConfig" {
    "extends": [
      "react-app",
      "prettier"
    ]
  } ,
  ...
}
```

### husky

Git hooks made easy

lint-staged - 커밋을 하기 직전에 eslint나 prettier을 통해 staged된 파일을 점검할 수 있게된다.
Run linters on git staged files

// js파일이 스테이지에 올라와있으면 eslint --fix를 하고 변경된 사항을 다시 git add 하겠다.

```js
"lint-staged": {
  "\*_/_.js": [
  "eslint --fix",
  "prettier --write",
  "git add"
  ]
}
```

React Developer Tools

---

### 데이터 바인딩?

    두 데이터 혹은 정보의 소스를 일치시키는 기법

#### \* 단방향 데이터 바인딩?

    데이터와 템플릿을 결합해 화면을 생성하는것 (JS -> HTML만 가능)

- 장점

  - 데이터 변화에 따른 성능 저하 없이 DOM객체 갱신가능
  - 데이터 흐름이 단방향 (부모 -> 하위 컴포넌트)
  - 데이터 추적과 디버깅이 쉽다.

- 단점
  - 변화를 감지하고 화면을 업데이트 하는 코드를 매번 작성해야한다.
