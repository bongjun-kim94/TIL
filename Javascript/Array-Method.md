# Arry method

```javascript
let arr = [1, 2, 3, 4, 5];

// 배열 요소에 접근
console.log(arr[0]); // 1
console.log(arr[3]); // 4

// 배열 요소의 개수
console.log(arr.length);

// 배열의 마지막 요소에 접근
console.log(arr.length - 1); // 4
```

### sort

    배열을 오름차순, 내림차순으로 정렬한다.

    배열 자체가 변경되니까 조심!

```javascript
const arr = [3, 5, 8, 2, 1];
const result = arr.sort();
console.log(result); // [1, 2, 3, 5, 8]

// 거꾸로 출력
const result2 = arr.sort((a, b) => b - a);
console.log(result2); // [8, 5, 3, 2, 1]

function
```

### splice

    특정 요소를 지울 수 있다.

```javascript
const arr = [3, 5, 8, 2, 1];
// 1번째부터 2개 지움
arr.splice(1, 2);

console.log(arr); // [3, 2, 1]
```

### slice

    특정 요소를 반환 있다.

```javascript
const arr = [1, 2, 3, 4, 5];
// 1번째부터 3전까지 반환

console.log(arr.slice(1, 3)); // [2, 3]
```

### concat

    concat() 메서드는 둘 이상의 배열을 병합하는데 사용된다.
    기존 배열을 변경하지 않고, 새 배열을 반환
    합쳐서 새 배열로 반환

```javascript
const arr = [1, 2, 3];

console.log(arr.concat([4, 5])); // [1, 2, 3, 4, 5]

console.log(arr.concat([4, 5], [6, 7])); // [1, 2, 3, 4, 5, 6, 7]
```

### indexOf / lastIndexOf

```javascript
const arr = [1, 2, 3, 4, 5];
arr.indexOf(3); // 2
```

### includes

    포함하고 있는지만 확인

```javascript
const arr = [1, 2, 3, 4, 5];

arr.includes(3); // true
arr.includes(7); // false
```

### filter

    조건을 만족하는 모든 요소를 배열로 반환

```javascript
const arr = [1, 2, 3, 4, 5];

const result = arr.filter((item) => {
  return item % 2 === 0;
});

console.log(result); // [2, 4]
```

### reverse

    배열을 역순으로 재정렬

```javascript
const arr = [1, 2, 3, 4, 5];

console.log(arr.reverse()); // [5, 4, 3, 2, 1]
```

### map

    * 함수를 받아 특정 기능을 실행, 새로운 배열을 반환

    * 배열 내의 모든 요소 각각에 대하여 주어진 함수를 호출한 결과를 모아 새로운 배열을 반환

```javascript
const userList = [
  {
    name: "test1",
    age: 20,
  },
  {
    name: "test2",
    age: 30,
  },
  {
    name: "test3",
    age: 40,
  },
];

const newUserList = userList.map((user, index) => {
  return Object.assign({}, user, {
    id: index + 1,
    isAdult: user.age > 25,
  });
});

console.log(newUserList);
```

```javascript
const arr = [1, 2, 4, 8];

const mapTest = arr.map((x) => x * 2);

console.log(mapTest); // [2, 4, 8, 16]
```

### join

    배열을 합쳐서 문자열을 만듬

```javascript
const arr = ["안녕", "하세요", "여러분"];

const result = arr.join(); // 구분자를 넣지 않아도 출력됨 기본은 ,(콤마)

console.log(result); // 안녕,하세요,여러분
```

### split

    문자열을 나눠서 배열로 만들어줌

```javascript
const arr = "안녕, 하세요, 여러분";

const result = arr.split(","); // 구분자로 전달해 주어야함
const result1 = arr.split(",", 2);

console.log(result); // ['안녕', '하세요' , '여러분']
console.log(result1); // ['안녕', '하세요']
```

### reduce

    arr.redece()
    인수로 함수를 받음
    (누적 계산값, 현재값) => { return 계산값 };

```javascript
// forEach
const arr = [1, 2, 3, 4, 5];

let result = 0;

arr.forEach((num) => {
  result += num;
});

console.log(result); // 15

// arr.reduce()
const arr = [1, 2, 3, 4, 5];

const result = arr.reduce((prev, cur) => {
  // 누적 계산값 + 현재값
  return prev + cur;
  // 초기값 0, 안써도 상관은 x (첫 번째 요소가 들어감)
}, 0);

console.log(result);

// 나이가 15세 이상인 사람의 이름만 출력
let userList = [
  { name: "mike", age: 30 },
  { name: "mike2", age: 35 },
  { name: "mike3", age: 10 },
  { name: "mike4", age: 20 },
  { name: "mike5", age: 25 },
  { name: "mike6", age: 8 },
];

let result = userList.reduce((prev, cur) => {
  if (cur.age > 15) {
    prev.push(cur.name);
  }
  return prev;
}, []);

console.log(result); // ['mike', 'mike2', 'mike4', 'mike5']

// 나이의 합
let userList = [
  { name: "mike", age: 30 },
  { name: "mike2", age: 35 },
  { name: "mike3", age: 10 },
  { name: "mike4", age: 20 },
  { name: "mike5", age: 25 },
  { name: "mike6", age: 8 },
];

let result = userList.reduce((prev, cur) => {
  return (prev += cur.age);
}, 0);

console.log(result); // 128
```

### push

    배열 끝에 하나 이상의 요소를 추가하고,
    배열의 새 길이를 반환

```javascript
let name = ["kim", "lee", "park"];
let add = name.push("choi", "song");

console.log(name); // ['kim', 'lee', 'park', 'choi', 'song'];
// add 변수는 추가한 배열의 새 길이 값을 포함
console.log(add); // 5

const arr = [];
arr.push("kim");
arr.push("lee");
arr.push("park");

console.log(arr); // [ 'kim', 'lee', 'park' ]
// length는 메서드가 아니다.
console.log("Total arr :" + arr.length); // 3
```

### unshift()
- 새로운 요소의 배열을 맨 앞쪽에 추가하고, 새로운 길이를 반환
- unshift 메서드는 배열 형태의 객체 시작점에 주어진 값을 삽입
```ts
const arr = [1, 2, 3];

console.log(arr.unshift(4, 5)); // 5

console.log(arr); // [4, 5, 1, 2, 3]

const arr2 = [1, 2];

arr2.unshift(0);

console.log(arr2); // [0, 1, 2]

arr2.unshift(-2, -1);

console.log(arr2); // [-2, -1, 0, 1, 2]

```