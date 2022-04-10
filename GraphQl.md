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
