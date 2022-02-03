# JS데이터

```javascript
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
```

<br />

```javascript
const pi = 3.14159265358979;
console.log(pi);

// 소수점 두자리까지만 남겨두고 나머지는 제거
const str = pi.toFixed(2);
console.log(str); // 3.14
console.log(typeof str); // string

const integer = parseInt(str);
const float = parseFloat(str);
console.log(integer); // 3
console.log(float); // 3.14
console.log(typeof integer, typeof float); // number number 
```

<br />

```javascript
Math.abs()
// 절대값을 반환 -1 -> 1, -99 -> 99
console.log('abs:', Math.abs(-12)); // 12
// 인수로 들어온 숫자 데이터들 중에 가장 작은값을 출력
console.log('min: ', Math.min(2, 8)); // 2
// 인수로 들어온 숫자 데이터들 중에 가장 큰 값을 출력
console.log('max: ', Math.max(2, 8)); // 8
// 올림처리
console.log('ceil: ', Math.ceil(3.14)); // 4
// 내림처리
console.log('floor: ', Math.floor(3.14)); // 3
// 반올림처리
console.log('round: ', Math.round(3.14)); // 3
// 0~1 사이의 랜덤한 숫자를 반환, 난수
console.log('random: ', Math.random()); // 0.~~~~~

console.log(0.7414322798398292 * 10); // 7.414322798398292
```

<br />

# 배열 데이터 api

```javascript
// 배열 데이터 각각의 이름을 element(요소) 라고 한다 === 배열의 item
const numbers = [1, 2, 3, 4];

// 주어진 판별 함수를 만족하는 첫 번째 요소의 값을 반환
const found = numbers.find(el => el > 2);
console.log(found); // 3

//                 0         1         2 = index
const fruits = ['Apple', 'Banana', 'Cherry'];

console.log(numbers);
// 대괄호에 숫자를 넣어서 조회하는것 - 인덱싱(indexing)
console.log(fruits[2]);
```

<br />

# length

```javascript
console.log(numbers.length); // 4
console.log(fruits.length); // 3
console.log([1, 2].length); // 2
console.log([].length); // 0
```

<br />

# concat
    두개의 배열 데이터를 병합하여 새로운 배열 데이터를 반환, 원본의 데이터는 영향x

```javascript
console.log(numbers.concat(fruits)); // [ 1, 2, 3, 4, 'Apple', 'Banana', 'Cherry' ]
console.log(numbers);
console.log(fruits);
```

<br />

# forEach
    element는 item으로도 자주 사용, array부분은 자주 사용x
    배열 데이터의 아이템의 개수만큼 특정한 콜백함수를 반복적으로 실행하는 용도로 사용하는 메소드

```javascript
fruits.forEach(function (element, index, array) {
  console.log(element, index, array);
});

// Apple 0 [ 'Apple', 'Banana', 'Cherry' ]
// Banana 1 [ 'Apple', 'Banana', 'Cherry' ]
// Cherry 2 [ 'Apple', 'Banana', 'Cherry' ]
```

<br />

# map
    forEach는 따로 실행되고 반환되는것이 없다.

```javascript
const a = fruits.forEach((fruit, index) => {
  console.log(`${fruit} - ${index}`); // Apple - 0
});                                   // Banana - 1
                                      // Cherry - 2
console.log(a); // undefined

// map이라는 메소드는 인수로 사용하는 콜백의 내부에서 반환하는 하나의 데이터를 가지고 그 데이터들을 모아놓은 새로운 배열을 만들어서 반환
const b = fruits.map((fruit, index) => {
  // return `${fruit} - ${index}`; // console.log() - // [ 'Apple - 0', 'Banana - 1', 'Cherry - 2' ]
  return {
    id: index,
    name: fruit
  }
});
// or
const b = fruits.map((fruit, index) => ({ 
  id: index, 
  name: fruit 
}));
  return `${fruit} - ${index}`; // console.log() - // [ 'Apple - 0', 'Banana - 1', 'Cherry - 2' ] 

console.log(b);
// [
//   { id: 0, name: 'Apple' },
//   { id: 1, name: 'Banana' },
//   { id: 2, name: 'Cherry' }
// ]
```

<br />

# filter

```javascript
const aa = numbers.map(number => {
  return number < 3;
});
console.log(aa); // [ true, true, false, false ]

// 필터된 새로운 배열 데이터를 결과로 반환
const bb = numbers.filter(number => {
  return number < 3;
});
console.log(bb); // [ 1, 2 ]
```

<br />

# find(), findIndex()

```javascript
// 대문자 B로 시작하는 문자데이터
const aaa = fruits.find(fruit => /^B/.test(fruit));
console.log(aaa); // Banana

const bbb = fruits.findIndex(fruit => /^C/.test(fruit));
console.log(bbb); // 2
```

<br />

# includes()
    인수로 사용되는 특정한 데이터가 해당하는 특정 배열에 들어있는지 그렇지 않은지 확인하는 메소드
```javascript
const c = numbers.includes(3);
console.log(c); // true

const d = fruits.includes('Bongjun');
console.log(d); // false
```

<br />

# push(), unshift()
### 원본 수정됨 주의!

    배열데이터의 가장 뒤쪽 부분에 데이터가 삽입되어지는 메소드
```javascript

numbers.push(5);
console.log(numbers); // [ 1, 2, 3, 4, 5 ]

// 배열데이터의 가장 앞 부분에 데이터가 삽입되어지는 메소드
numbers.unshift(0);
console.log(numbers); // [ 0, 1, 2, 3, 4, 5 ]
```

<br />

# reverse()
### 원본 수정됨 주의!
    배열데이터를 거꾸로 뒤집어주는 메소드, 배열의 아이템의 순서를 뒤집어내는 용도로 사용
```javascript
numbers.reverse();
fruits.reverse();

console.log(numbers); // [ 4, 3, 2, 1 ]
console.log(fruits); // [ 'Cherry', 'Banana', 'Apple' ]
```

<br />

# splice()
### 원본 수정됨 주의!
    첫번째 부분은 배열 데이터의 인덱스 값을 집어넣음, 두번째 부분은 인덱스 번호에서 아이템 한개를 지움
    단순하게 ~~째 아이템을 지우는 용도, 새로운 아이템을 끼워넣는용도 두가지의 용도

```javascript
numbers.splice(2, 1);
console.log(numbers); // [ 1, 2, 4 ]

// numbers.slice(인덱스의 번호, 몇개를 삭제할지 숫자, 그 자리에 삽입할 데이터);
// 2번에서 아무런 아이템도 지우지않고 999라는 숫자 데이터를 그 자리에 삽입
numbers.splice(2, 0, 999);
console.log(numbers); // [ 1, 2, 999, 3, 4 ]
```

<br />

# Object.assign()
    객체데이터에서 속성의 이름은 고유해야한다. 새로운 속성의 숫자데이터로 덮어쓰기된다.

```javascript
const target = { a: 1, b: 2 };
const source = { b: 3, c: 5 };
// //                                대상객체,  출처객체
const returnedTarget = Object.assign(target, source);

console.log(target); // { a: 1, b: 3, c: 5 }
console.log(returnedTarget); // { a: 1, b: 3, c: 5 }

// 하나의 객체 데이터는 특정한 메모리 주소에 값이 들어가있다.
const userAge = {
  // key: value
  name: 'Bongjun',
  age: '29'
}
const userEmail = {
  name: 'Bongjun',
  email: 'bjkim@anidream.co.kr'
}
```

```javascript
const target = Object.assign(userAge, userEmail);
console.log(target); // { name: 'Bongjun', age: '29', email: 'bjkim@anidream.co.kr' }
console.log(userAge); // { name: 'Bongjun', age: '29', email: 'bjkim@anidream.co.kr' }
console.log(userEmail); // { name: 'Bongjun', email: 'bjkim@anidream.co.kr' }

console.log(target === userAge); // true

const target2 = Object.assign({}, userAge, userEmail);
console.log(target2); // { name: 'Bongjun', age: '29', email: 'bjkim@anidream.co.kr' }
console.log(target2 === userAge); // false

// 다른 메모리 주소를 바라보고 있기 때문에 서로 다르다고 판단해서 false
const ab = { k: 123 }
const ba = { k: 123 }
console.log(ab === ba); // false

const user = {
  name: 'Bongjun',
  age: 29,
  email: 'bjkim@anidream.co.kr'
}

const keys = Object.keys(user);
console.log(keys); // [ 'name', 'age', 'email' ]

console.log(user['email']); // bjkim@anidream.co.kr
console.log(user.email); // bjkim@anidream.co.kr

// user객체에서 각각의 key부분에 있는 값들을 추출해서 그것을 배열로 만들어서 반환
const values = keys.map(key => user[key]);
console.log(values); // [ 'Bongjune', 29, 'bjkim@anidream.co.kr' ]
```

<br />

# 구조 분해 할당 (Destructuring assignment) <br /> (구조화 할당)

```javascript
const { name, age, email, adress } = user;

console.log(`사용자의 이름은 ${name}입니다.`); // 사용자의 이름은 Bongjun입니다.
console.log(`${name}의 나이는 ${age}입니다.`); // Bongjun의 나이는 29입니다.
console.log(`${name}의 이메일 주소는 ${email}입니다.`); // Bongjun의 이메일 주소는 bjkim@anidream.co.kr입니다.
console.log(adress); // undefined

const fruits2 = ['Apple', 'Banana', 'Cherry'];
// 구조분해하는 데이터의 타입에 맞게 기호를 사용
const [q, w, e, r] = fruits2;
console.log(q, w, e, r); // Apple Banana Cherry undefined
```

<br />

# 전개연산자 (Spread)
```javascript
console.log(fruits2); // [ 'Apple', 'Banana', 'Cherry' ]
console.log(...fruits2); // Apple Banana Cherry

// function toObject(a, b, c) {
//   return {
//     a: a,
//     b: b,
//     c: c,
//   }
// }

const toObject = (a, b, c) => ({ a, b, c });
console.log(toObject(...fruits2));

// console.log(toObject(fruits2[0], fruits2[1], fruits2[2])); // { a: 'Apple', b: 'Banana', c: 'Cherry' }
// console.log(toObject(...fruits2)); // { a: 'Apple', b: 'Banana', c: 'Cherry' }
```

<br />

# 데이터 불변성(Immutability)
```javascript
원시 데이터 : String, Number, Boolean, undefined, null
참조형 데이터 : Object, Array, Function
함수의 인수로 사용되는 또다른 함수를 콜백함수라고함

원시 데이터 - 데이터가 불변하기 때문에 데이터의 생김새가 똑같으면 사실상 같은 데이터라 봐도 충분하다.
참조형 데이터 - 불변하는 개념이 아니라 선언할때 마다 새로운 메모리 주소에 참조형 데이터들이 할당될 수 있는 구조
생김새가 같더라도 서로 같은 데이터가 아닐 수 있음, 그래서 한쪽을 수정하면 다른쪽도 수정됨.
let a = { k: 1 };
let b = { k: 1 };
console.log(a, b, a === b); // { k: 1 } { k: 1 } false

// 같은 메모리 주소를 바라보고 있기 때문에 값이 같아짐
a.k = 7;
// 할당연산자를 사용했을때, a가 가지고 있는 데이터가 복사되는 개념이 아니고,
// 단순하게 메모리 주소만 같은 곳으로 바라보게 만들어 줌. 
// a를 수정해도 b가 수정되고, b를 수정해도 a가 수정된다.
b = a;
console.log(a, b, a === b); // { k: 7 } { k: 7 } true

a.k = 2;
console.log(a, b, a === b); // { k: 2 } { k: 2 } true

let c = b;
console.log(a, b, c, a === c); // { k: 2 } { k: 2 } { k: 2 } true

a.k = 9;
console.log(a, b, c, a === c); // { k: 9 } { k: 9 } { k: 9 } true
```

<br />

# 얕은 복사(Shallow copy), 깊은 복사(Deep copy)
```js
`공통사용`
const users = {
  name: 'bongjunk',
  age: 29,
  emails: ['bjkim@anidream.co.kr']
}
```
---
```javascript
CASE 1 - Call By reference(데이터 복사가 아닌 참조)
`데이터가 그대로 하나 더 생성된 것이 아닌 해당 데이터의 메모리 주소를 전달하게되어,
결국 한 데이터를 공유하게 되는것`

const copyUsers = users;
console.log(copyUsers === users); // true

console.log('users', users); // users { name: 'bongjunk', age: 22, emails: [ 'bjkim@anidream.co.kr' ] }
console.log('copyUsers', copyUsers); // copyUsers { name: 'bongjunk', age: 22, emails: [ 'bjkim@anidream.co.kr' ] }
```

---

```javascript
CASE 2
                            `대상객체, 출처객체`
const copyUsers = Object.assign({}, users);
console.log(copyUsers === users); // false

얕은 복사
const copyUsers = {...users};
console.log(copyUsers === users); // false

// 같은 데이터를 수정하는것이라 copyUsers에도 영향이감
users.age = 22;
console.log('users', users); // users { name: 'bongjunk', age: 22, emails: [ 'bjkim@anidream.co.kr' ] }
console.log('copyUsers', copyUsers); // copyUsers { name: 'bongjunk', age: 29, emails: [ 'bjkim@anidream.co.kr' ] }

users.emails.push( 'mydlwm_s@naver.com' );
console.log(users.emails === copyUsers.emails); // true

console.log('users', users); // users { name: 'bongjunk', age: 22, emails: [ 'bjkim@anidream.co.kr', 'mydlwm_s@naver.com' ] }
console.log('copyUsers', copyUsers); // users { name: 'bongjunk', age: 22, emails: [ 'bjkim@anidream.co.kr', 'mydlwm_s@naver.com' ] }
```
---
```js
CASE 3 -  lodash를 이용한 깊은 복사

const copyUsers = _.cloneDeep(users);
console.log(copyUsers === users); // false

let objects = [{ 'a': 1 }, { 'b': 2 }];

let deep = _.cloneDeep(objects);
console.log(deep[0] === objects[0]); // false
```

### 정리
- 객체라던가 배열을 복사할 때는 내부의 또다른 참조데이터가 없다는 전제하에 손쉽게 얕은 복사 사용
- 특정한 참조데이터 내부에 또다른 참조데이터가 들어가 있다면 깊은 복사를 고려

<br />

# JSON
    JavaScript Object Notation - 자바스크립트의 데이터로 표현해야하는 하나의 포맷

```js
const user2 = {
  name: 'Bongjun',
  age: 29,
  emails: [
    'mydlwm_s@naver.com',
    'bjkim@anidream.co.kr'
  ]
};

console.log('user2', user2);
// user2 {
//   name: 'Bongjun',
//   age: 29,
//   emails: [ 'mydlwm_s@naver.com', 'bjkim@anidream.co.kr' ]
// }     

const str2 = JSON.stringify(user2);
console.log(typeof str2); // string

const obj = JSON.parse(str2);
console.log('obj', obj);
// obj {
//   name: 'Bongjun',
//   age: 29,
//   emails: [ 'mydlwm_s@naver.com', 'bjkim@anidream.co.kr' ]
// }
```

<br />

# localStorage

```js
//user2 객체 데이터를 문자데이터화해서 로컬스토리지의 user2라는 이름으로 저장
localStorage.setItem('user2', JSON.stringify(user2));
console.log(JSON.parse(localStorage.getItem('user2')));
localStorage.removeItem('user2');

const str3 = localStorage.getItem('user2');
const obj = JSON.parse(str3);
obj.age = 22;
console.log(obj);
localStorage.setItem('user2', JSON.stringify(obj));
```