# JavaScript
---
자바스크립트는(JavaScript)는 객체(Object)기반의 스크립트언어다.
HTML로는 웹의 내용을 작성하고, CSS로는 웹을 디자인하고, JavaScript로는 웹의 동작을 구현한다.

## JavaScript의 역사
---
1995년 넷스케이프(Netscape)의 브렌던 아이크(Brendan Eich)에 의해 만들어졌다.
처음엔 모카라는 이름으로 개발되었으나, 그 후에 라이브스크립트, 최종적으로는 자바스크립트라는 이름으로 변경된다.

## JavaScript 특징
---
* 객체 기반의 스크립트 언어
* 동적이며, 타입을 명시할 필요가 없는 인터프리터 언어
* 객체 지향형 프로그래밍과 함수형 프로그래밍을 모두 표현가능

## Java & JavaScript
---
|자바|자바스크립트|
|--|--|
|컴파일 언어|인터프리터 언어|
|타입검사 엄격|타입 명시x|
|클래스 기반 객체지향언어|프로토타입기반의 객체지향언어|

## JavaScript 소개
---
1. 자바스크립트는 HTML의 '내용'을 변경할 수 있다
2. 자바스크립트는 HTML의 '속성'을 변경할 수 있다
3. 자바스크립트는 HTML의 '스타일'을 변경할 수 있다 

## JavaScript 문법
---
* 실행문은 ';'로 구분
* 대소문자를 구분한다
### 리터럴(literal)
리터럴은 표현되는 값 그 자체를 의미한다
### 식별자(Identifier)
변수나 함수의 이름을 작성할 때 사용하는 이름
JavaScript에서는 영문자, 숫자, '_', '$'만 사용가능하다
Camel Case 방식을 사용한다
### 키워드
몇몇 단어들을 특별한 용도로 사용하기 위해 예약어로 지정해 놨다
- var -> 변수의 정의를 위한 키워드
- function -> 함수의 정의를 위한 키워드
### 주석
* 한 줄 주석 : // 주석문
* 여러 줄 주석 : /* 주석문 */
* 여러 줄 주석은 중첩이 안된다
* 여러 줄 주석안에 한 줄 주석은 넣을 수 있다

## JavaScript 출력
---
1. Window.alert() 메소드
2. HTML DOM 요소를 이용한 innerHTML 프로퍼티
3. document.write() 메소드
4. console.log() 메소드

### Window.alert() 메소드
가장 간단한 출력 방법으로 브라우저와 별도의 대화상자를 띄운다  
  window.alert("메세지");

### HTML DOM 요소를 이용한 innerHTML 프로퍼티
가장 많이 사용되는 방법으로 document 객체의 getElementByID() 나 getElementsByTagName() 등의 메소드를 사용하여 HTML요소를 선택하고,
innerHTML 프로퍼티를 이용하면 선택된 HTML요소의 내용(content)이나 속성(attribute)값 등을 손쉽게 변경할 수 있다

### DOM 요소
HTML 요소를 다루기 위해서는 우선 해당 요소를 선택해야 한다
1. HTML 태그 이름을 이용한 선택<br/>  
  getElementsByTagName() 메소드는 HTML태그 이름을 이용하여 HTML요소를 선택한다  <br/><br/>
  ex) var selectedItem = document.getElementsByTagName("li");  // 모든 'li' 요소를 선택함<br/>
  for(var i=0; i<selectedItem.length;i++){  <br/>
  selectedItem.item.style.color = "red";}   // 선택된 모든 요소의 텍스트 색상을 변경함 <br/><br/>
2. 아이디를 이용한 선택  <br/>
  getElementById() 메소드는 아이디를 이용하여 HTML 요소를 선택한다  <br/><br/>
  ex) var selectedItem = document.getElementById("even"); // 아이디가 "even"인 요소를 선택함<br/>
  selectedItem.stlye.color = "red"; //선택된 요소의 텍스트 색상을 변경함  <br/><br/>
3. 클래스를 이용한 선택  <br/>
  getElementByName() 메소드는 HTML요소의 name속성을 이용하여 HTML 요소를 선택한다  <br/><br/>
  ex) var selectedItem = document.getElementByClassName("odd"); //클래스가 odd인 모든 요소를 선택함  <br/>
  for(var i=0; i<selectedItem.length;i++) {                                                <br/>
  selectedItem.item(i).style.color="red"; //선택된 모든 요소의 택스트 색상을 변경함  <br/><br/>
4. name 속성을 이용한 선택  <br/>
  getElementByName() 메소드는 HTML요소의 name속성을 이용하여 HTML요소를 선택한다  <br/><br/>
  ex) var selectedItem = document.getElementsByName("first"); //name 속성 값이 first인 모든 요소를 선택함  <br/>
  for(var i=0; i<selectedItem(i).style.color = "red"; //선택된 모든 요소의 텍스트 색상을 변경함.  <br/><br/>
5. CSS 선택자를 이용한 선택  <br/>
  querySelectorAll() 메소드는 CSS선택자(아이디, 클래스.속성, 속성값 등)를 이용하여 HTML요소를 선택한다 <br/><br/>
  ex) var selectItem = document.querySelectorAll("li.odd");  //클래스가 "odd"인 요소 중에서 'li' 요소만을 선택함  <br/>
  for(var i=0; i<selectedItem.length; i++) {  <br/>
  selectedItem.item(i).style.color="red"; // 선택된 모든 요소의 텍스트 색상을 변경함  <br/><br/>
  
6. HTML객체 집합(object collection)을 이용한 선택  <br/>
  HTML DOM에서제공하는 객체 집합(Object Collection)을 이용하여 HTML 요소를 선택할 수 있다 <br/><br/>
  ex) var title = document.title; // <title> 요소를 선택함  <br/>
  document.write(title);  <br/><br/>
  ---
 ### DOM 요소의 내용변경
  ---
  HTML DOM을 이용하면 HTML 요소의 내용(content)이나 속성값 등을 손쉽게 변경할 수 있다
  ex) var str = document.getElementById("text");
      str.innerHTML = "이 문장으로 바뀌었습니다!";
  
  ### DOM 요소의 스타일 변경
  ---
  HTML DOM을 이용하면 HTML 요소의 스타일도 변경가능하다 
    ex) var str = document.getElementById("text");   // 아이디가 "text"인 요소를 선택함
        function changRedColor() { str.style.color = "red";}     //해당 요소의 글자색을 빨간색으로 변경
        function changeBlackColor() { str.style.color="black";} //해당 요소의 글자색을 검정색으로 변경
  





