# MUI
    부트스트랩, antd와 같이 빠르고 쉽게 웹 개발을 위한 웹 디자인 CSS를 도와주는 프레임워크이다. 


```js
// with npm
npm install @mui/material @emotion/react @emotion/styled

// with yarn
yarn add @mui/material @emotion/react @emotion/styled
```
- MUI 링크 : https://mui.com/

```ts
xs (extra-small) : 0px ~ 600px
sm (small) : 600px ~ 960px
md (medium): 960px ~ 1280px
lg (large) : 1280px ~ 1920px
xl (extra-large) : 1920px ~
```

###

```ts
m	margin
mt	margin-top
mr	margin-right
mb	margin-bottom
ml	margin-left
mx	margin-left, margin-right
my	margin-top, margin-bottom
p	padding
pt	padding-top
pr	padding-right
pb	padding-bottom
pl	padding-left
px	padding-left, padding-right
py	padding-top, padding-bottom
```

### mui layout 
- Container, Grid, box
- Box: Box는 div를 대체하는 강력하고 편리한 컴포넌트
- Grid: Container안의 레이아웃을 핸들링하고 반응형으로 배치할때 유용
  - Grid의 breakpoints는 총 5개로 이루어져있다.
  - xl, lg, md, sm, xs
- Container: 레이아웃을 잡을때 좌 우 중앙 위치시 사용

### useMideaQuery
- React용 CSS 미디어 쿼리 훅이다. 쿼리가 일치하는지 여부에 따라 구성 요소를 렌더링
```ts
const theme = useTheme();
const isMobile =  useMediaQuery('(max-width: 600px)');
const isMobile = useMediaQuery(theme.breakpoints('sm'));

console.log(isMobile); 

```