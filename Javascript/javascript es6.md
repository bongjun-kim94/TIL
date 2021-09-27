# 자바스크립트 ES6란?

    ECMAScript 2015로도 알려져 있는 ECMAScript 6는 ECMAScript 표준의 가장 최신 버전입니다.

# 화살표 함수 (arrow function)

    함수 표현식보다 단순하고 간결한 문법으로 함수를 만들 수 있다.

```javascript
// 화살표 함수 호출
// ES5
var sum = function (a, b) {
  return a + b;
};
console.log(sum(5, 10));

// ES6
const sum = (a, b) => a + b;
console.log(sum(5, 10));
```

# 동기 & 비동기

- 동기란? 발생하는 하나의 이벤트가 모두 끝날 때까지 다른 이벤트를 처리하지 못하고 이벤트가 모두 완료 된 후 다음 이벤트를 동작하는 실행 순서가 확실한 것을 동기적 방식이라 부른다.

- 비동기란? 특정 코드의 처리가 끝나기 전에 다음 코드를 실행할 수 있는 것을 뜻한다.
  연속적으로 발생하는 이벤트를 담은 후 완료되는 순서대로 일을 처리하는 실행 순서가 확실하지 않는 것을 비동기적 방식이라 한다.

- 비동기 처리를 하는 세 가지 방법
  - 콜백 함수 사용 - 가독성이 매우 떨어짐, 모든 콜백에서 각각 에러처리를 해야함
  - Promise
  - Promise를 활용한 async/ await

* Promise 객체는 비동기 작업이 맞이할 미래의 완료 또는 실패와 그 결과 값을 나타냅니다.
* resolve(성공)되는 값은 then 메소드의 인자로 넘어간다. then 메소드는 다시 Promise를 반환
* 반대로 reject(실패)되는 값은 catch 메소드의 인자로 넘어간다.

```javascript
// 프로미스 생성
const promise = function (param) {
  return new Promise(function (resolve, reject) {
    if (param) {
      resolve("success");
    } else {
      reject("failure");
    }
  });
};

// 프로미스 실행
promise(true).then(
  function (message) {
    console.log(message); // 성공
  },
  function (error) {
    console.log(error); // 실패
  }
);
```

- setTimeout - 일정 시간이 지난 후 함수를 실행
- setInterval - 일정 시간 간격으로 함수를 반복

```javascript
// 3초뒤 실행
function fn() {
  console.log(3);
}

setTimeout(fn, 3000);
// 또는
// 3초뒤 실행
setTimeout(() => {
  console.log(3);
}, 3000);
```

- async/await
  - promise를 더욱 쉽게 사용할 수 있도록 해주는 (ES8) 문법
  - 함수 앞부분에 async 키워드를 추가, 함수 내부의 promise앞에서 await 키워드를 사용
  - 코드가 간결해지지만, 에러 처리를 위해 try / catch 로 후속처리, 동기적인 코드 흐름으로 개발 가능

# this

- this - 선언이 아닌 호출에 따라 달라짐

- 일반함수의 this는 window(전역)을 가르키며, 화살표 함수의 this는 언제나 상위스코프의 this를 가르킴

- Call, Apply, Bind함수는 this를 바인딩 하기위한 방법
  - 함수 호출 방식과 관계없이 this를 지정할 수 있음
  - 메서드에 첫 번째 인수로 전달하는 객체에 바인딩
  - 일반함수에서의 this는 undefined가 바인딩 됨.
  - call은 모든 함수에서 사용할 수 있으며, this를 특정값으로 지정할 수 있다.
  - apply는 매개변수를 배열로 받는다.
  - call과 apply는 매개변수를 받는 방법만 다르다.

# 비구조화 할당

    배열이나 객체의 속성을 해체하여, 그 값을 개별 변수에 담을 수 있게 함

```javascript
const [a, b, c] = [1, 2, 3];
console.log(a); // 1
console.log(a, b, c); // 1, 2, 3

const obj = { x: "red", y: "black", z: "yellow" };
let { x, y, z } = obj; // obj.x
console.log(x, y, z);
```

### 구조분해할당

    배열이나 객체의 속성을 분해해서 그 값을 변수에 담을 수 있게 하는 표현식

```javascript
let names = ["Mike", "Tom", "Jane"];

// 배열 구조분해
let [names1, names2, names3] = names;

console.log(names1); // 'Mike'
console.log(names2); // 'Tom'
console.log(names3); // 'Jane'

// 객체 구조분해
let user = { name: "Mike", age: 30 };
let { name, age } = user; // let name = user.name

console.log(name); // 'Mike'
console.log(age); // 30

// 새로운 변수 이름으로 할당 가능
let { name: userName, age: userAge } = user;

console.log(userName); // 'Mike'
console.log(userAge); // 30
```

# 객체 리터럴

    중괄호({})로 감싸진 하나 이상의 속성 이름과 속성 값의 리스트

### 객체 선언 방법

```javascript
  // Javascript 객체 선언 방법
  var people = new Object();
  // 객체 리터럴 표기법
  var people = {}

  // 객체 리터럴
  const obj = {
    prop1 = "첫번째 속성값",
    prop2 = "두번째 속성값",
    prop3 = "세번째 속성값",
  }


  // 공부하고 내용 추가 예정
```

# 스프레드 연산자(Spread Operator)

    객체 또는 배열을 펼칠 수 있다.

```javascript
// 1~5까지 담긴 배열
let arr = [1, 2, 3, 4, 5];
console.log(arr); // [1, 2, 3, 4, 5]
console.log(...arr); // 1, 2, 3, 4, 5
```

# 호이스팅

    어디에 변수를 선언하고 초기화 했을때, 선언부분이 최상단으로 끌어올려지는 현상

```javascript
console.log(a); // undefined
var a = 1;
```

- var 변수와 일반 함수 선언식에 적용된다.
- 함수표현식 에서는 적용되지 않는다.
- 일반 함수 선언문에는 호이스팅이 적용된다.

# 클로저

    클로저는 독립적인 변수를 가르키는 함수이다.
    클로저 안에 정의된 함수는 만들어진 환경을 기억한다.

    // 이해가 잘 안된다.

# for of

```javascript
// es5에는 for in 구문이 있다.
for (var i in { a: 1, b: 2 }) {
  console.log(i); // a b
}

const arr = [1, 2, 3, 4, 5];
// for (변수 in 오브젝트 또는 배열)
// 배열의 인덱스가 i에 할당되어 반복
for (let i in arr) {
  console.log(i); // 0 1 2 3 4
}

// es6에는 for of가 도입되었다. 배열에 대한 값을 출력
for (const a of [1, 2, 3]) {
  console.log(a); // 1 2 3
}

const arr = [1, 2, 3, 4, 5];
// for (변수 of 배열)
for (let i of arr) {
  console.log(i); // 1 2 3 4 5
}
```
