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

- computed(내부에서 observable 을 사용하는 함수)
  - 데코레이터 없이 사용하는 방식
- <onservable 클래스>의 getter에 @computed 달아서 처리
  - 스토어에 사용
  - getter에만 붙일수 있다.
- 함수가 아니라 리액티브 하다는 것에 주목
- 실제 컴포넌트에서 사용하는 (게터)값들에 달아서 사용하면 최소 범위로 변경할 수 있기 때문에 유용하다.
  - 30살이 넘었을때만 나이를 올리면 30살 이하일때는 재렌더링 대상이 아닌 것과 같은 경우
  - 내부적으로 고도의 최적화 -> 어떻게?
    - 매번 재계산을 하지 않는다
    - 계산에 사용할 observable 값이 변경되지 않으면 재실행하지 않음
    - 다른 computed 또는 reaction에 의해 호출되지 않으면 재실행하지 않음
    - observable이 변했는데 computed가 변하지 않을때 렌더하지 않음

## inject와 Provider

- Provider라서 컨테이너라는 개념을 사용해도 좋다.
- 프로바이더에 props로 넣고, @inject로 꺼내 쓴다고 생각하면 된다.
  - 상당히 명시적이고 편함
  - 컨테이너를 쓰지 않아도 된다. 하지만 중간에 작성해주는것이 테스트와 분리를 위해 훨씬 좋다.
    - props로 바꿔줍니다.
    - this.props.store
