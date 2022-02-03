# Lodash 사용법

## _.cloneDeep
    참조데이터 상황에서 깊은 복사(Deep copy)시 사용

```javascript
let objects = [{ 'a': 1}, { 'b': 2 }];

let deep = _.cloneDeep(objects);
console.log(deep[0] === objects[0]); // false
```

## uniq
    배열데이터 안에 들어있는 여러 중복되는 데이터들을 고유하게 바꿔줌

```javascript
_.uniq([2, 1, 2]);
// => [2, 1];
```

<br />

```js
const usersA = [
  { 
    userId: '1', 
    name: 'Bongjun' 
  },
  { 
    userId: '2', 
    name: 'Neo' 
  }
];

const usersB = [
  {
    userId: '1',
    name: 'Bongjun2',
  },
  {
    userId: '3',
    name: 'Amy'
  }
];
```

```js
const usersC = usersA.concat(usersB);

console.log('concat', usersC);
// concat [
//   { userId: '1', name: 'Bongjun' },
//   { userId: '2', name: 'Neo' },
//   { userId: '1', name: 'Bongjun2' },
//   { userId: '3', name: 'Amy' }
// ]

`uniqBy : 배열 데이터가 하나일때 사용`
console.log('uniqBy', _.uniqBy(usersC, 'userId'));
// uniqBy [
//   { userId: '1', name: 'Bongjun' },
//   { userId: '2', name: 'Neo' },
//   { userId: '3', name: 'Amy' }
// ]

`unionBy : 배열 데이터가 여러개일때 사용하는 개념`
const usersD = _.unionBy(usersA, usersB, 'userId');
console.log('unionBy', usersD);
// unionBy [
//   { userId: '1', name: 'Bongjun' },
//   { userId: '2', name: 'Neo' },
//   { userId: '3', name: 'Amy' }
// ]
```
<br />

## _.find, _.findIndex, _.remove

```js
const users2 = [
  { userId: '1', name: 'BONGJUN' },
  { userId: '2', name: 'Neo' },
  { userId: '1', name: 'Amy' },
  { userId: '1', name: 'Evan' },
  { userId: '1', name: 'Lewis' },
];

const foundUser = _.find(users2, { name: 'Amy' });
console.log(foundUser); // { userId: '1', name: 'Amy' }

const foundUserIndex = _.findIndex(users2, { name : 'Amy' });
console.log(foundUserIndex); // 2

_.remove(users2, { name: 'BONGJUN' });
console.log(users2);
// [
//   { userId: '2', name: 'Neo' },
//   { userId: '1', name: 'Amy' },
//   { userId: '1', name: 'Evan' },
//   { userId: '1', name: 'Lewis' }
// ]
```