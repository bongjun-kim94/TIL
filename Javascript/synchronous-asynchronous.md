# 동기 vs 비동기

- 동기란?

  - 요청을 보내고, 응답을 받아야만 다음으로 진행할 수 있는 실행방식
  - 프로그램을 작성한 순서대로 한 줄씩 실행

- 동기 동작원리

  - 코드가 실행되면 차례대로 Call Stack에 함수가 쌓인다

```js
const name = "Bongjun"; // 1. name이란 문자열을 선언
const naming = `My Name Is ${name}!`; // 2. name을 사용하여 naming이라는 새로운 문자열을 선언
console.log(naming); // 3. naming을 JavaScript 콘솔에 출력
```

- 비동기란?

  - 비동기 프로그래밍은 작업이 완료될 때까지 기다리지 않고, 잠재적으로 오래 실행되는 작업을 시작하여 해당 작업이 실행되는 동안에도 다른 이벤트에 응답할 수 있게 하는 기술
  - 작업이 완료되면 프로그램이 결과를 제공

- 비동기 동작원리
  - Call Stack 에서 비동기 함수가 호출되면 Call Stack에 먼저 쌓였다가 백그라운드로 이동한 후 해당 함수가 등록되고 Call Stack에서 사라짐

### Promose

- 비동기 작업의 최종 완료 또는 실패를 나타내는 객체
- Promise 객체는 비동기 작업이 맞이할 미래의 완료 또는 실패과 그 결과값을 나타냄
- 함수에 콜백을 전달하는 대신에, 콜백을 첨부하는 방식의 객체

- Promise는 다음 중 하나의 상태를 가짐
  - 대기(pending): 이행 하지도, 거부하지도 않은 초기 상태
  - 이행(fulfilled): 연산이 성공적으로 완료됨, 비동기 처리가 완료되어 프로미스가 결과값을 반환해준 상태
  - 거부(rejected): 연산 실패
- 이행이나 거부될 때, 프로미스의 `then` 메서드에 의해 대기열(큐)에 추가된 처리기들이 호출

```ts
// 비동기 작업이 성공한 경우 resolve()를 호출하고, 실패한 경우 reject()를 호출
let exPromise = new Promise((resolve, reject) => {
  // 이 예제에서는 setTimeout()을 사용해 비동기 코드를 흉내냅니다.
  setTimeout(() => {
    resolve("성공!");
  }, 500);
});

exPromise.then((successMessage) => {
  // successMessage는 위에서 resolve() 호출에 제공한 값
  console.log("Promise " + successMessage);
});

// 대기(Pending)
new Promise();

// new Promise() 메서드를 호출할 때 콜백함수를 선언할 수 있고, 콜백 함수의 인자는 resolve, reject
new Promise(function (resolve, reject) {
  // code...
});

// 이행 (Fulfilled)
new Promise(function (resolve, reject) {
  // 콜백 함수의 인자 resolve를 아래와 같이 실행하면 이행 상태가 된다.
  resolve();
});

// 이행 상태가 되면 then()을 이용하여 처리 결과 값을 받을 수 있다.
function getPromise() {
  return new Promise(function (resolve, reject) {
    let data = 100;
    resolve(data);
  });
}

// resolve()의 결과 값 data를 resolveData로 받음
getPromise().then(function (resolveData) {
  console.log(resolveData); //100
});

// Rejected(실패)
new Promise(function (resolve, reject) {
  reject();
});

function getPromise() {
  return new Promise(function (resolve, reject) {
    reject(new Error("Error!!"));
  });
}

// reject()의 결과 값 Error를 err에 받음
getPromise()
  .then()
  .catch(function (err) {
    console.log(err);
  });
```

### 콜백함수(Callback)

- 콜백함수는 함수 안에서 실행되는 또 다른 함수

- 특정 함수에 매개변수로 전달된 함수, 어떤 특정한 시점에 다시 호출되는 함수

- 다른 함수의 인자로써 이용될때나, 어떤 이벤트에 의해 호출 되어질떄 사용하는 함수

- 콜백함수는 이름이 없는 익명의 함수를 사용

  - 함수의 내부에서 실행되기 때문!

### async await 사용법

- async await은 promise를 좀 더 편하게 사용할 수 있게 해준다.
- function 앞에 async 키워드는 두 가지 효과가 있다.

  - 함수는 언제나 promise를 반환
  - 함수 안에서 await를 사용할 수 있다.

- Promise 앞에 async 키워드를 붙이면, javascript는 promise가 처리될 때까지 대기
- 처리가 완료되면 조건에 따라 동작이 이어짐
  - 에러발생 - 예외가 생성됨(에러가 발생한 장소에서 throw error를 호출한 것과 동일)
  - 에러 미발생 - promise 객체의 result 값을 반환
- async/await를 함께 사용하면 읽고, 쓰기 쉬운 비동기 코드를 작성할 수 있다.
- async/await를 사용하면, promise.then/catch가 거의 필요 없다.

```ts
// async 키워드는 함수 앞에 위치
async function ex() {
  /* 함수 앞에 async 키워드를 붙이면 항상 promise를 반환 */
  return;
}
```

- async 함수에는 await 식이 포함될 수 있다.
- 이 식은
  1. async 함수의 실행을 일시 중지한 후
  2. 전달된 promise의 해결을 기다린 후
  3. async 함수의 실행을 다시 시작하고 완료 후 값을 반환
- await 키워드는 async 함수 에서만 유효
  - async 함수의 본문 외부에서 사용시 SyntaxError가 발생
- async/await 함수의 목적은 여러 promise의 동작을 동기스럽게 사용할 수 있게 해줌
- async 함수는 항상 promise를 반환

```ts
const resolve2Seconds = () => {
  return new Promise((resolve) => {
    setTimeout(() => {
      resolve("resolved");
    }, 2000);
  });
};

const asyncCall = async () => {
  console.log("call");
  const result = await resolve2Seconds();
  console.log(result);
};

asyncCall();
// "call"
// "resolved"
```

```ts
async function* foo() {
  yield await Promise.resolve("a");
  yield await Promise.resolve("b");
  yield await Promise.resolve("c");
}

let str = "";

const generate = async () => {
  for await (const value of foo()) {
    str += value;
  }
  console.log(str);
};

generate(); // "abc"
```

- \*yield

  - yield 키워드는 제너레이트 함수(function\* or 레거시 generator 함수)를 중지하거나 재개하는데 사용됨

- 동기란? 동시에 일어난다는 뜻, 요청과 결과가 동시에 일어나고, 요청을 하면 끝날때까지 결과가 주어져야 다음 작업 실행

  - 장점 : 설계가 간단하고 직관적
  - 단점 : 요청에 의한 결과가 봔환될 때 까지 대기해야한다.

- 비동기란? 요쳥을 보내고, 응답과 상관없이 다음 동작을 실행할 수 있는 방식
- 작업 처리 단위를 동시에 맞추지 않아도 됨

  - 장점 : 결과가 반환되는 시간동안 다른 작업을 수행할 수 있다.
  - 단점 : 동기식보다 설계가 복잡하다.
