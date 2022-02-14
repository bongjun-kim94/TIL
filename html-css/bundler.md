# bundler

## 번들러 개요 - parcel vs webpack

    parcel - 구성없는 단순한 자동 번들링, 소/중형 프로젝트에 적합
    webpack - 매우 꼼꼼한 구성 중/대형 프로젝트에 적함

# parcel



공급 업체 접두사(Vender Prefix) - webkit이라던지 ms


browserslist 옵션은 현재 NPM 프로젝트에서 지원할 브라우저의 범위를 명시하는 용도입니다.
그 명시를 Autoprefixer 패키지가 활용하게 됩니다.

<!-- 전세계의 점유율이 1% 이상인 모든 브라우저, 해당하는 브라우저의 마지막 두 개의 버전까지 지원 -->
{
    "browserslist": [
    "> 1%",
    "last 2 versions"
    ]
}

뒤에 rc(Runtime Configuration의 약어)가 붙은 파일은 구성 파일을 의미합니다.


// ESM - 브라우저에서 동작하는 가져오기 내보내기 방식
// CommonJS - nodejs 환경에서 동작하는 개념 nodejs 는 commonjs라는 방식을 사용한다

// import autoprefixer from 'autoprefixer';
const autoprefixer = require('autoprefixer');

// export {
//   plugins: [
//     autoprefixer
//   ]
// }
module.exports = {
  plugins: [
    autoprefixer
  ]
}

빠른 모듈 교체(HMR, Hot Module Replacement)는 런타임 페이지에 새로고침 없이 수정된 내용을 자동으로 갱신하는 방식

서버 포트 변경
"dev": "parcel index.html --port 1216",


## webpack

webpack.config.js 는 브라우저에서 동작하는 것이 아니고, nodejs 환경에서 동작

이스케이프 문자(Escape String)는 백슬래시를 사용해 원래의 의미를 벗어자는 문자를 만들 수 있습니다.
정규표현식에서 .(마침표)은 '임의의 한 문자'를 의미하기 때문에, 그 의미에서 벗어나 단순 마침표로 해석될 수 있도록 이스케이프 문자로 만들어 줘야 합니다.


에러 : Error: Cannot find module 'autoprefixer'
해결방법 : npm i autoprefixer 으로 설치하여 종속성 제거