# 마크다운(markdown) 작성요령

    #의 개수로 제목의 중요도를 정해줄 수 있다.

# 제목1
## 제목2
### 제목3
#### 제목4
##### 제목5 
###### 제목6
</br>

# 문장

동해물과 백두산이 마르고 닳도록 
하느님이 보우하사 우리나라 만세

<br />

# 줄바꿈 

    html의 break태그로 줄바꿈 해줌

동해물과 백두산이 마르고 닳도록 <br /> 
하느님이 보우하사 우리나라 만세

<br />

# 강조

- _기울임_ : 글자를 _ _ 로 감싸서 사용

- **두껍게** : 글자를 ** ** 로 감싸서 사용

- **_기울임 + 두껍게 _** : 기울임과 두껍게를 동시에 사용하려면 ** __ __**로 사용

- ~~취소선~~ : 글자를 ~~ ~~ 로 감싸서 사용

- <u>밑줄</u> : u 태그로 감싸서 사용

<br />

# 목록(List)

1. 순서가 필요한
1. 순서가 필요한
    1. 순서가 필요한
    1. 순서가 필요한

<br />

- 순서가 필요없는
- 순서가 필요없는
    - 순서가 필요없는
    - 순서가 필요없는
- 순서가 필요없는

<br />

# 링크(Links)

<a href="https://www.naver.com">Naver</a> : a태그를 이용하는 방법

[Naver](https://www.naver.com) : `[이름](주소)` 를 이용하는 방법

<a href="https://www.naver.com" title="Naver로 이동">Naver</a> : 마우스 올릴시 title제목 보여줌

[Naver](https://www.naver.com "Naver로 이동") : `()`주소창 뒤에 "title" 사용

<a href="https://www.naver.com" title="Naver로 이동" target="_blank">Naver</a> : 마크다운엔 _blank 기능이 없어서 a태그를 사용

<br />

# 이미지(Images)

`![대체text](경로)` : 링크와 비슷한데 맨앞에 !를 붙여서 사용

`[![대체text](경로)](연결주소)` : `[]` 안에 넣어주고 `()`에는 주소를 입력하면 이미지 링크로 활용가능

<br />
 
# 인용문(BlockQuote)
    > 기호를 사용해서 작성
> 남의 말이나 글에서 직업 또는 간접으로 따온 문장.  
> (네이버 국어 사전)

<br />

# 인라인(inline) 코드 강조

`` 백틱 기호사이에 강조 문장 넣어서 사용

<br />

# 블록(block) 코드 강조

- css
```css
  .block {
    width: 30px;
    height: 30px;
    margin: 0 auto;
  }
```

- javascript
```javascript
function func() {
  let a = 123;
  return a;
}
```

- bash(terminal)
```bash
$ git remote -v
```

- plaintext
```plaintext
동해물과 백두산이
마르고 닳도록
```

<br />

# 표(Table)

position 속성

```
값 | 의미 | 기본값
:--:|:--:|:--: - 정렬 :가운데:, :왼쪽, 오른쪽:
static | 기준 없음 | o
relative | 요소 자신 | x
absolute | 위치 상 부모 요소 | x
fixed | 뷰포트 | x
```

값 | 의미 | 기본값
:--:|:--:|:--:
static | 기준 없음 | o
relative | 요소 자신 | x
absolute | 위치 상 부모 요소 | x
fixed | 뷰포트 | x

<br />

# 수평선

    ---, ***, ___ 입력시 수평선 생성
--- 
***
___