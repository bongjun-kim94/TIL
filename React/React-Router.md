# 리액트 라우터 (React Router)

## SPA 라우팅 과정
1. 브라우저에서 최초에 '/' 경로로 요청
2. React Web App 을 내려줌
3. 내려받은 React App에서 '/'(루트) 경로에 맞는 컴포넌트를 보여줌
4. React App 에서 다른 페이지로 이동하는 동작을 수행하면,
5. 새로운 경로에 맞는 컴포넌트를 보여줌

<br />

    · npm
    · npm install react-router-dom

    · yarn
    · yarn add install react-router-dom
- cra 에 기본 내장된 패키지가 아니다.
- react-router-dom은 Facebook의 공식 패키지는 아니다.
- 가장 대표적인 라우팅 패키지

#### 특정 경로에서 보여줄 컴포넌트를 준비합니다.
- '/' => Home 컴포넌트
- '/profile' => Profile 컴포넌트
- '/about' => About 컴포넌트

```jsx
import { BrowserRouter, Routes, Route } from 'react-router-dom';
import Home from './pages/Home';
import Profile from './pages/Profile';
import About from './pages/About';

function App() {
  return (
    <>
      <BrowserRouter>
        <Routes>
          <Route path="/" element={<Home />} />
          <Route path="/Profile" element={<Profile />} />
          <Route path="/About" element={<About />} />
        </Routes>
      </BrowserRouter>
    </>
  );
}

export default App;
```
- Route는 Routes의 직속 자식이어야 함
- v5 -> v6버전으로 넘어오면서 Route에 exact Prop 사라짐, 서브 경로가 필요한 경우 path에 /* 사용
- exact가 기본적으로 적용, 필요하지 않을때 * 적용
- Route 컴포넌트에 경로(path)와 컴포넌트(element)를 설정하여 나열
- BrowserRouter로 Routes를 감싸줍니다.
