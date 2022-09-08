# GraphQl

    GraphQL은 웹 클라이언트가 데이터를 질의하는데에 최적화된 일종의 인터페이스이자 쿼리 언어입니다.

### Schema란?

- gql은 스키마 작성에 사용되는 언어 타입을 가지고 있어, SDL(Schema Definition Language)이라고 한다.
- GraphQL은 SDL이라 어떤 언어나 프레임워크를 쓰던간에 상관이 없다.

### Types란?

- gql에서 가장 중요한 특징 중 하나이다.
- 뒤에 !(느낌표)는 field가 null이 될 수 없다는 걸 의미.
- Query에서 특정 데이터를 꼭 리턴 시켜 주어야 한다.
- 아래 구문에선 age만 null로 리턴 가능

```ts
type User {
  id: ID!
  name: String!;
  age: Int
}
```

### Scalar types

- Int: 부호가 있는 32비트 정수
- Float: 부호가 있는 부동소수점 값
- String: UTF-8 문자열
- Boolean: True or False return
- ID : 고유한 값의 지표

### Query, Mutation, Subscribe

- Query: 서버로부터 데이터를 받는 방법(데이터를 받는 방식)
- Mutation: 서버에 올라간 데이터를 업데이트 하는 것(Create, Update, Delete)
  - 서버에 변경된 데이터를 보내거나 업데이트 된 데이터를 받는 방식
- Subscribe: 서버와 실시간으로 연결을 유지하는 방법(실시간 통신에 사용)

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

### GraphQl 구조

- Query (쿼리 = 데이터)
  - 읽기를 요청하는 구문
- Mutation (변형)
  - 수정을 요청하는 구문
  - 쿼리를 추가, 삭제할 수 있다.
- Subscription (설명)

### useQuery, useLazyQuery 차이점

#### useQuery

- useQuery는 query에 대한 결과를 응답
  - 페이지가 로딩됐을때 자동으로 실행
  - (컴포넌트가 실행될 때 자동으로 쿼리가 실행)

#### useLazyQuery

- useLazyQuery는 결과와 쿼리를 실행할 수 있는 함수를 return 한다.
  - 이벤트에 대한 응답으로 쿼리를 실행하는데 적합
  - 특정 액션 이후에 데이터 호출
