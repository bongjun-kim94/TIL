# nodejs 값 입력받기

    nodejs로 값을 입력받는 방법은 대표적으로 두가지가 있다.

## fs module

```javascript
const fs = require("fs");

// 문자 하나만 입력받을 경우
const input = fs.readFileSync("/dev/stdin").toString().split(" ");

let num = Number(input[0]);

// 한 칸 띄어쓰기로 구분
// input[0], input[1] 에서 사용
const input = fs.readFileSync("/dev/stdin").toString().split(" ");

// 줄 바꿈으로 구분
const input = fs.readFileSync("/dev/stdin").toString().split("\n");

// 여러 줄 입력받기
const fs = require("fs");
const input = fs.readFileSync("/dev/stdin").toString().split("\n");

const count = input[0];
const numbers = [];

for (let i = 1; i < input.length; i++) {
  if (input[i] !== "") {
    numbers.push(input[i].split(" "));
  }
}

for (let i = 0; i < numbers.length; i++) {
  const num1 = Number(numbers[i][0]);
  const num2 = Number(numbers[i][1]);

  console.log(num1 + num2);
}
```

## readline module

```javascript
const readline = require("readline");
const rl = readline.createInterface({
  input: process.stdin,
  output: process.stdout,
});

rl.on("line", function (line) {
  console.log(line);

  re.close();
}).on("close", function () {
  process.exit();
});

// ex) 사분면 고르기
const readline = require("readline");
const rl = readline.createInterface({
  input: process.stdin,
  output: process.stdout,
});

let input = [];
rl.on("line", function (line) {
  input.push(parseInt(line));
}).on("close", function () {
  const X = input[0];
  const Y = input[1];

  if (X > 0) {
    Y > 0 ? console.log(1) : console.log(4);
  }
  if (X < 0) {
    Y > 0 ? console.log(2) : console.log(3);
  }
  process.exit();
});
```
