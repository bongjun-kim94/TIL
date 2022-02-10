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