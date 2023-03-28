# NextJs

- 리액트 기반의 프레임워크
  - 생산성과 편의성 증대
  - SPA의 단점을 커버
- Next.js는 기본적으로 모든 페이지를 pre-render한다.
- 모든것을 자동으로 설정하는 `create-next-app`를 사용하여 새 Next.js앱을 만드는 것이 좋다.

      npx create-next-app@latest
      or
      yarn create next-app
      or
      pnpm create next-app

- 설치가 완료되면 `npm run dev`나 `yarn start`를 입력하여 개발 서버를 시작

- `npm run build`

```json
// package.json
"scripts": {
  "dev": "next dev",
  "build": "next build",
  "start": "next start",
  "lint": "next lint",
}
```

- "dev": "next dev" : 개발 모드에서 Next.js를 시작하기 위한 실행
- "build": "next build" : 프로덕션 사용을 위한 애플리케이션을 빌드하기 위해 실행
- "start": "next start" : Next.js 프로덕션 서버를 시작하기 위해 실행
- "lint": "next lint" : Next.js의 내장 ESLint 구성을 설정하기 위해 실행

### getStaticProps(SSG: Static Site Generation)

- getStaticProps는 최초 빌드 시에 딱 한 번만 호출이 된다.

- 매번 fetch를 하지 않으니 getServerSideProps 보다 성능이 좋음

### getServerSideProps(SSR: Server Side Rendering)

- getStaticProps와 다르게 요청이 들어올 때마다 호출되며, 그 때마다 사전 렌더링을 진행한다.

- 요청 시마다 다시 호출되므로 빌드 이후 자주 바뀌게 될 동적 데이터가 들어갈 때 더 사용하기 좋다.

- pre-render가 꼭 필요한 동적 데이터가 있는 page에 사용. 속도는 느리지만 동적으로 수정 가능

### 동적 라우팅

    파일 네임이나 폴더에 []를 써줌으로 이 페이지는 동적 라우팅이 된다는 것을 명시

```js
// 사용예시
import { useRouter } from "next/router";

const test = () => {
  const router = useRouter();
  const { id } = router.query;

  return (
    <>
      <p>test : {id}</p>
    </>
  );
};
```

### 서버 사이드 렌더링(SSR)

- SSR은 사이트가 열릴때, 렌더링된 html을 불러온다. 빠르게 화면을 제공
- 상대적으로 서버 요청이 적음

#### 장점
- 초기 페이지 로드 시간이 빠르다.
  - 렌더링이 준비된 HTML 파일을 브라우저에서 로드하기 때문

### 클라이언트 사이드 렌더링(CSR)

- 서버는 요청을 받으면 클라이언트에 HTML과 JS를 보내줌 클라이언트는 받아서 렌더링을 시작

- 모든것은 클라이언트에서 처리된다.

#### 장점
- 후속 페이지 로드 시간이 더 빠르다.
- 모든 스트립트가 사전에 로드되어, CSR 로드 시간이 줄어든다.
- 서버를 호출할 때마다 전체 UI를 로드할 필요가 없다.

#### 단점
- 초기 페이지 로드 시간이 SSR보다 느리다.
  - HTML을 컴파일 하기 전에 기본 HTML, CSS 및 스크립트를 로드하기 떄문이다.

### - Warning: Function components cannot be given refs. Attempts to access this ref will fail. Dis you mean to use React.forwardRef()? 에러

- Next.js 에서 <Link>를 사용시 구성요소를 자식으로 사용할 떄 에러가 발생

```js
// error
<Link>
    <button></button>
</Link>

// success
<Link>
    <a>
        <button></button>
    </a>
</Link>
```
### Router
- Next.js 에서 라우터를 사용하려면 `useRouter`훅을 사용해서 `router`객체에 접근할 수 있다.

```ts
import { useRouter } from 'next/router';

const TestRouter = () => {
  const router = useRouter();

  const routerClick = (e) => {
    e.preventDefault();
    router.push('/');
  }
  return (
    <>
      <p>test router</p>
      <button onClick={routerClick}>라우터 버튼</button>
    </>
  )
}

```

### router.push, router.place 차이
- `router.push` 사용시 히스토리가 순서대로 쌓여서 메인 다음 페이지에서 뒤로 가기 버튼 클릭시 메인 페이지로 돌아간다.

- `router.replace` 사용시 현재 페이지를 변경해줘서 뒤로 가기 클릭시 메인 페이지 이전의 페이지로 이동
- `router.replace`는 페이지를 이동하기보다 현재 페이지를 바꿔줌

### Next.js 13버전

- `next/link` Link 태그 사용시 자식요소로 `<a></a>`태그 생략가능
```ts
<Link href='/Main'><a>메인</a></Link>
<Link href='/Main'>메인</Link>
```