# Moment.js

    Javascript에서 날짜 및 시간을 조작하고 작업하는데 도움이 되는 Javascript 라이브러리

    날짜 및 시간과 관련된 라이브러리 중에서 가장 오래되었다.

- 객체 형태로 정의되어 new Date()와 비슷하게 선언하여 사용한다.
- 날짜/시간 이라는 개념을 핸들링 하기 위해 만들어진 오브젝트
- OOP 개념이 담긴 라이브러리
- 현재는 두 가지 이유로 개발이 중단
- moment는 mutable

  - Moment.js의 용량문제
  - 너무 오래되어 신규 기능 추가가 어려움

- 단점을 극복하기 위해 Day.js, Luxon.js, date-fns.js등 여러 라이브러리가 개발되었다.

# Day.js

    Moment.js의 축소 버전으로 동일한 API를 사용하며, 용량은 Moment.js파일의 2~3%

```js
// dayjs()에 빈 값을 전달하면 현재 날짜 및 시간 기준으로 dayjs 객체가 생성됨
dayjs();
```

# date.fns

- 함수 단위로 라이브러리가 구성되어 있다.
- date-fns는 immutable
