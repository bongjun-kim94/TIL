# What Is MobX

- 데코레이터를 적극 활용한다.
  - cra에 데코레이터를 사용하는법
  - 스토어 객체에 붙이는 데코레이터가 있고, => @observable
  - 컴포넌트에서 사용하는 데코레이터가 있다.
- TypeScript가 Base인 라이브러리
- Redux와 마찬가지로, 스토어에 필요한 부분과 리액트에 필요한 부분이 있다.
  - npm i mobx
  - npm i mob-react
- 리덕스와 다르게 단일 스토어를 강제하진 않는다.

- 리액티브 프로그래밍 > 함수형 프로그래밍
- 간편한 비동기 처리
- 데코레이터의 적극적인 사용으로 인해, 깔끔한 구성
- 하지만, 단일스토어가 아니다
  - 최상위 스토어를 만들고, props로 공유해 가는 방식
  - 스토어를 어떻게 사용할지에 대한 적합한 해결을 모색해야 할 것

## @observable (by mobx)

- 두 가지 방법으로 주로 쓰임
  - 데코레이터 없이 사용하는 방식
  - @없이, 함수처럼 사용해서 리턴한 객체를 사용
- @observable<클래스의 프로퍼티>
  - 데코레이터로 사용하는 법
  - 클래스 내부에 프로퍼티 앞에 붙여서 사용
  - 한 클래스 안에 여러개의 @observable 존재

```ts
// 클래스에서 observavle을 달면 constructor에서 makeObservable을 해줘야함
class PersonStore {
  @observable
  name = "Bong";

  @observable
  age = 29;

  constructor() {
    makeObservable(this);
  }
}
```

## @observer (by mobx-react)

- observer(<컴포넌트>);
  - 데코레이터 없이 사용하는 방식
  - 함수 컴포넌트에 사용
- <컴포넌트 클래스>에 @observer 달아서 처리 -클래스 컴포넌트에 사용

## @computed (by mobx)
