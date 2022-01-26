console.log(typeof 'hello'); // string
console.log(typeof 123); // number
console.log(typeof true); // boolean
console.log(typeof undefined); // 의도하지 않은 빈 값, undefined
console.log(typeof null); // 의도한 빈 값, object
console.log(typeof {}) // object
console.log(typeof []) // object

// function getType(data) {
//   return Object.prototype.toString.call(data).slice(8, -1);
// }

console.log(getType(false)); // Boolean
console.log(getType(null)); // Null
console.log(getType({})); // Object
console.log(getType([])); // Array

// 산술 연산자 (arithmetic operator)

console.log(1 + 2);
console.log(5 - 7);
console.log(3 * 4);
console.log(10 / 5);
console.log(10 % 5);

let qq = 2  // = = 할당연산자
qq += 2;
console.log(qq); // 4

// 비교 연산자 (comparison operator)

const a = 1;
const b = 2;
console.log(a === b); // flase
console.log(a !== b); // true
console.log(a < b); // true
console.log(a > b); // false
console.log(a >= b); // false

function isEqual(x, y) {
  return x === y
}

console.log(isEqual(1, 1)); // true

// 논리 연산자 (logical operator)

function logical () {
  const a = 1;
  const b = 'AB' === 'AB'
  const c = false;

  console.log(a); // 1
  console.log(b); // true
  console.log(c); // true

  // and 연산자 : a, b, c 가 전부 true인지 확인해서 전부 true인 경우에만 true 반환
  console.log('&&: ', a && b && b); // true
  // or 연산자: a, b, c 중 하나라도 true가 있으면 true 반환
  console.log('||: ', a || b || c) // 1(true)
  // not 연산자: true -> false, false -> true 반환
  console.log('!: ', !a);
}

logical();

// 삼항 연산자 (ternary operator)

function ternary() {
  const a = 1 < 2

  if (a) {
    console.log('참');
  } else {
    console.log('거짓');
  }

  console.log(a ? '참' : '거짓');
}

ternary();

// 조건문 (If statement, Switch statement)

function ifElse() {
  const a = 2;

  if (a === 0) {
    console.log('a is 0');
  } else if (a === 2) {
    console.log('a is 2');
  } else if (a === 4) {
    console.log('a is 4');
  } else {
    console.log('rest...');
  }

  // 조건문 (Switch statement)
  const b = 2;

  switch (b) {
    case 0 :
      console.log('a is 0'); 
      break;
    case 2 :
      console.log('a is 2');
      break;
    case 4 :
      console.log('rest...');
      break;
    default:
      break;
  }
}

ifElse();

// 반복문 (For statement)
// for (시작조건; 종료조건; 변화조건) {}

// const ulEl = document.querySelector('ul');

// console.log(ulEl);

// for(let i = 0; i < 10; i += 1) {
//   const li = document.createElement('li');
//   li.textContent = `list-${i + 1}`;
//   // 짝수인 리스트만 출력
//   if ((i + 1) % 2 === 0) {
//     li.addEventListener('click', function() {
//       console.log(li.textContent);
//     });
//   } 
//   ulEl.appendChild(li);
// }

// 변수의 유효범위 (Variable Scope)
// ver, let, const

function scope() {
  if (true) {
    const a = 123;
    console.log(a); // 123
  }
  console.log(a); // a is not defined
}
scope()

// 형변환 (Type conversion)


// Truthy(참 같은값)
// true, {}, [], 1, 2, 'false', -12, '3.14 ...

// Falsy(거짓 같은 값)
// false, '', null, undefined, 0 , -0, NaN

function type() {
  const a = 1;
  const b = '1';

  console.log(a == b); // true - 권장하지 않는방법
  console.log(a === b); // false

  if(1) {
    console.log(1 + undefined); // NaN, 숫자 데이터긴한데 숫자는 아니다
  }
}
type();

// 함수 복습
// 함수선언식 - 기명함수
//          매개변수
function sum(x, y) {
  // 더해진 값이 반환되면 return 키워드를 통해 함수 밖으로 내보낼 수 있다.
  return x + y
}
//   인수
sum(1, 3);
sum(4, 12);

// 함수표현식 - 익명함수
// const sum = function(x ,y) {
//   return x + y;
// }

// sum(1, 3);

function sum2() {
  console.log(arguments); // [Arguments] { '0': 7, '1': 3 }
  return arguments[0] + arguments[1]; // 10
}

console.log(sum2(7, 3));

// 화살표 함수
// () =>  {} vs function() {}

const double = function(x) {
  return x * 2;
}
console.log('double: ', double(7)); // 14

const doubleArrow = (x) => {
  return x * 2;
}
// 축약형
// const doubleArrow = x => x * 2
// 객체데이터는 () - 소괄호 안에 작성해야함
// const duobleArrow = x => ({ name: 'bongjun'});
console.log('doubleArrow: ', doubleArrow(7)); // 14

// 즉시실행함수
// IIFE, Immediately-Invoked Function Expression

const aa = 7;
function double2() {
  console.log(aa * 2); // 14
}
double2();

// 즉시실행함수
(function () {
  console.log(aa * 2); // 14
})();

(function () {
  console.log(aa * 2); // 14
}());

// 호이스팅(Hoisting)
// 함수 선언부가 유효범위 최상단으로 끌어올려지는 현상

// const a = 7;

// double();

// const double = function () {
//   console.log(a * 2); // double is not a function
// }

// const a = 7;

// double();

// function double () {
//   console.log(a * 2); // 14
// }

// 타이머 함수
// setTimeout(함수, 시간): 일정 시간 후 함수실행
// setInterval(함수, 시간): 시간 간격마다 함수실행
// clearTimeout(): 설정된 Timeout 함수를 종료
// clearInterval(): 설정된 Interval 함수를 종료


//                 단위: ms = 1000ms = 1초
// const timer = setTimeout(() => {
//   console.log('Bongjun!');
// }, 3000);

// // h1태그 클릭시 타이머 멈춤
// const h1El = document.querySelector('h1');
// h1El.addEventListener('click', () => {
//   clearTimeout(timer);
// });

// const timer2 = setInterval(() => {
//   console.log('Bongjun2');
// });

// const h1El2 = document.querySelector('h1');
// h1El2.addEventListener('click', () => {
//   clearTimeout(timer2);
// });

// 콜백(Callback)
// 함수의 인수로 사용되는 함수

function timeout(callback) {
  setTimeout(() => {
    console.log('Bongjun!');
    callback();
  }, 3000)
}
// 콜백함수
timeout(() => {
  console.log('Done!');
});

const bong = {
  fitstName: 'Bongjun',
  lastName: 'Kim',
  getFullName: function () {
    return `${this.fitstName} ${this.lastName}`
  }
}
console.log(bong.getFullName());

function user(first, last) {
  this.firstName = first;
  this.lastName = last;
}

//                생성자함수
const bongjunk = new user('Bongjun', 'Kim');

console.log(bongjunk);

// this
// 일반(Normal) 함수는 호출 위치에서 따라 this 정의!
// 화살표(Arrow) 함수는 자신이 선언된 함수 범위에서 this 정의!

const bongjun = {
  name: 'Bongjun',
  normal: function () {
    console.log(this.name); // Bongjun
  },
  arrow: () => {
    console.log(this.name); // undefined
  }
}
bongjun.normal(); // Bongjun
bongjun.arrow(); // undefined

const amy = {
  name: 'Amy',
  normal: bongjun.normal,
  arrow: bongjun.arrow
}

amy.normal(); // Amy, 호출 위치에서 정의
amy.arrow(); // undefined, 화살표 함수가 만들어지는 곳에서 정의

// ES6 Classes

class User {
  constructor(first, last) {
    this.firstName = first
    this.lastName = last
  }
  getFullName() {
    return `${this.firstName} ${this.lastName}`
  }
}

const james = new User('james', 'kim');
const neo = new User('Neo', 'Smith');

console.log(james); // User { firstName: 'james', lastName: 'kim' }
console.log(neo.getFullName()); // Neo Smith


// Javascript Level up

// JS데이터
// string: "", '', ``
// Number
// Boolean: true, false
// undefined
// null
// Array: []
// Object: {}

// string.prototype.indexOf();
// 일치하는 값이 없으면 -1반환
const result = 'Hello World!'.indexOf('World'); //6
console.log(result); // 6

const str = 'Hello world!';
const email = 'bjkim@anidream.co.kr';
console.log('0123'.length); //4
console.log(str.length); //12
console.log(str.indexOf('Bongjun') !== -1); // false
console.log(str.slice(0, 3)); // Hel = 0번째부터 3번째까지 자름
console.log(str.replace('world', 'Bongjun')); // Hello Bongjun = 첫번째 인수의 문자를 찾아서 두번째 인수에 해당하는 내용으로 교체
console.log(str.replace(' world', '')); // Hello!
console.log(email.match(/.+(?=@)/)[0]); // bjkim - 정규표현식 @ 앞에있는 내용을 모두 추출한다.
console.log(str.trim()); // 문자 앞 뒤의 공백 제거