    position: relative;

    position: absolute;

    position속성의 값으로 absolute, fixed가 지정된 요소는, display 속성이 block으로 변경됨

## 표기법
    ash-case - - - -
    snake-case _ _ _ -
    camelCase theQuickBrownFox
    pascalCase TheQuickBrownFoxd

## 데이터종류(자료형)
    string
    Number
    Boolean
    Undefined
    Null
    Object
    Array

- undefined - 값이 할당되어 있지 않은 상태
- null - 어떤 값이 의도적으로 비어있음을 의미

- 변수 - 데이터를 저장하고 참조(사용)하는 데이터의 이름

- var, let, const

```js
`함수 - 특정 동작(기능)을 수행하는 일부 코드의 집합(부분) function`

// 기명(이름이 있는) 함수
// 함수 선언
function hello() {
console.log('Hello~~')
}

// 익명(이름이 없는) 함수
// 함수 표현
let world = function() {
console.log('World~~')
}

// 함수 호출
hello();
world();
```

```js
// 객체 데이터
const hero = {
  name: 'bongjun',
  age: 29,

  // 메소드(Method)
  getName function() {
    return this.name;
  }
};

const hisName = hero.getName();
console.log(hisName); // bongjun
console.log(hero.getName(); // bongjun
```

```
<script defer src="./main.js"></script>
defer - html코드를 다 읽은 상태로 다시 main.js 내용을 실행하겠다
```

```js
const boxEl = document.querySelector('.box');

// Getter, 값을 얻는 용도
console.log(boxEl.textContent); // Box!!

// Setter, 값을 지정하는 용도
boxEl.textContent = 'hero';
console.log(boxEl.textContent);
```

### Node.js는 Chrome V8 JavaScript 엔진으로 빌드된 JavaScript 런타임.
- 프로그래밍 언어가 동작하는 환경

### npm init -y : packege.json 생성

### npm i -D xxx
- -D 개발용 의존성 패키지 : 설치한 특정한 패키지 들이 개발할때만 필요, 웹 직접 동작x
- -D : --save -dev 의 약어

### npm i xxx
- 일반 의존성 설치 : 웹 브라우저에서도 동작 할수 있는 개념이다 하고 선언, 동작 용도

### 번들(Bundle)은 우리가 프로젝트 개발에 사용한 어려 모듈(패키지)을 하나로 묶어내는 작업