# Arry method

### sort

    배열을 오름차순, 내림차순으로 정렬한다.

```javascript
const arr = [3, 5, 8, 2, 1];
const result = arr.sort();
console.log(result); // [1, 2, 3, 5, 8]

// 거꾸로 출력
const result2 = arr.sort((a, b) => b - a);
console.log(result2); // [8, 5, 3, 2, 1]
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

    함수를 받아 특정 기능을 실행, 새로운 배열을 반환

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

### join

    배열을 합쳐서 문자열을 만듬

```javascript
const arr = ["안녕", "하세요", "여러분"];

const result = arr.join();

console.log(result); // 안녕,하세요,여러분
```

### split

    문자열을 나눠서 배열로 만들어줌

```javascript
const arr = "안녕, 하세요, 여러분";

const result = arr.split(",");

console.log(result); // ['안녕', '하세요' , '여러분']
```