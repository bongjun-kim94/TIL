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
  /* 요소의 전체 너비와 높이에 패딩과 테두리가 포함됨 */
  box-sizing: border-box;
}
```

## width & height

- width: 요소의 너비값을 설정
- height: 요소의 높이값을 설정
- min-width: 요소의 최대 너비값을 설정
- min-height: 요소의 최소 너비값을 설정, 필요한 경우 축소되지만 원래 크기보다 크게 확대되지는 않는다.
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
  - position: sticky; : 고정 요소는 스크롤 위치에 따라 상대 요소와 고정 요소 사이를 전환
  - 주어진 오프셋 우치가 뷰포트에서 만날 때까지 상대적으로 배치된 다음 제자리에 '고정'

```css
ul {
  position: sticky;
  top: 0;
}
```

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

- float으로 컨텐츠를 띄워 붙이고 width 값을 100%/n(개수) 만큼 주면 동일한 간격으로 정렬됨
- ex) 4개 = 25%, 5개 = 20%, 6개 = 16.66%

## Center Align

- margin: auto;
  - 블록요소 (예: `<div>`)를 가로로 가운데에 맞출때 사용

```css
.center {
  margin: auto;
  width: 50%;
  border: 1px solid black;
  padding: 5px;
}
```

- text-align: center;
  - 요소 내부의 텍스트 가운데 정렬

```css
.center {
  text-align: center;
  border: 1px solid black;
}
```

- margin: 0 auto;
  - 이미지를 가운데에 맞추려면 왼쪽 및 오른쪽 여백을 auto로 설정하고, block 요소로 만듬

```css
img {
  display: block;
  width: 100px;
  margin: 0 auto;
}
```

- position: absolute;
  - 요소를 정렬하는 방법

```css
.right {
  position: absolute;
  right: 0px;
  width: 200px;
  border: 1px solid black;
  padding: 5px;
}
```

- float
  - 요소를 정렬하는 방법

```css
.right {
  float: right;
  width: 200px;
  border: 1px solid black;
  padding: 5px;
}
```

- Clearfix Hack
  - 요소가 포함된 요소보다 크고 떠있는 경우 컨테이너 외부에서 오버플로된다.

```css
.clearfix::after {
  content: "";
  clear: both;
  display: block;
}
```

- Padding + text-align: center;
  - 수직과 수평 가운데 맞춤

```css
.center {
  padding: 50px 0;
  border: 1px solid black;
  text-align: center;
}
```

- Line-Height
  - height 속성과 line-height 속성을 동일한 값으로 사용

```css
.center {
  line-height: 100px;
  height: 100px;
  border: 1px solid black;
  text-align: center;
}

/* 텍스트가 여러 줄일 경우 */
.center p {
  line-height: 1.5;
  display: inline-block;
  vertical-align: middle;
}
```

## Flexbox

- 수직 중앙 정렬, IE10 및 이전 버전에서 지원되지 않음
- 인터페이스 내의 아이템 간 공간 배분과 강력한 정렬 기능을 제공하기 위한 1차원 레이아웃 모델로 설계되었다.
- justify-content : 주축을 따라 flex 항목 행을 정렬하는 방식을 지정
  - flex-start: 초기값
  - flex-end : flex 항목 행의 마지막 항목이 flex 컨테이너의 끝선에서 정렬됨
  - center : flex 항목들이 flex 항목 행의 가운데 정렬
  - space-around : 시작선 및 끝선과 flex 항목간 공간도 균등 배분에 고려하므로 시작선 및 끝선과 flex 항목 간의 공간의 크기를 1로 배분한다면 flex 항목 사이의 공간은 2로 배분합니다.
  - space-between : 주축 방향 여유 공간을 flex 항목 사이의 공간에 균등배분
  - space-evenly : 여유 공간을 flex 항목 사이의 공간 및 시작선 및 끝선과 flex 항목 간의 공간에 모두 균등하게 배분

```css
.center {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 300px;
  border: 1px solid black;
}
```

## Flex Container

- 플렉스 컨테이너 속성

  - flex-direction : 플렉스 항목 방향을 정의
  - flex-wrap : 플렉스 항목을 래핑할지 여부 지정
  - flex-flow : flex-direction flex-wrap 모두 설정하기 위한 약식 속성
  - justify-content : 플렉스 항목을 정렬하는데 사용
  - align-items : 플렉스 항목을 정렬하는데 사용
  - align-content : 플렉스 하인을 정렬하는데 사용

```css
.flex-container {
  display: flex;
  /* flex-direction */
  flex-direction: column; /* 플렉스 항목을 수직으로 쌓는다. */
  flex-direction: column-reverse; /* 플렉스 아이템을 수직으로(아래에서 위) 쌓는다. */
  flex-direction: row; /* 플렉스 항목을 가로로 쌓는다. */
  flex-direction: row-reverse; /* 플렉스 항목을 가로로(오른쪽에서 왼쪽) 쌓는다  */

  /* flex-wrap */
  flex-wrap: wrap; /* 필요한 경우 플렉스 항목이 너비에 맞춰서 다음으로 넘어감 */
  flex-wrap: nowrap; /* 기본값. 플렉스 항목이 래핑되지 않도록 지정 */
  flex-wrap: wrap-reverse; /* 유연한 항목이 필요한 경우 역순으로 래핑 */

  /* flex-flow */
  flex-flow: row wrap;

  /* justify-content */
  justify-content: center; /* 컨테이너 중앙에 플렉스 항목을 정렬 */
  justify-content: flex-start; /* 컨테이너 시작 부분에 플렉스 항목을 정렬(기본값) */
  justify-content: flex-end; /* 컨테이너 끝에 플렉스 항목을 정렬 */
  justify-content: space-around; /* 플렉스 항목에 균일한 간격을 만들어줌 */
  justify-content: space-between; /* 플렉스 항목 사이에 균일한 간격지정 */

  /* align-items */
  align-items: center; /* 컨테이너 중간에 플렉스 항목을 정렬 */
  align-items: flex-start; /* 컨테이너 맨 위에 플렉스 항목을 정렬 */
  align-items: flex-end; /* 컨테이너 맨 아래 플렉스 항목을 정렬 */
  align-items: stretch; /* 플렉스 항목을 확장하여 컨테이너를 채움(기본값) */
  align-items: baseline; /* 기준선과 같은 플렉스 항목을 정렬 */
}
```

## Flex Items

- order : 플렉스 항목의 순서를 지정
- flex-grow : 나머지 플렉스 항목에 비해 플렉스 항목이 얼마나 커질지 지정
- flex-shrink : 나머지 플렉스 항목에 비해 플렉스 항목이 축소되는 정도를 지정
- flex-basis : 플렉스 항목의 초기 길이를 지정
- flex : 축약형. flex-grow, flex-shrink, flex-basis 순서로 지정됨
- align-self : 유연한 컨테이너 내부에서 선택한 항목의 정렬을 지정

```html
<div class="flex-container">
  <div style="order: 3">1</div>
  <div style="order: 1">2</div>
  <div style="order: 2">3</div>

  <div style="flex-grow: 1">1</div>
  <div style="flex-grow: 2">2</div>
  <div style="flex-grow: 7">3</div>

  <div>1</div>
  <!-- 두 번째 플렉스 항목이 다른 플렉스 항목만큼 줄어들지 않도록 합니다. -->
  <div style="flex-shrink: 0">2</div>
  <div>3</div>

  <div>1</div>
  <div style="align-self: flex-start">2</div>
  <div style="align-selg: flex-end">3</div>
</div>
```

- flex-basis 속성
  - 항목의 크기를 결정한다. 기본값은 auto, 항목이 크기를 갖고 있는지 확인하고, 항목의 크기가 100px 이면 flex-basis 값으로 100px이 사용됨
  - flex 항목에 크기가 지정되어 있지 않으면, flex 항목의 내용물 크기가 flex-basis 값으로 사용됨, 따라서 flex 컨테이너에서 `display: flex;` 속성만을 지정하면 flex 항목들이 각 내용물 크기만큼 공간을 차지함
- flex-grow 속성
  - flex-grow 값을 양수로 지정하면 flex 항목별로 주축 방향 크기가 flex-basis 값 이상으로 늘어날 수 있게 됩니다.
  - 모든 항목의 flex-grow 값을 1로 지정하면 사용가능한 공간은 각 항목에게 동일하게 분배되며, 각 항목은 주축을 따라 분배받은 값만큼 사이즈를 늘려 공간을 차지
- flex-shrink 속성
  - flex-grow 속성이 주축에서 남는 공간을 항목들에게 분배하는 방법을 결정한다면, flex-shrink 속성은 주축의 공간이 부족할때 각 항목의 사이즈를 줄이는 방법을 정의
  - flex-grow, flex-shrink의 값은 비율이다. flex 항목의 flex 속성을 모두 1 1 200px로 지정하고, 한 항목만 크기가 늘어나는 비율을 타 항목의 두배로 하고 싶으면 해당 flex 항목의 flex 속성을 2 1 200px 지정하면 된다.
- 축약형 속성 flex
  - 보통은 flex-grow, flex-shrink, flex-basis값을 각각 사용하지 않고, 세 속성을 한번에 지정하는 flex 축약형을 많이사용
  - flex-grow, flex-shrink, flex-basis 순서로 지정됨
  - flex 축약형 표현에 사용할 수 있는 미리 정의된 축약 값
    - flex: initial : flex: 0 1 auto 로 지정한 것과 동일
    - flex: auto : flex: 1 1 auto 로 지정한 것과 동일, flex: initial 과는 주축 방향 여유 공간이 있을때 flex 항목들이 늘어나서 주축 방향 여유 공간을 채우는 점만 다름
    - flex: none : flex: 0 0 auto 으로 지정한 것과 동일, flex 컨테이너 크기 변화에도 flex 항목 크기는 변하지 않고 flex-basis를 auto로 지정했을때 정해지는 크기로 결정됨
    - flex: `<positive-number>`
  - 이 축약형은 더 축약해서 flex: 1 이나, flex: 2 처럼 쓸 수도 있는데, 이는 flex-grow만 지정하고 나머지는 1 0 으로 사용한다는 뜻. 따라서 flex: 2는 flex: 2 1 0와 동일하게 처리됨

## Combinators

- 결합자는 선택자 간의 관계를 설명한다.
  - 자손 선택자 (공백): 지정된 요소의 자손인 모든 요소와 일치
  - 자식 선택자 (>): 지정된 요소의 자식인 모든 요소를 선택
  - 인접한 형제 선택자(+): 다른 특정 요소 바로 뒤에 있는 요소를 선택, 형제 요소는 동일한 부모 요소를 가져야함
  - 일반 형제 선택자(~): 지정된 요소의 다음 형제인 모든 요소를 선택

```css
/* 자손선택자 */
div p {
  background-color: red;
}

<div>
  <p>test text</p>
</div>

/* 자식 선택자 */
div > p {
  background-color: red;
}

<div>
  <p>test text</p>
  /* css 적용안됨 */
  <section>
    <p>test text2</p>
  </section>
</div>

/* 인접 형제 선택자 */
div + p {
  background-color: red;
}

<div>
  <p>test text</p>
  <p>test text</p>
</div>
<p>test text</p> /* red */
<div>
  <p>test text</p>
  <p>test text</p>
</div>
<p>test text</p> /* red */

/* 일반 형태 선택자 */
div ~ p {
  background-color: red;
}

<div>
  <p>test text</p>
  <p>test text</p>
</div>
<p>test text</p> /* red */
<span>test text</span>
<p>test text</p> /* red */
```

## Attributes Selectors

- attribute 선택자 : [attribute] 선택자는 지정된 속성을 가진 요소를 선택하는데 사용

```html
<style>
  /* 대상 속성이 있는 모든 <a> 요소를 선택 */
  a[target] {
    background-color: red;
  }
</style>

<a href="https://www.google.com">google</a>
<!-- red -->
<a href="https://www.google.com" target="_blanc">google</a>
<!-- red -->
<a href="https://www.google.com" target="_top">google</a>
```

- attribute="value" 선택자 : [attribute="value"] 선택자는 지정된 속성과 값을 가진 요소를 선택하는데 사용

```html
<style>
  a[target="_blank"] {
    background-color: red;
  }
</style>

<a href="https://www.google.com">google</a>
<!-- red -->
<a href="https://www.google.com" target="_blanc">google</a>
<a href="https://www.google.com" target="_top">google</a>
```

- attribute~="value" 선택자 : [attribute~="value"] 선택자는 지정된 단어를 포함하는 속성 값을 가진 요소를 선택하는데 사용

```html
<style>
  [title~="flower"] {
    border: 1px solid black;
  }
</style>

<!-- black -->
<img src="images/test.png" title="flower" width="200" height="150" />
<img src="images/test2.png" title="Dog" width="300" height="200" />
```

- attribute|="value" 선택자 : [attribute |= "value"] 선택자는 지정된 속성이 있는 요소를 선택하는데 사용

```html
<style>
  [class|="top"] {
    background-color: red;
  }
</style>

<!-- red -->
<h2 class="top-header">Hello</h2>
<p class="topText">World!</p>
<p class="topContent">Last Text</p>
```

- attribute^="value" 선택자 : [attribute^="value"] 선택자는 값이 지정된 값으로 시작하는 지정된 속성을 가진 요소를 선택하는데 사용

```html
<style>
  [class^="top"] {
    background-color: red;
  }
</style>

<!-- red -->
<h2 class="top-header">Hello</h2>
<!-- red -->
<p class="topText">World!</p>
<!-- red -->
<p class="topContent">Last Text</p>
```

- attribute$="value" 선택자 : [attribute$="value"] 선택자는 속성값이 지정된 값으로 끝나는 요소를 선택하는데 사용

```html
<style>
  [class$="test"] {
    background-color: red;
  }
</style>

<!-- red -->
<div class="first_test">First Div</div>
<div class="second">Second Div</div>
<!-- red -->
<div class="last-test">Last Div</div>
<!-- red -->
<p class="ptest">First P Tag</p>
```

- attribute*="value" 선택자 : [attribute*="value"] 선택자는 속성 값에 지정된 값이 포함된 요소를 선택하는데 사용

```html
<style>
  [class*="test"] {
    background-color: red;
  }
</style>

<!-- red -->
<div class="first_test">First Div</div>
<div class="second">Second Div</div>
<!-- red -->
<div class="last-test">Last Div</div>
<!-- red -->
<p class="ptest">First P Tag</p>
```

```css
/* styling example */
input[type="text"] {
  width: 200px;
  display: block;
  background-color: red;
}

input[type="button"] {
  width: 300px;
  display: block;
  margin-left: 20px;
}
```

## Text Effects

- text-overflow : 표시되지 않는 오버플로 컨텐츠가 사용자에게 어떻게 보여져야 하는지를 지정
- word-wrap : 긴 단어를 줄 바꿈 할 수 있다.
- word-break : 줄 바꿈 규칙을 지정
- writing-mode : 텍스트 줄을 가로로 배치할지 세로로 배치할지 지정

```css
/* text-overflow */
p.test1 {
  white-space: nowrap;
  width: 150px;
  border: 1px solid black;
  overflow: hidden;
  text-overflow: clip; /* default */
}

p.test2 {
  white-space: nowrap;
  width: 150px;
  border: 1px solid black;
  overflow: hidden;
  text-overflow: ellipsis; /* 마지막에 ···표시 */
}

/* word-wrap */
p {
  word-wrap: break-word;
}

/* word-break */
p.test1 {
  word-break: keep-all;
}

p.test2 {
  word-break: break-all;
}

/* writing-mode */
p.test1 {
  writing-mode: horizontal-tb;
}

span.text2 {
  writing-mode: vertical-rl;
}

p.test2 {
  writing-mode: vertical-rl;
}
```

## 2D Transforms

- transform
  - translate() : 현재 위치에서 요소를 이동합니다 (X축 및 Y축에 대해)
  - rotate(): 주어진 각도에 따라 요소를 시계 뱡향 또는 역방향으로 회전
  - scale(): 요소의 크기를 늘리거나 줄인다.
  - scaleX(): 요소의 너비를 늘이거나 줄인다.
  - scaleY(): 요소의 높이를 높이거나 낮춘다.
  - skewX(): 지정된 각도만큼 X축을 따라 요소를 기울임
  - skewY(): 지정된 각도만큼 Y축을 따라 요소를 기울임
  - skew(): 지정된 각도만큼 X및 Y축을 따라 요소를 기울임
  - matrix(): 모든 2D변환 방법을 하나로 결합
    - 매개변수 : matrix(scaleX(), skewY(), skewX(), scaleY(), translateX(), translateY())

```css
/* translate() */
div {
  /* 오른쪽으로 100px 아래로 100px 이동 */
  transform: translate(100px, 100px);
}

/* rotate() */
div {
  /* 시계 방향으로 30도 회전 */
  transform: rotate(30deg);
  /* 시계 반대 방향으로 50도 회전 */
  transform: rotate(-50deg);
}

/* scale() */
div {
  /* div 요소를 원래 크기의 가로 2배, 높이 3배로 늘린다   */
  transform: scale(2, 3);
  /* div 요소를 우너래 너비와 높이의 절반으로 줄인다 */
  transform: scale(0.5, 0.5);
}

/* scaleX() */
div {
  /* 원래 너비의 2배 */
  transform: scaleX(2);
  /* 원래 너비의 절반 */
  transform: scaleX(0.5);
}

/* scaleY() */
div {
  /* 원래 높이의 2배 */
  transform: scaleY(2);
  /* 원래 높이의 절반 */
  transform: scaleY(0.5);
}

/* skewX() */
div {
  /* X축을 따라 20도 기울임 */
  transform: skewX(20deg);
}

div {
  /* Y축을 따라 20도 기울임 */
  transform: skewY(20deg);
}

/* skew() */
div {
  /* X축을 따라 20도, Y축을 따라 30도 기울임 */
  transform: skew(20deg, 30deg);
  /* 두번째 매개변수를 지정하지 않으면 값이 0, X축을 따라 요소를 20도 기울임 */
  transform: skew(20deg);
}

/* matrix() */
div {
  transform: matrix(1, -0.3, 0, 1, 50, 100);
}
```

## 3D Transforms

- transform
  - rotateX() : X축을 중심으로 요소를 지정된 각도로 회전
  - rotateY() : Y축을 중심으로 요소를 지정된 각도로 회전
  - rotateZ() : Z축을 중심으로 요소를 지정된 각도로 회전

```css
.myDiv {
  /* X축을 중심으로 100도 회전 */
  transform: rotateX(100deg);
  /* Y축을 중심으로 100도 회전 */
  transform: rotateY(100deg);
  /* Z축을 중심으로 100도 회전 */
  transform: rotateZ(100deg);
}
```

## Transitions

    전환 효과를 만드려면 다음 두 가지를 지정해야 한다.
    · 효과 추가 CSS 속성
    · 효과 지속 시간

- transition : CSS 전환을 사용하면 주어진 기간 동안 속성 값을 부드럽게 변경
- transition-delay : 전환 효과에 대한 초를 지정
- transition-duration : transition이 끝날 때까지 걸리는 시간
- transition-property : transition이 적용될 속성을 정함
- transition-timing-function
  - ease : 느린 시작, 빠른 시작, 느린 종료로 전환 효과를 지정
  - linear : 처음부터 끝까지 동일한 속도로 전환 효과를 지정
  - ease-in : 느린 시작으로 전환 효과를 지정
  - ease-out : 느린 끝으로 전환 효과를 지정
  - ease-in-out : 느린 시작과 끝으로 전환 효과를 지정
  - cubic-bezier(n,n,n,n) : 3차 베지어 함수에서 교유한 값을 정의

```css
/* transition */
div {
  transition: width 2s, height 4s;
}

/* transition-timing-function */
.div1 {
  transition-timing-function: linear;
}
.div2 {
  transition-timing-function: ease;
}
.div3 {
  transition-timing-function: ease-in;
}
.div4 {
  transition-timing-function: ease-out;
}
.div5 {
  transition-timing-function: ease-in-out;
}

/* transition-delay */
div {
  /* 시작하기 전에 1초의 지연 */
  transition-delay: 1s;
}

/* transition + transformation */
div {
  transition: width 1s, height 1s, transform 1;
}
```

## CSS Animations

    애니메이션을 사용하면 요소를 한 스타일에서 다른 스타일로 점진적으로 변경할 수 있다.

- @keyframes : 애니메이션이 특정 시간에 현재 스타일에서 새 스타일로 점차 변경됨
- animation-name
- animation-duration : 애니메이션을 완료하는데 걸리는 시간, 기본값 0초
- animation-delay : 애니메이션 시작에 대한 지연을 지정, 음수 값을 사용하면 애니메이션이 N초 동안 이미 재생된 것처럼 시작
- animation-iteration-count : 애니메이션이 실행되어야 하는 횟수를 지정
- animation-direction : 애니메이션을 앞으로, 뒤로 또는 번갈아 재생 여부 지정
  - normal : 애니메이션은 정상적으로 재생, 기본값
  - reverse : 애니메이션이 역방향으로 재생
  - alternate : 애니메이션이 먼저 앞으로 재생된 다음 뒤로 재생
  - alternate-reverse : 애니메이션이 먼저 뒤로 재생된 다음 앞으로 재생
- animation-timing-function : 애니메이션의 속도 곡선을 지정
  - ease : 느린 시작, 빠른 시작, 느린 종료로 전환 효과를 지정
  - linear : 처음부터 끝까지 동일한 속도로 전환 효과를 지정
  - ease-in : 느린 시작으로 전환 효과를 지정
  - ease-out : 느린 끝으로 전환 효과를 지정
  - ease-in-out : 느린 시작과 끝으로 전환 효과를 지정
  - cubic-bezier(n,n,n,n) : 3차 베지어 함수에서 교유한 값을 정의
- animation-fill-mode : 애니메이션은 첫 번째 키프레임이 재생되기 전이나 마지막 키프레임이 재생된 후에 요소에 영향을 주지 않습니다. 하지만 이 속성은 이 동작을 재정의 할 수 있다.
  - none : 기본값, 애니메이션은 실행 전후에 요소에 스타일을 적용하지 않음
  - forwards : 요소는 마지막 키프레임에 의해 설정된 스타일 값을 유지
  - backwards : 요소는 첫 번째 키프레임에 의해 설정된 스타일 값(방향에 따라 다름)을 가져오고 진행 시간동안 값을 유지
  - both : 애니메이션은 앞뒤 모두에 대한 규칙을 따르며 애니메이션 속성을 양방향으로 확장
- animation

```css
@keyframes example {
  from { /* 0% 시작 */
    background-color: red;
  }
  to { /* 100% 완료 */
    background-color: green;
  }
}

div {
  width: 100px;
  height: 100px;
  background-color: red;
  animation-name: example;
  animation-duration: 2s;
}

@keyframes example {
  0% {background-color: red; left: 0px; top: 0px;}
  25% {background-color: green; left: 100px; top: 0px;}
  50% {background-color: blue; left: 200px; top: 100px;}
  75% {background-color: yellow; left: 100px; top: 0px;}
  100% {background-color: skyblue; left: 0px; top: 0px;}
}

div {
  width: 100px;
  height: 100px;
  background-color: red;
  position: relative;
  animation-name: example;
  animation-duration: 2s;
}

/* animation-delay */
div {
  animation-name: example;
  animation-duration: 4s;
  animation-delay: 2s;
}

/* animation-iteration-count */
div {
  /* 애니메이션이 중지되기 전에 애니메이션을 3번 실행 */
  animation-iteration-count: 3;
  /* 애니메이션이 영원히 계속됨 */
  animation-iteration-count: infinite;
}

/* animation-direction */
div {
  /* 애니메이션을 역방향으로 실행 */
  animation-direction: reverse;
  /* 애니메이션을 먼저 앞으로 실행한 다음 뒤로 실행 */
  animation-direction: alternate;
  /* 애니메이션을 먼저 뒤로 실행한 다음 앞으로 실행 */
  animation-direction: alternate-reverse;
}

/* animation-timing-function */
.div1 {animation-timing-function: linear;}
.div2 {animation-timing-function: ease;}
.div3 {animation-timing-function: ease-in;}
.div4 {animation-timing-function: ease-out;}
.div5 {animation-timing-function: ease-in-out;}

/* animation-fill-mode */
div {
  animation-name: example;
  animation-duration: 2s;
  /* 애니메이션이 끝날 때 <div> 요소가 마지막 키프레임의 스타일 값을 유지하도록 함 */
  animation-fill-mode : forwards;
  /* 애니메이션이 시작되기 전(애니메이션 지연기간) 첫 번째 키프레임에 의해 설정된 스타일 값을 <div> 요소가 가져오도록 함 */
  animation-fill-mode : backwards;
}

/* animation shorthand */
div {
  animation-name: example;
  animation-duration: 5s;
  animation-timing-function: linear;
  animation-delay: 2s;
  animation-iteration-count: infinite;
  animation-direction: alternate;
}

div {
  animation: example 5s; linear 2s infinite alternate;
}

```

## Tooltip

- 툴팁은 사용자가 요소 위로 마우스 포인터를 이동할 때 무언가에 대한 추가 정보를 지정하는데 자주 사용됨

```html
<style>
  /* Tooltip Container */
  .tooltip {
    position: relative;
    display: inline-block;
    border-bottom: 1px dotted black;
  }

  /* Tooltip Text */
  .tooltip .tooltiptext {
    visibility: hidden;
    width: 100px;
    background-color: red;
    color: #fff;
    text-align: center;
    padding: 5px 0;
    border-radius: 5px;

    position: absolute;
    z-index: 1;
  }

  .tooltip:hover .tooltiptext {
    visibility: visible;
  }
</style>

<!-- 
  HTML
  · 컨테이너 요소 <div>를 사용하고, tooltip 클래스를 추가, 사용자가 이 <div>위에 마우스를 올리면 툴팁 텍스트가 표시됩니다. 
  · tooltip text는 <span>을 사용하여, 인라인 요소 안에 배치
-->

<div>
  <div class="tooltip">
    Hover over me
    <span class="tooltiptext">Tooltip text</span>
  </div>
</div>
```

### Styling Images

- border-radius 속성을 이용하여 둥근 이미지

```css
img {
  border-radius: 8px;
  border-radius: 50%;
}
```

- 이미지를 축소해야 하는경우 축소하되 원래 크기보다 확대하지 않으려면 height 속성 추가

```css
img {
  max-width: 100%;
  height: auto;
}
```

- 이미지를 중앙에 정렬하려면 여백을 설정하고 block 요소로 만듬

```css
img {
  display: block;
  margin: 0 auto;
  width: 50%;
}
```

- Transparent Image

```css
img {
  /* opacity 속성은 0.0 ~ 1.0 사이의 값을 가질 수 있다. 값이 낮을수록 더 투명해짐 */
  opacity: 0.5;
}
```

- Filter 속성은 요소에 시각적 효과(예: 흐림 및 채도)를 추가

```css
.blur {
  filter: blur(4px);
}
.brightness {
  filter: brightness(100%);
}
.contrast {
  filter: contrast(100%);
}
.grayscale {
  filter: grayscale(180deg);
}
.huerotate {
  filter: hue-rotate(180deg);
}
.invert {
  filter: invert(100%);
}
.opacity {
  filter: opacity(50%);
}
.saturate {
  filter: saturate(7);
}
.sepia {
  filter: sepia(100%);
}
.shadow {
  filter: drop-shadow(8px 8px 10px green);
}
```

- Flip an Image

```css
img: hover {
  transform: scaleX(-1);
}
```

- Image Reflections
  - box-reflect 속성은 이미지 반사를 만드는 데 사용됨
  - 속성값은 `below`, `above`, `left`, `right`

```css
img {
  /* 이미지 아래에 반사 */
  -webkit-box-reflect: below;
  /* 이미지 오른쪽에 반사 */
  -webkit-box-reflect: right;
  /* 이미지 위쪽에 20px 오프셋을 사용하여 반사 */
  -webkit-box-reflect: above 20px;
}
```

- Object-fit Property
  - obejct-fit 속성은 컨테이너에 맞게 `<img>` 또는 `<video>` 크기를 조정하는 방법을 지정하는데 사용됨

```css
img {
  /* 기본값. 이미지는 주어진 치수를 채우도록 크기가 조정 */
  object-fit: fill;
  /* 이미지는 종횡비를 유지하지만 주어진 치수에 맞게 크게가 조정 */
  object-fit: contain;
  /* 이미지는 종횡비를 유지하고 주어진 치수를 채움. 이미지에 맞게 잘린다 */
  object-fit: cover;
  /* 이미지의 크기가 조정되지 않는다. */
  object-fit: none;
  /* 이미지가 가장 작은 버전 none 또는 contain */
  object-fit: scale-down;
}
```

- Masking

  - mask-image 속성은 마스크 레이어 이미지를 지정
  - mask layer image는 PNG이미지, SVG이미지, CSS 그라디언트 또는 SVG`<mask>` 요소일 수 있습니다.

  - Browser Support(브라우저 지원)
    - 대부분의 브라우저는 CSS 마스킹을 부분적으로만 지원, 그래서 표준 속성 외에 -webkit- 접두사를 사용해야함

```css
.mask {
  -webkit-mask-image: url(w31ogo.png);
  mask-image: url(w31ogo.png);
  -webkit-mask-repeat: no-repeat;
  mask-repeat: no-repeat;

  /* 선형 그라디언트를 마스크 레이어로 사용 */
  -webkit-mask-image: linear-gradient(black, transparent);
  mask-image: linear-gradient(black, transparent);

  -webkit-mask-image: radial-gradient(
    circle,
    black 50%,
    rgba(0, 0, 0, 0.5) 50%
  );
  mask-image: radial-gradient(circle, black 50%, rgba(0, 0, 0, 0.5) 50%);
}
```

- Multiple Columns
  - multi-column layout을 사용하면 신문에서와 같이 여러 열의 텍스트를 쉽게 정의할 수 있다.
  - column-count
  - column-gap
  - column-rule-style
  - column-rule-width
  - column-rule
  - column-span
  - column-width

```css
div {
  /* 요소의 텍스트를 3개의 열로 나눔 */
  column-count: 3;
  /* 열 사이의 간격 */
  column-gap: 30px;
  /* 열 사이의 선 스타일을 지정 */
  column-rule-style: solid;
  /* 열 사이의 선 너비를 지정 */
  column-rule-width: 3px;
  /* 열 사이의 규칙 색상을 지정 */
  column-rule-color: lightblue;
  /* 모든 column-rule-* 속성을 설정하기 위한 약식 속성 */
  column-rule: 3px solid lightblue;
  /* 요소가 가로질러야 하는 열의 수 지정 */
  column-span: all;
  /* 열에 대해 제안된 최적의 너비를 지정 */
  column-width: 100px;
}
```

- Resizing
  - resize 속성은 사용자가 요소의 크기를 조정할 수 있는지 여부를 지정

```css
div {
  /* 요소의 너비만 조정 */
  resize: horizontal;
  /* 요소의 높이만 조정 */
  resize: vertical;
  /* 요소의 높이와 너비를 모두 조정 */
  resize: both;
  overflow: auto;
}

textarea {
  /* <textarea>는 기본적으로 크기 조정이 가능하지만, resize: none;을 사용하면 크기 조정이 비활성화됨 */
  resize: none;
}
```

- Outline Offset
  - outline-offset 속성은 윤곽선과 요소의 가장자리 또는 테두리 사이에 공간을 추가
  - \*외곽선 !== 테두리, 테두리와 달리 윤곽선은 요소의 테두리 외부에 그려지며 다른 내용과 겹칠 수 있다.
  - 요소의 전체 너비와 높이는 윤곽선 너비의 영향을 받지 않음

```css
div.ex1 {
  margin: 20px;
  border: 1px solid black;
  outline: 4px solid red;
  outline-offset: 15px;
}
```

- Media Queries
  - CSS3에 도입된 CSS 기술
  - 미디어 쿼리를 사용하는 것은 데스크톱, 랩톱, 태블릿 및 휴대폰에 맞춤형 스타일 시트를 제공하는 데 널리 사용되는 기술
- 뷰포트란? : 웹 페이지에서 사용자가 볼 수 있는 영역
  - 큰 고정 너비 요소를 사용하지 마시오.
  - 컨텐츠가 잘 렌더링되기 위해 특정 뷰포트 너비에 의지하지 않도록 함
  - CSS 미디어 쿼리를 사용하여 작은 화면과 큰 화면에 서로 다른 스타일 적용

```css
/* 뷰포트가 964px 까지 배경색을 blue로 변경 */
@media screen and (max-width: 964px) {
  body {
    background-color: blue;
    color: white;
  }
}

/* 뷰포트가 480px 이상인 경우 배경색을 lightgreen으로 변경 */
@media screen and (min-width: 480px) {
  body {
    background-color: lightgreen;
  }
}

/* 브라우저의 너비가 480px ~ 964px 사이인 경우 <div> 요소의 모양을 변경 */
@media screen and (max-width: 964px) and (min-width: 480px) {
  div.ex {
    font-size: 24px;
    padding: 50px;
    border: 3px solid black;
    background: yellow;
  }
}
```

### Grid Elements

- 그리드 레이아웃은 하나 이상의 자식 요소가 있는 부모 요소로 구성됨
- Display Property
  - display 속성이 grid 또는 inline-grid로 설정되면 HTML 요소는 그리드 컨테이너가 된다.
- 그리드 항목의 수직선을 열(Column)이라고 합니다.
- 그리드 항목의 수평선을 행(Row)라고 합니다.
- Grid Gaps
  - 각 열/행 사이의 공백을 간격이라고 한다.
  - column-gap : 열 사이의 간격 설정
  - row-gap : 행 사이의 간격 설정
  - gap : row-gap, column-gap에 대한 약식속성
- Grid Lines
- Grid Container
  - grid-template-columns
    - 그리드 레이아웃 열 수를 정의하고, 각 열의 너비를 정의
    - 그리드 레이아웃에 4개의 열이 포함되도록 하려면, 4개의 열 너비를 지정하거나 모든 열의 너비가 같아야 하는 경우 "auto" 지정
  - grid-template-rows
    - 각 행의 높이를 정의, 값은 공백으로 구분된 목록이며, 각 값은 해당 행의 높이를 정의
  - justify-content
    - 컨테이너 내부의 전체 그리드를 정렬하는데 사용
    - 효과를 나타내려면 그리드의 전체 너비가 컨테이너 너비보다 작아야함
  - align-content
    - 컨테이너 내부의 전체 그리드를 수직으로 정렬하는데 사용

```css
.grid-container {
  display: grid;
  display: inline-grid;
  column-gap: 50px; /* 열 사이의 간격을 설정 */
  row-gap: 50px; /* 행 사이의 간격을 설정 */
  gap: 50px 100px; /* gap 속성은 row-gap, column-gap 에 대한 약식속성 */
  gap: 50px; /* 행 간격과 열 간격을 하나의 값으로 설정 */
}

.item1 {
  /* 열 행 1에 그리드 항목을 배치하고, 열 행 3에서 끝나도록 한다. */
  grid-column-start: 1;
  grid-column-end: 3;

  grid-template-columns: auto auto auto auto;
  grid-template-columns: 80px 200px auto 40px;
  grid-template-rows: 80px 200px;

  justify-content: space-evenly;
  justify-content: space-around;
  justify-content: space-between;
  justify-content: center;
  justify-content: start;
  justify-content: end;

  align-content: center;
}
```

### Grid Item

- 기본적으로 컨테이너에는 각 행의 각 열에 대해 하나의 그리드 항목이 있지만 여러 열 및 행에 걸쳐 있도록 그리드 항목의 스타일을 지정할 수 있다.
- grid-column 속성은 항목을 배치할 열을 정의
- grid-row 속성은 항목을 배치할 행을 정의
- grid-area 속성은 grid-row-start, grid-column-start, grid-row-end, grid-column-end의 약식속성으로 사용

```css
.item1 {
  /* item1이 1열에서 시작하고 5열보다 먼저 끝나도록 함 */
  grid-column: 1 / 5;
  /* item1이 1열에서 시작하여 3열로 확장되도록 함 */
  grid-column: 1 / span 3;

  /* item1이 행1에서 시작하여, 행4에서 끝나도록 한다. */
  grid-row: 1 / 4;
  /* item1이 1행에서 시작하여 2행에 걸쳐있도록 한다. */
  grid-row: 1 / span 2;
}

.item8 {
  /* item8을 행 1과 2행에서 시작하고, 행 5행과 6행에서 끝내도록 한다. */
  grid-area: 1 / 2 / 5 / 6;
  /* item8을 행 2행과 열 행 1에서 시작하고 2행과 3열로 확장합니다. */
  /*        2행  1열    2행       3열  */
  grid-area: 2 / 1 / span 2 / span 3;
}
```

출처 : [https://www.w3schools.com/css/]
