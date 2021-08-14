# localStorage & sessionStorage

+ HTML5에서 추가된 저장소, HTML5을 지원하지 않는 경우 사용불가
+ 간단한 키와 값을 저장할 수 있다. key-value 스토리지 형태
+ cookie의 단점을 보완한 웹 스토리지
+ 로컬스토리지와 세션스토리지의 차이점은 영구성이다.

## localStorage
+ 도메인 별로 관리 할 수 있다.
+ 도메인창을 닫더라도 유지된다.

```javascript
    if(typeof(Storage) !== "undefined") {
        localStorage.setItem("name","bongjun kim");
    }

    console.log(localStorage.getItem("name")); // bongjun kim
```

## sessionStorage

+ 같은 브라우저 탭에서만 유지된다.
+ 탭을 닫는순간 사라지는 데이터

```javascript
    if(typeof(Storage) !== "undefined") {
        sessionStorage.setItem("name2","Bongjun Kim");
    }

    console.log(sessionStorage.getItem("name2")); // Bongjun Kim
```

## 배열을 저장하고 싶다면?

```javascript
    if(typeof(Storage) !== "undefined") {
        // 배열 저장, 문자열로 변환해서 저장
        // JSON.stringify : json 객체를 String 객체로 변환시켜 줍니다.
        let array = ["a","b"];
        localStorage.setItem("array",JSON.stringify(array));
    }

    // 배열처럼 보이는 문자로 저장
    console.log(localStorage.getItem("array")); // ["a","b"]
    // JSON.parse : string 객체를 json 객체로 변환시켜줍니다.
    console.log(JSON.parse(localStorage.getItem("array"))); (2) ["a", "b"]
```



- - -

쿠키란?

+ 대부분의 브라우저가 지원
+ 매번 서버로 전송되고, 용량에 제한이있다. (4KB)
+ 문자열만 저장이 가능, 만료일자가 존재한다.
