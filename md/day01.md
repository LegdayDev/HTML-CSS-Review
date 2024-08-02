## HTML&CSS REVIEW

### DAY 01
> 1. 기본 태그들
> 2. 기본적인 웹 스타일
> 3. 이스케이프 문자
> 4. 선택자 우선순위
> 5. 배경설정 및 margin collapse
> 6. position 
> 7. 반응형 width & box-sizing
> 8. form 태그

#### 기본 태그들
```html
<p>글 본문</p>
<h1>글 제목</h1>
<img src="이미지 경로">
<a href="">링크</a>
<button>버튼</button>
<ul><li>리스트</li></ul>
<ol><li>리스트</li></ol>
```
- 특정 태그는 `href` , `src` 속성을 이용하여 추가 정보를 기입한다.
  - `href` : 클릭 시 이동할 링크
  - `src` : 파일 경로
- `HTML(Hyper Text Markup Language)`은 마크업언어기 때문의 **자료의 구조를 쉽게 파악**할 수 있어야 한다. 그렇기 때문에 자료의 구조를 쉽게 파악할 수 있게 알맞은 용도의 태그를 사용해야 한다.
- 용도에 맞는 태그를 사용하면 '웹표준'에 맞는 웹을 만들어낼 수 있다.
---
#### 기본적인 웹 스타일
- HTML 은 웹페이지의 구조(뼈대)라면 스타일같은 레이아웃을 꾸밀 때는 CSS(Cascading Style Sheet)를 사용한다.
- CSS를 적용하는 방법은 크게 3가지이다.
  1. 인라인 스타일
  2. 내부 스타일
  3. 외부 스타일
- 인라인 스타일은 아래와 같이 HTML 태그 안에 직접 기입하는 것이다.
  ```html
  <p style="font-size : 20px; color : red"> 글자 </p>
  ```
- 내부 스타일은 `<head>` 태그 안에 `<style></style>` 태그안에 기입하는 방법이다.
- 외부 스타일은 프로젝트 내부에 CSS 파일을 생성하여 아래와 같은 코드로 적용한다.
  ```html
  <link href="CSS 파일 경 로" rel="stylesheet">
  ```
- CSS를 적용하는 코드의 모양은 `스타일이름: 스타일값; 스타일 이름: 스타일값; ...` 이런식으로 코딩한다.
  ```html
  <p style="font-size: 20px; color: red">글자</p>
  ```
- 텍스트를 꾸밀 때 사용하는 속성은 아래와 같다.
  ```css
  font-size : 20px;
  font-family : 'gulim';
  color : black;
  letter-spacing : -1px;
  text-align : center;
  font-weight : 600;
  ```
- 이미지 정렬과 폭 조정하는 속성은 아래와 같다.
  ```css
  display : block;
  margin-left : auto;
  margin-right : auto;
  width : 150px;
  ```
- 텍스트의 일부만 변경하고 싶으면 `<span></span>` 태그를 사용한다.
---
### 이스케이프 문자
- HTML 에서 공백은 스페이스바 로는 나타낼 수 없다. 이스케이프 문자를 사용하여 표현해야 한다.
- 공백 말고도 부등호나 쌍따옴표 같은 문자는 이스케이프 문자를 사용해야 한다.
  - `&lt;` : 작은 부등호 기호
  - `&gt;` : 큰 부등호 기호
  - `&amp;` : 엠퍼샌드 기호(&)
  - `&quot;` : 쌍따옴표(")
  - `&apos;` : 홀따옴표(')
  - `&nbsp;` : 공백(' ')
---
### 스타일 우선순위
- CSS 에서 스타일을 적용할 때는 선택자를 이용하여 스타일을 지정한다.
  - 태그 선택자 : HTML 태그명
  - ID 선택자 : HTML 태그 ID 명
  - CLASS 선택자 : HTML 태그 Class 명
- 우선순위는 아래와 같다.
  1. 인라인 스타일
  2. ID 선택자
  3. CLASS 선택자
  4. 태그 선택자
---
### Float 속성
- `<div></div>` 로 영역을 지정할 때 가로로 정렬을 해야할 때가 있다.
- float 속성을 이용하면 요소를 붕 띄워서 정렬을 한다. 이 때 `<div>` 태그로 한번 감싸줘야 제대로 정렬이 된다.
  ```html
  <div>
    <div class="left-box"></div>
    <div class="right-box"></div>
    <div class="footer"></div>
  </div>
  ```
- float 속성을 지정한 요소 다음에 오는 요소는 제자리를 찾지 못하기 때문에 claer 속성을 사용하여 제자리에 오게 한다.
  ```css
  .footer {
    clear : both
  }
  ```
---
### 배경설정 및 margin collapse
- 이미지를 넣을 때는 `<img>` 태그를 이용했지만 이미지 자체를 배경으로 사용할려면 CSS의 `background-image` 속성을 이용하면 된다.
- 배경관련 CSS 속성들은 다음과 같다.
  ```css
  .main-background {
    background-image : url(../img/shoes.jpg);
    background-size : cover;
    background-repeat : no-repeat;
    background-position : center;
    background-attachment : fixed;
  }
  ```
- `margin collapse` 란 `margin collapse effect` 라고 부르는 일종의 버그이다.
- 부모 자식 태그 간 **margin 간격이 중복되어 의도치 않게 간격 조정이 일어나는 경우**를 말한다.
- 해결하는 방법은 둘 중 한 요소의 `margin` 이나 `padding` 값을 줘서 간격 중복이 일어나지 않게 하면 된다.
---
### position
- 요소의 위치를 지정할 때는 margin 을 이용하여 할 수 있다.
- 하지만 `position` 이라는 속성을 이용하면 좌표값을 통해 위치를 조정할 수 있다.
- 좌표를 지정하는 속성에는 `top`, `left`, `bottom`, `right` 속성을 이용한다.
- 이 때, `position` 은 **좌표속성을 적용할 기준점**이 된다.
- 기준을 정하는 속성값은 다음과 같다.
  - `static` : 좌표적용을 하지 않음
  - `relative` : 현재 요소를 기준
  - `absolute` : 부모 요소중 relative 가 적용된 부모요소를 기준
  - `fixed` : 브라우저 창을 기준
- 예를 들어, `position` 을 통해 요소 가운데 정렬을 하기 위해서는 다음과 같이 한다.
  ```css
  .button {
    position : absolute; 
    left : 0;
    right : 0; 
    margin-left : auto;
    margin-right : auto;
    width : 적절히
  }
  ```
---
### 반응형 width & box-sizing
- div 태그를 통해 **박스를 만들 때 width 를 주게되면 padding 이나 border 를 고려하지 않는다.**
- 만약 `max-width` 값을 `600px` 로 지정한 요소에** padding 값을 넣게 되면 600을 벗어나게 된다.**
- 이를 막기 위해서는 `box-sizing: border-box;` 를 지정한다. 이 속성을 width 값에 padding 과 border 를 포함하게 만든다.
- 보통 CSS 파일 최상단에 셋팅값으로 먼저 선언하게 된다.
- border 가 아닌 padding 만 포함할 수 있다.
  ```css
  .box {
    box-sizing : border-box; /*박스의 폭은 border까지 포함입니다*/
    box-sizing : content-box; /*박스의 폭은 padding 안쪽입니다*/
  }
  ```
- CSS 파일 작성 시 기본으로 세팅하는 코드들이 몇개 있지만 아래 예시는 대표적인 것만 적었다.
  ```css
  div {
    box-sizing : border-box;
  }
  body {
    margin : 0;
  }
  html {
    line-height : 1.15; /*기본 행간 높이*/
  }
  ```
- 위 속성 말고도 `<h>`, `<p>` , `<li>`, `<a>` 등등 기본으로 초기화 할 것들도 많이 적게 된다.
- 필수 기본값 CSS 리스트를 만들어둬서 사용하는 것도 좋은 방법이다.
- CSS 를 적용할 때는 브라우저마다 `<button>` 스타일이나 line-height 강튼 줄간격 등등이 조금씩 다르다.
- 어떤 개발자가 [CSS normalize](https://github.com/necolas/normalize.css/blob/master/normalize.css) 라고 만든 문서가 있는데 여기 스타일을 복붙하면 브라우저간 다르게 보이는 문제들을 미리 해결할 수 있다.
---
### form 태그
- `<input>` 태그는 사용자 입력값을 받을 수 있는 태그이다. type 속성을 통해 여러 형식으로 받을 수 있다. 종류는 다음과 같다.
  ```html
  <input type="text">
  <input type="email">
  <input type="password">
  <input type="radio">
  <input type="file">
  <input type="checkbox">
  <input type="submit">
  <select>
    <option>옵션1</option>
  </select>
  <textarea></textarea>
  ```
- type 속성 외에도 다른 속성들이 더 있다.
  - `placeholder` : 힌트
  - `value` : 미리 입력된 값
  - `name` : 서버로 전송 시 key 가 되는 값
- CSS 에서 태그선택자로 적용할 때 특정 type 에만 지정할 수 있다.
  ```css
  input[type=email] {
    color: grey;
  }
  ```
- 사용자 입력값을 받았으면 제출이나 전송하는 버튼이 필요하다. 보통 `<button>` 태그로도 가능하지만 input 의 type 속성을 통해 만들 수 있다.
  ```html
  <input type="submit" value="전송">
  ```