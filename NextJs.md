# NextJs

### getStaticProps(SSG: Static Site Generation)

- getStaticProps는 최초 빌드 시에 딱 한 번만 호출이 된다.

### getServerSideProps(SSR: Server Side Rendering)

- getStaticProps와 다르게 요청이 들어올 때마다 호출되며, 그 때마다 사전 렌더링을 진행한다.

- 요청 시마다 다시 호출되므로 빌드 이후 자주 바뀌게 될 동적 데이터가 들어갈 때 더 사용하기 좋다.
