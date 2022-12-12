# React Native

- React를 사용하여, Android, IOS 등을 위한 기본 앱 만들기
- Android, IOS 앱을 만들 수 있는 크로스 플랫폼(하이브리드 플랫폼) 이다.
- Javscript로 작성 - 네이티브 코드로 렌더링

```js
import React from "react";
import { Text, View } from "react-native";
import { HEADER } from "./Header";
import { heading } from "./Typography";

const WelcomeScreen = () => (
  <View>
    <Header title="Welcome to React Native" />
    <Text style={heading}>Step One</Text>
    <Text>Edit App.js to change this screen and turn it into your app.</Text>
    <Text style={heading}>See Your Changes</Text>
    <Text>Press Cmd + R inside the simulator to reload your app’s code.</Text>
    <Text style={heading}>Debug</Text>
    <Text>
      Press Cmd + M or Shake your device to open the React Native Debug Menu.
    </Text>
    <Text style={heading}>Learn</Text>
    <Text>Read the docs to discover what to do next:</Text>
  </View>
);
```

### React Native 장/단점
- 장점
  - 안드로이드와 IOS를 동시에 개발 할 수 있다.
  - 오픈 소스 플랫폼이기 떄문에 쉽고 빠르게 접근이 가능하다.
  -  리액트의 방식을 사용하여 컴포넌트 기반 개발 방식으로 소스코드의 재활용성이 높음
  - 기존 JavaScript 기반인 React로 개발하던 사람은 쉽게 접근이 가능

- 단점
  - 네이티브 개발에 비해 다양한 API를 사용하지 못한다.
  - 브릿지를 사용해 자바 스트립트의 스레드와 네이티브 스레드를 연결시켜 동작하는 하이브리드 앱 방식이라 네이티브 개발 방식보다 성능이 떨어질 수 있다.
  - 네이티브 개발인 안드로이드나 IOS 개발 보다는 라이브러리에 대한 지원이 적다.


## React Native의 두 가지 개발방법

### EXPO
- React Native 개발을 개발자가 쉽게 할 수 있도록 도와주는 툴
- 기본 설정이 되어있으며, native 파일을 숨겨놓고 자동으로 관리해줌
- 간단하고 편리하지만 모듈을 만들어서 사용하지 못함
- 애플리케이션 개발을 단순화하는 많은 편의 유틸리티 기능이 있다.

- 장점

- 단점
  - 제공되는 API만 사용가능
  - 빌드 시간이 오래 걸린다.

* CLI 란?
- CLI(명령줄 인터페이스)는 프로그래머가 명령을 실행하여 앱을 개발할 수 있는 시각적 인터페이스

### React Native CLI
- 어떤 툴 같은걸 사용하지 않고, React Native만을 이용해서 개발
- 자신이 원하는 기능이나 요소들을 제어할 수 있다.
- native 파일에 접근이 가능
- 더 많은 라이브러리를 사용할 수 있다.
- 자유도가 높아 개발의 많은 기능들을 사용할 수 있습니다.
- 빌드의 제어가 가능하다.
- Expo 패키지를 이용할 수 있지만 설정이 필요하다.

- 장점 
  - EXPO 패키지를 이용할 수 있지만 설정이 필요하다.
  - 자유도가 높다.
  -빌드의 제어가 가능하다.
- 단점
  - 프로젝트 설정에 시간이 많이 소요된다.
  - 모든 라이브러리 들을 따로 설치해줘야한다.
  - Android Studio(Android) 및 XCode(IOS)를 설치 해야한다.

### Scroll View
- 스크롤 뷰(ScrollView)는 여러개의 컴포넌트(Components)와 뷰(Views)를 담을 수 있는 스크롤 컨테이너다.

```ts
import { ScrollView, View, Text } from 'react-native';

const TestApp = () => {
  return (
    <ScrollView>
      <View>
        <Text>
          TestApp
        </Text>
      </View>
    </ScrollView>
  )
}
```

### React Navigation
- 모바일 앱은 보통 여러 화면으로 구성되어 있는데, 이러한 앱을 만드려면 내비게이션 관련 서드 파티 라이브러리를 사용해야 한다.
* 보통 두 가지를 사용한다.
- react-navigation
  - 리액트 네이티브 커뮤니티에서 관리, 내비게이션 기능이 자바스크립트로 구현되어 있다.
- react-native-navigation
    - 홈페이지 제작 서비스 Wix에서 관리한다.
    - 내비게이션 기능이 자바스크립트가 아닌 각 플랫폼의 네이티브 코드로 구현되어 있다.
    - react-navagation보다 더욱 네이티브 스러운 사용 경험을 제공