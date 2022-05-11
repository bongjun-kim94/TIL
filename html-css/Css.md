# CSS (Cascading Style Sheets)

## margins

- margin 속성은 정의된 테두리 외부 요소 주변의 공간을 제어하는것

- margin-top | margin-right | margin-bottom | margin-left

```css
/* Margin - Individual Sides */
p {
  /*      top|right|bottom|left */
  margin: 20px 30px 40px 50px;
}

p {
  /*    top|left,right|bottom */
  margin: 20px 30px 40px;
}

p {
  /* top,bottom|left,right */
  margin: 20px 40px;
}

p {
  /* top, right, bottom, left */
  margin: 20px;
}
```

- h1 + h2 여백은 (50 + 20 = 70) 이지만, 때때로 두 여백중 가장 큰 여백과 동일한 단일 여백으로 축소. 실제는 50px

- 상, 하 여백에서만 발생 좌, 우 에서는 발생x

```css
/* Margin Collapse */
h1 {
  /* margin-bottom: 50px; */
  margin: 0 0 50px 0;
}

h2 {
  /* margin-top: 20px; */
  margin: 20px 0 0 0;
}
```

## padding

- padding 속성은 정의된 테두리 내부의 요소 컨텐츠 주위에 공간을 만드는데 사용

- padding-top | padding-right | padding-bottom | padding-left

```css
div {
  /* padding-top | padding-right | padding-bottom | padding-left */
  padding-top: 20px;
  padding-right: 30px;
  padding-bottom: 40px;
  padding-left: 50px;
}

/* 요소의 너비는 300px 이지만, 실제 너비는 (300px + 25px + 25px = 350px) 이다. */
div {
  width: 300px;
  padding: 25px;
}
```

- padding의 크기와 상관없이 너비를 300px로 유지하려면, `box-sizing` 속성 사용

```css
div {
  width: 300px;
  padding: 25px;
  box-sizing: border-box;
}
```

## width & height

- width: 요소의 너비값을 설정
- height: 요소의 높이값을 설정
- min-width: 요소의 최대 너비값을 설정
- min-height: 요소의 최소 너비값을 설정
- max-width: 요소의 최대 너비값을 설정
- max-height: 요소의 최대 높이값을 설정

## Outline

    요소를 눈에 띄게 만들기 위해, 테두리 outside 요소 주위에 그려지는 선

- outline-style(required)
  - dotted- 점선 윤곽을 정의합니다.
  - dashed- 점선 윤곽을 정의합니다.
  - solid- 실선을 정의합니다.
  - double- 이중 윤곽선 정의
  - groove- 3D 홈이 있는 윤곽을 정의합니다.
  - ridge- 3D 융기된 윤곽을 정의합니다.
  - inset- 3D 삽입 윤곽을 정의합니다.
  - outset- 3D 아웃셋 아웃라인 정의
  - none- 윤곽을 정의하지 않음
  - hidden- 숨겨진 윤곽선 정의
- outline-color
  - outline-color: red;
  - outline-color: #ffffff;
  - outline-color: rgb(255, 0, 0);
  - outline-color: hsl(0, 100%, 50%);
- outline-width
  - thin, medium, thick, (in px, pt, cm, em, etc)
- outline-offset
  - 윤곽선과 요소의 가장자리/테두리 사이에 공간을 추가, 요소와 윤곽선 사이의 공간은 투명
- outline

```css
p.ex {
  /* 목록에서 1개, 2개, 3개의 값으로 지정. 값의 순서는 상관없다. */
  outline: solid 5px red;
}
```

## Text

```css
h1 {
  color: red;
  /* center, left, right, justify */
  /* 
    text-align: justify; : 각 줄의 모든 너비가 동일, 왼쪽 및 오른쪽 여백이 직선이 되도록 늘어남. 
  */
  text-align: center;
}

p {
  /* text-align-last 속성은 텍스트의 마지막 줄을 정렬하는 방법을 지정 */
  /* right, center, justify */
  text-align-last: right;
}
```

- Text Direction

  direction 또는 unicode-bidi 속성을 사용하여 요소의 텍스트 방향을 변경할 수 있다.

```css
p {
  direction: rtl;
  unicode-bidi: bidi-override;
}
```

- Vertical Alignment(수직정렬)
  vertical-align 속성은 요소의 수직 정렬을 설정

```css
img {
  vertical-align: baseline;
  vertical-align: text-top;
  vertical-align: text-bottom;
  vertical-align: sub;
  vertical-align: super;
}
```

- text decoration
  - text-decoration-line 속성은 텍스트에 장식선을 추가하는데 사용
  - text-decoration-color 속성은 텍스트 장식선 색상을 설정
  - text-decoration-style 속성은 데코레이션 라인의 스타일을 설정
  - text-decoration-thickness 속성은 데코레이션 선의 굵기를 설정

```css
h1 {
  text-decoration-line: overline;
  (required)/*윗줄*/text-decoration-line: line-through; /* 가운데줄 */
  text-decoration-line: underline; /* 밑줄 */
  text-decoration-line: overline underline; /* 윗줄 아랫줄 함께사용
   */

  text-decoration-color: red;

  /* solid, double, dotted, dashed, wavy  */
  text-decoration-style: solid;

  /* 5px, 5% */
  text-decoration-thickness: auto;
}
```

- HTML의 모든 링크에는 밑줄이 생기는데 `text-decoration: none`을 사용해서 밑줄제거

- text-transform 속성은 텍스트에서 대문자와 소문자를 지정하는 데 사용
- 모든 것을 대문자 또는 소문자로 바꾸거나, 각 단어의 첫 글자를 대문자로 바꾸는 데 사용

```css
h1 {
  text-transform: uppercase; /* 모두 대문자로 */
  text-transform: lowercase; /* 모두 소문자로 */
  text-transform: capitalize; /* 단어 첫 글자만 대문자 */
}
```
