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

- `outline-style(required)`
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
- `outline-color`
  - outline-color: red;
  - outline-color: #ffffff;
  - outline-color: rgb(255, 0, 0);
  - outline-color: hsl(0, 100%, 50%);
- `outline-width`
  - thin, medium, thick, (in px, pt, cm, em, etc)
- `outline-offset`
  - 윤곽선과 요소의 가장자리/테두리 사이에 공간을 추가, 요소와 윤곽선 사이의 공간은 투명
- `outline`

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

- **text decoration**
  - `text-decoration-line` 속성은 텍스트에 장식선을 추가하는데 사용
  - `text-decoration-color` 속성은 텍스트 장식선 색상을 설정
  - `text-decoration-style` 속성은 데코레이션 라인의 스타일을 설정
  - `text-decoration-thickness` 속성은 데코레이션 선의 굵기를 설정

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

- `text-transform` 속성은 텍스트에서 대문자와 소문자를 지정하는 데 사용
- 모든 것을 대문자 또는 소문자로 바꾸거나, 각 단어의 첫 글자를 대문자로 바꾸는 데 사용

```css
h1 {
  text-transform: uppercase; /* 모두 대문자로 */
  text-transform: lowercase; /* 모두 소문자로 */
  text-transform: capitalize; /* 단어 첫 글자만 대문자 */
}
```

- `text-indent` : 텍스트의 첫 번째 줄 들여쓰기
- `letter-spacing` : 텍스트에서 문자 사이의 공백을 지정하는 데 사용
- `line-height` : 줄 사이의 공백을 지정하는 데 사용
- `word-spacing` : 텍스트에서 단어 사이의 공백을 지정하는 데 사용
- `white-space` : 요소 내부의 공백을 처리하는 방법을 지정

```css
p {
  text-indent: 20px;
  letter-spacing: 10px;
  line-height: 1;
  word-spacing: 5px;
  /* noweap, normal, pre */
  white-space: nowrap;
}
```

- `text-shadow` : 텍스트에 그림자를 추가

```css
h1 {
  /* 2px: 수펑그림자, 4px: 수직그림자 */
  text-shadow: 2px 4px;
  /* 색상추가 */
  text-shadow: 2px 4px red;
  /* 흐림효과(5px) 추가 */
  text-shadow: 2px 4px 5px red;
}
```

**Styling links**

- 링크의 상태
  - a:link - 방문하지 않은 정상적인 링크
  - a:visited - 사용자가 방문한 링크
  - a:hover - 사용자가 마우스를 가져가면 링크
  - a:active - 클릭하는 순간 링크

```css
/* 방문하지 않은 정상적인 링크 */
a:link {
  color: red;
}

/* 사용자가 방문한 링크 */
a:visited {
  color: green;
}

/* 사용자가 마우스를 가져가면 링크 */
a:hover {
  color: hotpink;
}

/* 클릭하는 순간 링크 */
a:active {
  color: blue;
}
```

**링크 상태에 대한 규칙**

- a:hover는 반드시 a:link 및 a:visit 뒤에 와야 한다.
- a:active는 반드시 a:hover 다음에 와야 한다.

## Display Property

- Block 요소 : 줄바꿈 되어 한 줄 차지, 사용 가능한 전체 너비를 차지(기본 너비값 100%)

```
- <div>
- <h1> ~ <h6>
- <p>
- <form>
- <header>
- <footer>
- <section>
- <article>
- <nav>
- <aside>
- <table>, <th>, <td>
- <figure>
```

- Inline 요소 : 줄바꿈 없이 나란히 배치, 필요한 만큼의 너비만 차지

```
- <span>
- <a>
- <img>
- <em>
- <b>
- <strong>
- <video>, <audio>
```

- display: none; : 삭제 및 재생성 없이 요소를 숨기고 표시
- visibility: hidden; : 요소는 숨겨지지만 공간은 그대로 차지, 레이아웃에 영향

```css
/*
  줄 바꿈 없이 다른 요소들과 나란히 배치되지만,
  inline 요소에서 불가능하던 width, height, margin, padding 속성을 사용가능
*/
span {
  display: inline-block;
}

/* 대표적인 inline-block 요소로 <img>, <button>, <input>, <select> 태그 등이 있다. */
```

- 각 요소들 중앙 정렬 방법
  - Block 요소 : `margin: auto;`
  - Inline/Inline-Block 요소 : 부모 요소에 `text-align: center;`

## Position Property

- static(정적)
  - HTML요소는 기본적으로 정적으로 배치된다.
  - 정적 위치 요소는 top, bottom, left, right 속성의 영향을 받지 않음
  - position: static이 있는 요소는 특별한 방식으로 배치되지 않고, 페이지의 흐름에 따라 배치
- relative(상대)
  - position: relative;는 정상 위치를 기준으로 배치
  - 상대적으로 배치된 top, bottom, left, right 속성을 설정하면 원래 위치에서 멀어짐
- fixed(고정)
  - position: fixed;는 뷰포트에 상대적으로 위치, 페이지 스크롤시 항상 같은 위치에 유지
  - top, bottom, left, right 속성은 요소의 위치를 지정하는데 사용
  - 고정 요소는 일반적으로 위치할시 페이지에 공백을 남기지 않음
- absolute(절대)
  - position: absolute;는 가장 가까운 위치에 있는 부모 요소를 기준으로 배치
  - 절대 위치 요소에 위치 지정 요소가 없으면, 문서 본문을 사용, 페이지 스크롤과 함께 이동
  - 절대 위치 요소는 일반 흐름에서 제거되며, 요소와 겹칠 수 있음
- sticky(끈끈한)

## Z-Index

- 요소가 배치되면 다른 요소와 겹칠 수 있다.
- z-index 속성은 요소의 순서를 지정(요소가 다른 요소의 앞이나 뒤에 배치되어야 하는지)
- 양수(+) 나 음수(-) 값으로 순서를 가질 수 있다.
- \*위치 지정 요소 및 플렉스 요소에서만 작동

## Overflow

- overflow 속성은 요소가 지정된 영역에 맞지 않을 때 자를지 혹은 스크롤바를 추가할지 여부를 지정
  - visible : 기본값
  - hidden : overflow가 잘리고 나머지 내용이 안보임
  - scroll : overflow가 잘리고 스크롤바가 추가되어 나머지 내용을 볼 수 있음
  - auto : scroll과 유사하지만 필요할때만 스크롤바 추가
  - overflow-x : 콘텐츠 왼쪽/오른쪽 가장자리로 수행할 작업을 지정 <!-- horizontal -->
  - overflow-y : 콘텐츠 위쪽/아래쪽 가장자리로 수행할 작업을 지정 <!-- vertical -->

## Float

- left : 요소는 왼쪽에 떠있다.
- right : 요소는 오른쪽에 떠있다.
- none : 기본값, 요소가 부동하지 않음
- inherit : 상위요소의 float 값을 상속

```css
img {
  float: left;
  float: right;
  float: none;
  float: inherit;
}
```
