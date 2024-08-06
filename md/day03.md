## HTML&CSS REVIEW

### DAY 03
> 1. 반응형 레이아웃
> 2. Transition 속성으로 애니메이션
> 3. CSS 덮어쓰기
> 4. Pseudo-element
> 5. Shadow DOM
---
## 반응형 레이아웃
### 1. 모던 웹에서 사용하는 단위
- 모던 웹에서 사용하는 단위는 `px` , `%` 말고 다음과 같이 더 있다.
  ```css
  .box{
    width: 16px; /* 기본 px 단위 */
    width: 1.5rem; /* HTML 태그 혹은 기본 폰트사이즈의 1.5배 */
    width: 2em; /* 내 폰트사이즈 혹은 상위요소 폰트사이즈의 2배 */
    width: 50vw; /* 브라우저(viewport) 화면 폭의 50% */
    width: 50vh; /* 브라우저(viewport) 화면 높이의 50% */
  }
  ```
- 이전 브라우저에는 `rem` 단위를 가끔 썻다.
- 그 당시에는 브라우저 설정에서 폰트크기를 설정했기 때문이다. 그러나 요즘은 `ctrl + 마우스휠` 로 줌인/줌아웃을 하기 때문에 유용한 속성은 아니다.
### 2. 반응형 웹
- `반응형 웹`이란 **한 가지의 웹사이트로 다양한 종류의 화면 크기에 최적화된 화면을 보여주는 것**이다. 반응형 웹을 구현하기 위해 `<head>` 태그에 아래 코드를 추가해줘야 한다.
  ```html
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  ```
- CSS 파일에 media query 를 이용하여 화면 크기에 따라 스타일을 지정해주면 된다.
  - 아래 코드는 화면이 1200px 이하일 경우 스타일 적용 코드와, 768px 이하일 경우 스타일 적용 코드, 576px 이하일 경우 스타일 적용 코드이다.
  - 아래 코드들은 CSS 최하단에 적어준다.
  ```css
  @media screen and (max-width : 1200px) { /* PC 사이즈 */ 
    .box { 
      font-size : 40px; 
    } 
  } 

  @media screen and (max-width :z 768px) { /* 태블릿 사이즈 */
    .box { 
      font-size : 30px; 
    } 
  }

    @media screen and (max-width : 576px) { /* 모바일 사이즈 */
    .box { 
      font-size : 20px; 
    } 
  }
  ```
### 3. Breakpoint
- `media query` 문법에서 `max-width` 안에 넣는 브라우저 폭을 `breakpoint` 라고 한다.
- `breakpoint` 는 원하는 만큼 넣을 수 있는데 맘대로 특정 폭을 넣는것 보다 자주 사용하는 breakpoint 를 쓰는게 좋다.
  - `1200px` / `992px` / `768px` / `576px`
  - 위 단위들은 `Bootstrap` 라이브러리가 기본으로 권장하는 `breakpoint이다`.
  - 768px 이나 576px을 모바일 폭으로 정하면 된다.
---
## Transition 속성으로 애니메이션
### 1. overflow 속성
- **박스의 폭이나 높이를 초과하는 내부요소를 처리**하기 위한 속성이다.
- 속성값으로 hidden 을 주면 넘치는 내부요소를 잘라 없애준다.
  - `overflow : visible;`
  - `overflow : scroll;`
### 2. opacity 속성
- HTML 요소의 투명도를 조절할 수 있는 속성이다.
- color 속성의 `rgba()` 함수로 색상과 투명도를 조절할 수도 있다.
  - 예시) `background-color: rgba(0,0,0,0.5);`
### 3. transition 속성
- `transition` 속성은 적용된 CSS 스타일 중 특정 스타일이 변할 때 특정 시간동안 변하게하는 애니메이션 효과를 줄 수 있다.
- 세부 속성은 다음과 같다.
  ```css
  .box{
    transition-delay: 1s; /* 시작 전 딜레이 */
    transition-duration: 0.5s; /* transition 작동 속도 */
    transition-property: opacity; /* 어떤 속성에 transition 입힐 건지 */
    transition-timing-function: ease-in; /* 동작 속도 그래프 조정 */
  }
  ```
### 4. 애니메이션 효과 만드는 법칙
- 애니메이션 종류는 transition 이외에도 정말 많다.
- 하지만 만드는 규칙만 안다면 애니메이션 속성은 구글링하여 적용할 수 있다.
> 1. 시작스타일 정하기
> 2. 최종스타일 정하기
> 3. 언제 최종스타일로 변할지 트리거 주기(대부분 마우스 올렸을 때 : hover)
> 4. transition 속성으로 서서히 동작하게 만들기
---
## CSS 덮어쓰기
> 유지보수를 하다보면 CSS를 수정할 수 없어 덮어써야 하는 경우가 있다.

### 1. 같은 클래스명이나 스타일을 하단에 작성
- 하나의 CSS 파일일 경우에는 덮어쓸 선택자 아래에 새로 작성하면 새로작성한 스타일이 우선적으로 적용된다.
  ```css
  .box{
    background: red;
  }
  .box{
    background: blue;
  }
  ```
- 같은 class 명이라도 하단에 정의한 클래스 명과 스타일을 우선적으로 적용한다.
- 선택자 뿐 아니라 CSS 파일이 여러개 첨부되었을 때도 같은 HTML 요소를 건든다면 제일 아래에 첨부한 CSS 파일이 우선적으로 적용된다.
### 2. 선택자 우선순위 이용
- 스타일을 지정할 때는 다음과 같은 우선순위로 적용된다.
  - `인라인스타일` > `ID 선택자` > `Class 선택자` > `태그 선택자`
- 또는 `!important` 를 붙히게 되면 최우선으로 스타일이 적용된다.
- 하지만 `!important` 는 근본적인 해결방안은 아니다.
---
## Pseudo-element
> Pseudo class는 특정 요소가 다른 상태일 때 스타일을 줄 수 있게 도와주는 것이였다.(hover 등등)<br>
> 마찬가지로 **특정 HTML 요소의 안쪽 일부만 스타일**을 주고 싶을 때 `Pseudo-element` 를 사용한다.

- `Pseudo-element`를 사용하는 방법은 선택자 뒤에 `::` 를 붙혀주는 것이다.
  - `first-letter` : 글자 중 첫 글자만 스타일
  - `first-line` : 글자 중 첫 줄만 스타일
  - `after` : 내부의 맨 마지막 부분 스타일 추가
  - `before` : 내부 맽 앞 부분 스타일 추가
---
## Shadow DOM
### 1. Shadow DOM 개발자 도구에서 확인하기
- `<input type="file" class="input-file">` 태그를 선언하면 파일선택 버튼이랑 오른쪽에 글씨랑 2개가 생성되는 것을 알 수 있다.
- 이유는 `Shadow DOM` 덕분이다.
- 쉽게말해 **숨겨진 HTML 요소**이다.
- 크롬 개발자도구에서 `Settings -> Preferences -> Show user agent shadow DOM` 항목이 있는데 체크를 해주면 `Shadow DOM` 을 볼 수 있다.
- 개발자 도구를 확인해보면 `pseudo` 라는 속성이 있다. 해당 속성값을 이용하여 `Pseudo-element` 를 사용하면 개발자가 원하는 커스텀을 할 수 있다.
  ```css
  input::-webkit-input-placeholder {
    color : red; 
  }
  ```
### 2. -webkit 이란
- `Shadow DOM` 을 사용하다보면 공통적으로 들어가는게 `-webkit-` 이다.
- 위 수식어는 **크롬 브라우저에서만 동작하는 수식어**다.
  - `-webkit-` : 크롬 브라우저
  - `-moz-` : 파이어폭스
  - `-ms-` : 익스플로러
