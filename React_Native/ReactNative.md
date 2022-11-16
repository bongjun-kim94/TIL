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