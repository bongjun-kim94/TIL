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

