# nodejs 값 입력받기

    nodejs로 값을 입력받는 방법은 대표적으로 두가지가 있다.

## fs module

```javascript
const fs = require("fs");

// 문자 하나만 입력받을 경우
const input = fs.readFileSync("/dev/stdin").toString();

// 한 칸 띄어쓰기로 구분
// input[0], input[1] 에서 사용
const input = fs.readFileSync("/dev/stdin").toString().split(" ");

// 줄 바꿈으로 구분
const input = fs.readFileSync("/dev/stdin").toString().split("\n");
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
