# ES6-ES11 문법

## Shorthand property names

- obj의 key와 value가 동일하면 하나로 쓸 수 있다.
```ts
const name = 'bongjun';
const age = 29;

const person1 = {
    name: name,
    age: age
};

const person2 = {
    name,
    age
}
```