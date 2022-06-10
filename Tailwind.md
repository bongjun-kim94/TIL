# Tailwind CSS

    npm install -D tailwindcss
    npx tailwindcss init

    // 함께 설치해주어야함
    npm install -D tailwindcss postcss autoprefixer

- Tailwind CSS는 클래스 이름에 대한 모든 HTML 파일, JavaScript 구성 요소 및 기타 템플릿을 검색하고 해당 스타일을 생성한 다음 정적 CSS 파일에 작성하여 작동합니다.

- 빠르고 유연하며 안정적이며 런타임이 없습니다.

### react-slick

    npm install react-slick --save
    npm install slick-carousel --save

- slick에서 제공해주는 css를 사용하기 위해 import 해준다.

```js
import "slick-carousel/slick/slick.css";
import "slick-carousel/slick/slick-theme.css";
```

### tailwind css 장점

- class명을 고려할 필요가 없다.
- css 파일 크기 감소
- 스타일과 코드를 한 곳에서 관리해 직관적이다.
- 쉬운 인라인 스타일
- custom으로 사용할 수 있다

### tailwind css 단점

- 클래스명을 여러개 넣다보니 코드가 못생겨진다.
- 클래스 명들을 html에 직접 입력함으로써 클래스가 반복되게 될 경우 용량 손해를 볼 수있다.
- 필요한 클래스는 외우고 있어야하고, 검색을 자주 하게된다.
- javascript 코드 사용 불가

### Unknown at rule @tailwindcss(unknownAtRules) 발생시

    vscode 확장 기능인 PostCSS Language Support를 설치하면 밑줄이 사라짐

```css
@tailwind base;
@tailwind components;
@tailwind utilities;

@apply;
```
