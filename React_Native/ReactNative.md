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
