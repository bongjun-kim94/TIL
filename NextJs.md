# NextJs

- Next.js는 기본적으로 모든 페이지를 pre-render한다.
- 모든것을 자동으로 설정하는 `create-next-app`를 사용하여 새 Next.js앱을 만드는 것이 좋다.

      npx create-next-app@latest
      or
      yarn create next-app
      or
      pnpm create next-app

- 설치가 완료되면 `npm run dev`나 `yarn start`를 입력하여 개발 서버를 시작

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
