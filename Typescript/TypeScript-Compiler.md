# TypeScript Compiler
    스키마 참고 URL : https://json.schemastore.org/tsconfig

## Compilation Context
    컴파일 컨텍스트는 근본적으로 집단에서 사용하는 용어이며 타입스크립트는 유효한 것을 분석하고 해석합니다. 어떤 파일의 정보와 함께 컴파일 컨텍스트에는 사용중인 컴파일러 옵션에 대한 정보가 들어있습니다. 이 논리그룹을 정의하는 가장 좋은 방법은 tsconfig.json 파일을 사용하는 것 입니다. 

## tsconfig schema

최상위 프로퍼티 <br />
files, include, exclude : 어떤 파일을 컴파일 할건지를 결정하는걸로 사용
- compileOnSave
- extends
- compileOptions : 어떤 설정으로 컴파일 할건지
- files
- include      
- exclude
- references
- ~~typeAcquisition~~
- ~~tsNode~~

## compileOnSave

    "compileOnSave": true 

- true / false (default false)
- 누가?
  - Visual Studio 2015 with TypeScript 1.8.4 이상
  - atom-typescript 플러그인
    - https://github.com/TypeStrong/atom-typescript#compile-on-save

```
schema
{
  ...,
  "compileOnSaveDefination": {
    "properties": {
      "compileOnSave": {
        "description": "Enable Compile-on-Save for this project.",
        "type": "boolean"
      }
    }
  },
  ...,
}
```

## extends
    보통 상속할때 사용하는 키워드
    
어떤 부모 설정의 경로
- 파일(상대) 경로명: string
- TypeScript 2.1 New Spec

```ts
// in PROJECT/base.json
{
  "compilerOptions": {
    "strict": true
  }
}

// in PROJECT/tsconfig.json
{
  "extends": "./base.json",
}
```

```
schema
{
  ...,
  "extendsDefinition": {
    "properties": {
      "extends": {
        "description": "Path to base configuration file to inherit from. Requires Typescript version 2.1 or later.",
        "type": "string"
      }
    }
  },
  ...,
}
```

    npm install --save-dev @tsconfig/deno
    // 기본적으로 여러가지 형태의 증명된 설정 파일들이 상속받을 수 있게 내려옴
    {
      "extends": "@tsconfig/deno/tsconfig.json",
      ...
    }

## files, include, exclude

    files나 include 프로퍼티가 tsconfig 파일안에 없으면 컴파일러는 모든 파일을 컴파일 하려고 한다.
    어떤 파일, 어떤 디렉토리를 컴파일하는지를 규명(규정)하는 그런 프로퍼티, 꼼꼼히 체크해서 사용

- 셋다 설정이 없으면, 전부다 컴파일
- files
  - 상대 혹인 절대 경로의 리스트 배열입니다.
  - exclude 보다 쎕니다.
- include, exclude
  - glob 패턴 (마치 .gitignore 적혀있는 형식)
  - include
    - exclude 보다 약합니다.
    - `*` 같은걸 사용하면, .ts / .tsx / .d.ts 만 include (allowJS)

- exclude
  - 설정 안하면 4가지(node_modules, bower_components, jspm_packages, `<outDir>`)를 <br />
  default로 제외합니다.
  - `<outDir>`은 항상 제외합니다. (include에 있어도)

```
schema
{
  ...,
  "filesDefinition": {
    "properties": {
      "files": {
        "description": "If no 'files' or 'include' property is present in a tsconfig.json, the compiler defaults to including all files in the containing directory and subdirectories except those specified by 'exclude'. When a 'files' property is specified, only those files and those specified by 'include' are included.",
        "type": "array",
        "uniqueItems": true,
        "items": {
          "type": "string"
        }
      }
    }
  },
  "excludeDefinition": {
    "properties": {
      "exclude": {
        "description": "Specifies a list of files to be excluded from compilation. The 'exclude' property only affects the files included via the 'include' property and not the 'files' property. Glob patterns require TypeScript version 2.0 or later.",
        "type": "array",
        "uniqueItems": true,
        "items": {
          "type": "string"
        }
      }
    }
  },
  "includeDefinition": {
    "properties": {
      "include": {
        "description": "Specifies a list of glob patterns that match files to be included in compilation. If no 'files' or 'include' property is present in a tsconfig.json, the compiler defaults to including all files in the containing directory and subdirectories except those specified by 'exclude'. Requires TypeScript version 2.0 or later.",
        "type": "array",
        "uniqueItems": true,
        "items": {
          "type": "string"
        }
      }
    }
  },
  ...,
}
```

# compileOptions

## typeRoots, types

### @types
- TypeScript 2.0 부터 사용 가능해진 내장 type definition 시스템
- 아무 설정을 안하면?
  - node_modules/@types 라는 모든 경로를 찾아서 사용
- typeRoots를 사용하면?
  - 배열안에 들어있는 경로들 아래서만 가져옵니다.
- types를 사용하면?
  - 배열 안의 모듈 혹은 ./node_modules/@types/ 안의 모듈 이름에서 찾아옵니다.
  - [] 빈 배열을 넣는다는건 이 시스템을 이용하지 않겠다는 것입니다.

- typeRoots 와 types를 같이 사용하지 않습니다.

```
{
  ...,
  "typeRoots": {
    "description": "Specify multiple folders that act like `./node_modules/@types`.",
    "type": "array",
    "uniqueItems": true,
    "items": {
      "type": "string"
    },
    "markdownDescription": "Specify multiple folders that act like `./node_modules/@types`.\n\nSee more: https://www.typescriptlang.org/tsconfig#typeRoots"
  },
  "types": {
    "description": "Specify type package names to be included without being referenced in a source file.",
    "type": "array",
    "uniqueItems": true,
    "items": {
      "type": "string"
    },
    "markdownDescription": "Specify type package names to be included without being referenced in a source file.\n\nSee more: https://www.typescriptlang.org/tsconfig#types"
  },
  ...,
}
```

## target, lib
    target이 어떤 런타임에서 실행 할수 있는지 결정해줌

- target
  - 빌드의 결과물을 어떤 버전으로 할 것이냐
  - 지정을 안하면 es3

- lib
  - 기본 type definition 라이브러리를 어떤 것을 사용할 것이냐
  - lib를 지정하지 않을때,
    - target이 'es3'이고, 디폴트로 lib.d.ts를 사용합니다.
    - target이 'es5'이면, 디폴트로 dom, es5, scripthost를 사용합니다.
    - target이 'es6'이면, 디폴트로 dom, es6, dom.iterable, scripthost를 사용합니다.
  - lib를 지정하면 그 lib 배열로만 라이브러리를 사용합니다.
    - 빈[] => 'no definition found ~~~'
    
## outDir, outFile, rootDir

    outFile: 하나의 파일로 합쳐서 컴파일 진행 후 반환
    rootDir: 컴파일을 시작하는 루트 폴더 (설정 안하면 자동으로 가장 상위 디렉토리 지정)
    outDir: 컴파일 후 생성되는 js파일이 생성될 폴더명

## strict

```   
schema
{
  "strict": {
    "description": "Enable all strict type checking options.",
    "type": "boolean",
    "default": false,
    "markdownDescription": "Enable all strict type checking options.\n\nSee more: https://www.typescriptlang.org/tsconfig#strict"
  },
}
```

Enable all strict type checking options.
  - --noImplicitAny
  - --noImplicitThis
  - --strictNullChecks
  - --strictFunctionTypes
  - --strictPropertyInitialization
  - --strictBindCallApply
  - --alwaysStrict

`--noImplicitAny` <br />

    명시적이지 않게 any 타입을 사용하여, 표현식과 선언에 사용하면, 에러를 발생.

- 타입 스크립트가 추론을 실패할 경우, any가 맞으면, any라고 지정하라.
- 아무것도 쓰지 않으면, 에러를 발생

- 이 오류를 해결하면, any라고 지정되어 있지 않은 경우는 any가 아닌것이다. (타입 추론이 되었으므로)

`--noImplicitThis` <br />

    명시적이지 않게 any타입을 사용하여, this 표현식에 사용하면, 에러를 발생합니다.

- 첫번째 매개변수 자리에 this를 놓고, this에 대한 타입을 어떤 것이라도 표현하지 않으면, noInplicitAny가 오류를 발생시킨다.
- JavaScript 에서는 매개변수에 this를 넣으면, 이미 예약된 키워드라 StntaxError를 발생시킨다.
- call / apply / bind와 같이 this를 대체하여 함수 콜을 하는 용도로도 쓰입니다.

- 그래서 this를 any로 명시적으로 지정하는 것은 합리적입니다. (물론 구체적인 사용처가 있는 경우 타입을 표현하기도 합니다.)

<br />

- Class에서는 this를 사용하면서, noImplicitThis와 관련한 에러가 나지 않습니다. (당연)
- Class에서 constructor를 제외한 멤버 함수의 첫번째 매개변수도 일반 함수와 마찬가지로 this를 사용할 수 있습니다.

`--strictNullChecks` <br />

- strictNullChecks 모드에서는, null 및 undefined값이 모든 유형의 도메인에 속하지 않으며, 그 자신을 타입으로 가지거나, any일 경우에만 할당이 가능합니다.
- 한 가지 예외는 undefined에 void 할당 가능
- 중요한 옵션

- strictNullChecks를 적용하지 않으면,
    - 모든 타입은 null, undefined값을 가질 수 있습니다.
    - string으로 타입을 지정해도, null 혹은 undefined 값을 할당할 수 있다는 것입니다.

- strictNullChecks를 적용하면,
  - 모든 타입은 null, undefined 값을 가질 수 없고, 가지려면 union type 을 이용해서 직접 명시해야 합니다.
  - any 타입은 null과 undefined를 가집니다. 예외적으로 void 타입의 경우 undefined를 가집니다.

- strictNullChecks를 적용하지 않고, 어떤 값이 null과 undefined를 가진다는 것을 암묵적으로 인정하고 계속 사용하다 보면, 정확히 어떤 타입이 오는지를 개발자 스스로가 간과할 수 있습니다.
- 정말로 null과 undefined를 가질 수 있는 경우, 해당 값을 조건부로 제외하고 사용하는 것이 좋습니다.
- 이 옵션을 켜고 사용하는 경우,
- 사용하려는 함수를 선언할 때부터 매개변수와 리턴 값에 정확한 타입을 지정하려는 노력을 기울여야 하고, 기울이게 될 것 입니다.

`--strictFunctionTypes` <br />
    
    함수 타입에 대한 bivariant 매개변수 검사를 비활성화합니다

- 반환 타입은 공변적(convariant)
- 인자 타입은 반공변적(contravariant)
- 그런데 타입스크립트에서 인자 타입은 공변적이면서, 반공변적인게 문제!
- 이 문제를 해결하는 옵션이 strictFunctionTypes
- 옵션을 켜먼, 에러가 안나던걸 에러나게 함

`--strictPropertyInitialization` <br />

    정의되지 않은 클래스의 속성이 생성자에서 초기화 되었는지 확인합니다.
    이 옵션을 사용하려면 --strictNullChecks를 사용하도록 설정해야 합니다.

constructor에서 초기값을 할당한 경우 => 정상

constructor에서 안하는 경우
  - 보통 다른 함수로 이니셜라이즈 하는 경우 (async 함수)
  - constructor 에는 async를 사용할 수 없다.

`--strictBindCallApply` <br />

    bind, call, apply에 대한 더 엄격한 검사 수행

- Function의 내장함수인 bind / call / apply를 사용할 때, 엄격하게 체크하도록 하는 옵션
- bind는 해당 함수 안에서 사용할 this와 인자를 설정해주는 역할을 하고 call과 apply는 this와 인자를 설정한 후, 실행까지 합니다.
- call과 apply는 인자를 설정하는 방식에서 차이점이 있습니다.
  - call은 함수의 인자를 `여러 인자의 나열로` 넣어서 사용하고, apply는 `모든 인자를 배열 하나`로 넣어서 사용합니다.

`--alwaysStrict` <br />

    - 각 소스 파일에 대해 JavaScript의 strict mode로 코드를 분석하고, "엄격하고 사용"을 해제합니다.
    - syntax 에러가 ts error로 나온다.
    - 컴파일된 JavaScript 파일에 "use strict" 추가됨