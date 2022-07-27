# GraphQl

    GraphQL은 웹 클라이언트가 데이터를 질의하는데에 최적화된 일종의 인터페이스이자 쿼리 언어입니다.

## Rest API vs GraphQl

```js
// 책 목록보기
axios.get("https://api.marktube.tv/v1/book", { header: `Bearer ${token}` });

// 책 조회하기
axios.post(
  "https://api.marktube.tv/v1/book",
  {
    title,
    message,
    author,
    url,
  },
  { headers: `Bearer ${token}` }

  // 책 수정하기
  axios.patch(
    `https://api.marktube.tv/v1/book/${book.id}`,
    {
      title,
      message,
      author,
      url,
    },
    { headers: `Bearer ${token}` },
  )
);

// 책 삭제하기
axios.delete(
  `https://api.marktube.tv/v1/book/${book.id}`,
  { headers: `Bearer ${token}` },
);
```

uri의 형태와 메소드의 조합으로 특정 리소스의 조회 생성,수정,삭제 등을 하는 방식
단점 : 요청이 항상 메소드와 uri 형태의 조합으로 이루어져 있어서 결과물을 의도적으로 받아오기 힘듬

GraphQl - 쿼리를 보내서 그 결과물로 원하는 데이터만 얻을 수 있다.

npm i apollo-server
npm i nodemon -D
npm i qraphql

## typeDef & resolver

### typeDef(s)

- GraphQL Schema를 정의하는 곳
  - object
  - Query
  - Mutation
  - Input
- gql과 Tagged Template Literals로 작성한다.

### resolver(s)

- Schema에 해당하는 구현을 하는 곳
- 요청을 받아 데이터를 조회, 수정, 삭제하는 로직을 작성하는 곳

### GraphQl code generator?

    *.graphql 의 파일에 존재하는 스키마와 쿼리를 바탕으로, 다양한 언어에 맞게 타입, 혹은 코드 자체를 생성해줍니다.

### GraphQl 단점?

- 재귀적인 쿼리가 불가능
- 고정된 요청과 응답만 필요한 경우 쿼리로 인해 요청의 크기가 REST API보다 커진다.
- 데이터 쿼리의 상당 작업을 서버측으로 옮겨 서버 개발자 작업의 복잡성이 커집니다.
- 캐싱이 REST API보다 훨씬 복잡

### useQuery, useLazyQuery 차이점

#### useQuery

- useQuery는 query에 대한 결과를 응답
  - 페이지가 로딩됐을때 자동으로 실행
  - (컴포넌트가 실행될 때 자동으로 쿼리가 실행)

#### useLazyQuery

- useLazyQuery는 결과와 쿼리를 실행할 수 있는 함수를 return 한다.
  - 이벤트에 대한 응답으로 쿼리를 실행하는데 적합
  - 특정 액션 이후에 데이터 호출