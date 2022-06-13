# Sass Basics

    CSS Preprocessing - CSS 전처리기 : CSS가 처리되기 전에 동작할 도구
    css는 그 자체로 재미있을 수 있지만, 스타일시트는 점점 더 커지고 복잡해지고 유지·관리하기 어려워진다.
    여기서 전처리기가 도움이 될 수 있다.

## Variables

    sass는 기본적으로 두개의 문법
    scss, sass

`기존 CSS문법` <br />

```css
body {
  font: 100% Helvetica, sans-serif;
  color: #333;
}
```

`sass - 기존의 css랑 호환이 잘 안되는 문제가 발생하여 호환할 수 있는 방법으로 새로운 문법으로 제공`

```scss
// SCSS 문법 - 기존 문법의 일부 단점을 보완하기 위해 나온 새로운 문법
$font-stack: Helvetica, sans-serif;
$primary-color: #333;

body {
  font: 100% $font-stack;
  color: $primary-color;
}

------------------------------------------

// SASS 문법
$font-stack: Helvetica, sans-serif
$primary-color: #333

body
  font: 100% $font-stack
  color: $primary-color
```

## Mixins

`기존 css 문법` <br />

```css
.info {
  background: DarkGray;
  box-shadow: 0 0 1px rgba(169, 169, 169, 0.25);
  color: #fff;
}

.alert {
  background: DarkRed;
  box-shadow: 0 0 1px rgba(139, 0, 0, 0.25);
  color: #fff;
}

.success {
  background: DarkGreen;
  box-shadow: 0 0 1px rgba(0, 100, 0, 0.25);
  color: #fff;
}
```

```scss
// SCSS
@mixin theme($theme: DarkGray) {
  background: $theme;
  box-shadow: 0 0 1px rgba($theme, .25);
  color: #fff;
}

.info {
  @include theme;
}
.alert {
  @include theme($theme: DarkRed);
}
.success {
  @include theme($theme: DarkGreen);
}

------------------------------------------

// SASS
@mixin theme($theme: DarkGray)
  background: $theme
  box-shadow: 0 0 1px rgba($theme, .25)
  color: #fff


.info
  @include theme

.alert
  @include theme($theme: DarkRed)

.success
  @include theme($theme: DarkGreen)
```

## 주석

    // 나 /* */ 둘 다 허용

```scss
// - 변환을 하면 css코드로 들어가지 않음

// $color: royalblue;

// .container {
//   h1 {
//    color: $color;
//   }
// }

------------------------------------------

/* - 변환을 해도 그대로 css코드로 들어감 */

/* $color: royalblue;
.container {
  h1 {
   color: $color;
  }
} * /
```

## 중첩 with SassMeister

    https://www.sassmeister.com/
    왼쪽에는 SCSS 코드가, 오른쪽에는 CSS 코드가 변환된 내용을 바로바로 볼 수 있는 사이트

## 상위(부모) 선택자 참조

    & - 상위 선택자 참조

```scss
// & - 상위 선택자 참조

// SCSS
.btn {
  position: absolute;
  &.active {
    color: red;
  }
}

.list {
  li {
    &:last-child {
      margin-right: 0;
    }
  }
}

.fs {
  &-small {
    font-size: 12px;
  }
  &-medium {
    font-size: 14px;
  }
  &-large {
    font-size: 16px;
  }
}
```

```css
/* css */
.btn {
  position: absolute;
}
.btn.active {
  color: red;
}

.list li:last-child {
  margin-right: 0;
}

.fs-small {
  font-size: 12px;
}
.fs-medium {
  font-size: 14px;
}
.fs-large {
  font-size: 16px;
}
```

## 중첩된 속성

- font-weight, font-size, font-family 처럼 font- 로 동일하게 시작하는 경우 `*네임스페이스`가 동일하다 라고한다.
- `*네임스페이스` - 이름을 통해 구분 가능한 범위를 만들어내는 것으로 일종의 `유효범위를 지정하는 방법`을 말합니다.

```scss
// 중첩된 속성
.box {
  font: {
    weight: bold;
    size: 10px;
    family: sans-serif;
  }
  margin: {
    top: 10px;
    left: 20px;
  }
  padding: {
    top: 10px;
    bottom: 40px;
    left: 20px;
    right: 30px;
  }
}
```

```css
font: {
  weight: bold;
  size: 10px;
  family: sans-serif;
}
margin: {
  top: 10px;
  left: 20px;
}
padding: {
  top: 10px;
  bottom: 40px;
  left: 20px;
  right: 30px;
}
```

## 변수

```scss
// 변수 (Variables) - 재활용이 가능한 용도로 사용하는 개념
// SCSS
$size: 200px; // 전역변수

.container {
  $size: 100px; // 선언 내부에서만 사용가능(유효범위)
  position: fixed;
  top: $size;
  .item {
    $size: 50px;
    width: $size;
    height: $size;
    transform: translateX($size);
  }
  left: $size; // 해당하는 변수가 재할당되면 재할당된 코드 아래쪽은 재할당된 코드가 적용
}

.box {
  width: $size;
}
```

```css
/* CSS */
.container {
  position: fixed;
  top: 100px;
  left: 50px;
}
.container .item {
  width: 50px;
  height: 50px;
  transform: translateX(50px);
}

.box {
  width: 200px;
}
```

## 산술 연산

```scss
// SCSS
div {
  $size: 30px;
  width: 20px + 20px;
  height: 40px - 10px;
  font-size: 10px * 2;
  // margin: 30px / 2; // 30px / 2;
  margin: (30px / 2); // 첫번째 방법 - 15px;
  margin: $size / 2; // 두번째 방법 - 15px; 변수를 통해 나누게 되면 scss로 연산을 하겠다라는 의미로 보기때문에 연산된다.
  margin: 10px + 12px / 2; // 세번째 방법 - 16px;  기본적인 산술 연산이 들어가 있기 때문에 단축속성을 구분하는 용도가 아니라는 것을 명확하게 함
  padding: 20px % 7;
}

span {
  font-size: 10px;
  line-height: 10px;
  font-family: serif;
  // font-size / line-height로 구분 - font-family라는 내용도 명시해줘야 동작함
  font: 10px / 10px serif; // scss 에서는 이러한 이유로 단순하게 / 기호를 사용했을때 따로 연산하지 않음
}

.div {
  // width: 100% - 200px; // 산술연산을 하려면 단위가 동일해야한다.
  width: calc(100% - 200px); // 출력이 될 수 있는 구조
}
```

```css
/* CSS */
div {
  width: 40px;
  height: 30px;
  font-size: 20px;
  margin: 15px;
  margin: 15px;
  margin: 16px;
  padding: 6px;
}

span {
  font-size: 10px;
  line-height: 10px;
  font-family: serif;
  font: 10px/10px serif;
}

.div {
  width: calc(100% - 200px);
}
```

## 재활용 (Mixins)

```scss
// SCSS
@mixin center {
  display: flex;
  justify-content: center;
  align-items: center;
}
//        매개변수
@mixin box($size: 100px, $color: tomato) {
  width: $size;
  height: $size;
  background-color: $color;
}

.container {
  @include center;
  .item {
    //           인수
    @include box(200px, red);
  }
}
.box {
  //            키워드 인수
  @include box($color: green);
  @include center;
}
```

```css
/* CSS */
.container {
  display: flex;
  justify-content: center;
  align-items: center;
}
.container .item {
  width: 200px;
  height: 200px;
  background-color: red;
}

.box {
  width: 100px;
  height: 100px;
  background-color: green;
  display: flex;
  justify-content: center;
  align-items: center;
}
```

## 반복문

```scss
// for (let i = 0; i < 5; += 1) {
//  console.log(`loop-${i}`);
//}

// SCSS
@for $i from 1 through 5 {
  // ${} - scss의 보간법
  .box:nth-child(#{$i}) {
    // 보간
    width: 100px * $i;
  }
}
```

```css
/* CSS */
.box:nth-child(1) {
  width: 100px;
}

.box:nth-child(2) {
  width: 200px;
}

.box:nth-child(3) {
  width: 300px;
}

.box:nth-child(4) {
  width: 400px;
}

.box:nth-child(5) {
  width: 500px;
}
```

## 함수

```scss
// mixin - css코드의 모음정도로 생각, 속성과 값을 재활용하는 용도
@mixin center {
  display: flex;
  justify-content: center;
  align-items: center;
}

// 함수 따로 연산을 해서 반환된 결과로 사용하기위해 만들어내는 개념
@function ratio($size, $ratio) {
  @return $size * $ratio;
}

.box {
  $width: 100px;
  width: $width;
  // 16:9 100px 대비해서 56.25px
  //          (100px * 9) / 16 - 연산되는 순서
  height: ratio($width, 9/16);
  @include center;
}
```

```css
.box {
  width: 100px;
  height: 56.25px;
  display: flex;
  justify-content: center;
  align-items: center;
}
```

## 색상 내장 함수

```scss
// SCSS
.box {
  $color: royalblue;
  width: 200px;
  height: 100px;
  margin: 20px;
  border-radius: 10px;
  background-color: $color;
  &.built-in {
    // mix(첫번째 인수의 색상과 두번째 인수의 색상을 섞어서 새로운 색상을 내어줌)
    background-color: mix($color, red);
    // lighten(첫번째 인수에 해당하는 색상을 10%더 밝게 만들어주는 함수)
    background-color: lighten($color, 10%);
    // darken(첫번째 인수에 해당하는 색상을 10%더 어둡게 만들어주는 함수)
    background-color: darken($color, 10%);
    // saturate(첫번째 인수에 해당하는 채도를 10%더 높여주는 함수)
    background-color: saturate($color, 10%);
    // desaturate(첫번째 인수의 해당하는 채도를 10%더 낮춰주는 함수)
    background-color: desaturate($color, 10%);
    // grayscale(주어진 인수를 회색으로 만들어줌, 두번째 인수가 필요하지 않음)
    background-color: grayscale($color);
    // invert(주어진 인수의 색상을 반전시키는 함수)
    background-color: invert($color);
    // rgba(첫번째 인수로는 기본적인 색상을 추가, 두번째 인수로는 색상에 대한 투명도를 입력 .5 === 50%)
    background-color: rgba($color, 0.5);
  }
}
```

```css
/* CSS */
.box {
  width: 200px;
  height: 100px;
  margin: 20px;
  border-radius: 10px;
  background-color: royalblue;
}
.box.built-in {
  background-color: #a03571;
  background-color: #6d8ce8;
  background-color: #214cce;
  background-color: #3664ec;
  background-color: #4c6fd6;
  background-color: #919191;
  background-color: #be961e;
  background-color: rgba(65, 105, 225, 0.5);
}
```

## 데이터 종류

```scss
$number: 1; // .5, 100px, 1rem
$string: bold; // realtive, "../images/a.png"
$color: red; // blue: 문자가 아닌 색상데이터, #FFFF00, rhba(0, 0, 0, .1)
$boolean: true; // false
$null: null;
$list: orange, royalblue, yellow; // js의 배열과 유사
$map: (
  o: orange,
  r: royalblue,
  y: yellow,
); // 객체 데이터와 유사

// each 키워드를 통해 list안에 있는 데이터들을 반복적으로 c라는 이름의 변수에 담아서 중괄호 사이에서 처리
@each $c in $list {
  .box {
    color: $c;
  }
}

// map
@each $key, $value in $map {
  // $k, $v도 상관없음
  .box-#{$key} {
    color: $value;
  }
}

.box {
  width: 100px;
  color: red;
  position: relative;
  // null이라는 데이터를 추가하면 position에 해당하는 속성이 출력x
  position: null;
}
```

```css
/* $list */
.box {
  color: orange;
}

.box {
  color: royalblue;
}

.box {
  color: yellow;
}

/* map */
.box-o {
  color: orange;
}

.box-r {
  color: royalblue;
}

.box-y {
  color: yellow;
}

.box {
  width: 100px;
  color: red;
  position: relative;
}
```

## 재활용 @content

```scss
// SCSS
@mixin left-top {
  position: absolute;
  top: 0;
  left: 0;
  @content;
}

.container {
  width: 100px;
  height: 100px;
  @include left-top;
}

.box {
  width: 200px;
  height: 300px;
  @include left-top {
    // 필요에 따라 기본적인 mixin에 추가적인 내용을 더해서 해당 내용을 사용 할 수 있는 문법 제공
    bottom: 0;
    right: 0;
    margin: auto;
  }
}
```

```css
/* CSS */
.container {
  width: 100px;
  height: 100px;
  position: absolute;
  top: 0;
  left: 0;
}

.box {
  width: 200px;
  height: 300px;
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  margin: auto;
}
```

### vw, vh

- `Viewport Width`, `Viewport Height`
- 뷰포트를 기준으로 하는 단위 (1vw = 뷰포트 너비의 1% | 1vh = 뷰포트 높이의 1%)
- 뷰포트 영역 전체를 차지하게 하거나 일부분만 차지하게 하는데 유용

### em, rem

- em : 폰트를 기준으로 한 단위
- rem : 최상위 폰트를 기준으로 한 단위(html 요소)

```css
html {
  font-size: 62.5%; /* 100% = 16px, 62.5% = 10px 8 */
}
.title {
  font-size: 1.6rem; /* 16px */
}
.contens {
  font-size: 2rem; /* 20px */
}
```
