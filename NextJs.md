# NextJs

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
import { useRouter } from 'next/router';

const test = () => {
    const router = useRouter();
    const { id } = router.query;

    return (
        <>
            <p>test : {id}</p>
        </>
    )
}
```