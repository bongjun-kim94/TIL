# 개요

    React에서 간단하게 form을 만들 수 있게 해주는 Node.js 패키지

    Formik은 가장 성가신 3가지 부분을 도와주는 작은 라이브러리
    폼태그 유효성 검증을 쉽게 도와주는 Formik

- 설치법

  npm
  npm install formik --save

  yarn
  yarn add formik

1. 양식 상태 안팎에서 값 가져오기
2. 유효성 검사 및 오류 메시지
3. 양식 제출 처리

- react-hook-form은 폼의 조건을 각각 따로 적어주는 반면,

- Formik는 폼의 조건을 한군데에 모아서 적어준다.

<br />

    import { Formik, FormikProps, Form, Field } from 'formik';

- <Formik />가장 중요한 구성 요소입니다. 소품을 통해 기본적으로 폼이 작동 할 수 있도록하는 Formik의 내장 폼 핸들러 중 일부를 구성합니다. render소품 도 활용하겠습니다 . 우리의 전체 양식은이 prop에 전달 된 함수를 통해 구성됩니다.
  FormikProps위의 renderprop 함수 를 통해 전달되어 양식의 상태 ( 값, 오류, 입력 터치 여부 (처음 선택), 양식 제출 여부 등)에 액세스 할 수 있습니다.
- <Form />필드를 단순히 감싸는 데 사용하는 가장 간단한 가져 오기입니다. 따라서 모든 <Field />구성 요소는의 자식이어야합니다 <Form />.
- <Field />Formik과 호환되는 요소를 만드는 데 사용됩니다. 즉, Field 구성 요소가 없으면 입력 요소는 Formik에 대해 아무것도 알지 못합니다. <Field />실제로 입력 텍스트 상자를 기본 입력 방법으로 제공하고 선택 드롭 다운 및 텍스트 영역 옵션을 제공합니다.
  즉, Field 컴포넌트를 선언함으로써 Formik에 연결된 입력을 렌더링 할 수 있습니다. 그러나 사용자 지정 구성 요소를 통해 Formik을 사용하려는 입력 방법에 연결할 수도 있습니다.

## initialValues: Values

- 양식의 초기 필드 값인 Formik은 이러한 값을 렌더링 방법 구성 요소에 사용할 수 있도록 합니다 values.
- initialValue소품은 우리가 양식 필드의 초기 값을 지정할 수 있습니다.
- 기본적으로 양식이 비어 있더라도 초기 값으로 모든 필드를 초기화해야 합니다. 그렇지 않으면 React에서 입력을 제어되지 않음에서 제어됨으로 변경했다는 오류가 발생합니다.

- validate소품은 우리가 검증 규칙을 지정할 수 있습니다.


## validationSchema

-validationSchema prop는 Yup schema를 사용하여 보다 쉽고 편하게 유효성 검사를 수행할 수 있다.

- 이 옵션은 Yup의 유효성 검사 오류 메세지를 키가 values / initialValues / touched와 일치하는 객체로 자동 변환 됩니다.


