# TypeScript Compiler

## Compilation Context
    컴파일 컨텍스트는 근본적으로 집단에서 사용하는 용어이며 타입스크립트는 유효한 것을 분석하고 해석합니다. 어떤 파일의 정보와 함께 컴파일 컨텍스트에는 사용중인 컴파일러 옵션에 대한 정보가 들어있습니다. 이 논리그룹을 정의하는 가장 좋은 방법은 tsconfig.json 파일을 사용하는 것 입니다. 

## tsconfig schema

최상위 프로퍼티
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

## compileOptions - typeRoots, types

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