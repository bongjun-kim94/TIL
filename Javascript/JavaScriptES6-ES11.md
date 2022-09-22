# ES6-ES11 문법

## Shorthand property names

- obj의 key와 value가 동일하면 하나로 쓸 수 있다.

```ts
const name = "bongjun";
const age = 29;

const person1 = {
  name: name,
  age: age,
};

const person2 = {
  name,
  age,
};
```

## Destructuring Assignment

- 배열, 객체 모두 사용 가능

```ts
// - Old
//array
const first = names[0];
const second = names[1];
//object
const name = persons.name;
const level = persons.level;

// - New
//array
const [first, second] = names;
//object
const { name, level } = persons;
//변수명을 key와 다르게 하고 싶은 경우
const { name: personsName, level: personsLevel } = student;
```
