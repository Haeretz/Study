## 자바스크립트 적용
---
### 자바스크립트를 적용하는 방법

HTMl 문서에 자바스크립트 코드를 적용하는 방법

1. 내부 자바스크립트 코드로 적용
2. 외부 자바스크립트 파일로 적용

---

### 내부 자바스크립트 코드

'<script>' 코드를 사용해 적용가능하다

(문법)

      <script>
        
        document.getElementById("text").innerHTML = "여러분을 환영합니다";
          
      </script>
  
  이렇게 삽입된 자바스크립트 코드는 HTML문서의 <head>나 <body> 태그, 또는 양쪽 모두에 위치할 수 있다
  
( <head>태그 속의 자바스크립트 코드 예제)
  
       <head>
          <meta charset="UTF8">
          <title>JavaScript Apply</title>
          <script>
              function printData() {
                  document.getElementById("date").innerHTML = Date();
              }
          </script>
       </head>

( <body>태그 속의 자바스크립트 코드 예제)
      
      <body>
           <p>자바스크립트를 이용하면 날짜와 시간에도 쉽게 접근가능 </p>
           <button onclick="printDate()">현재 날짜와 시간 표시!</button>
           <p id="date"></p>
           <script>
                 function printDate() {
                     documnet.getElementById("date").innerHTML = Date();
                 }
           </script>
      </body>
      
---
      
### 외부 자바스크립트 파일
      
자바스크립트 코드는 HTML문서의 내부뿐만 아니라 외부 파일로 생성하여 삽입도 가능하다

외부에 작성된 자바스크립트 파일은 .js 확장자를 사용한다
(적용법)
      
      [example.js]
      
      function printDate() {
         document.getElementById("date").innerHTML = Date();
      }
　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　
  
      <head>
          <meta charset="UTF8">
          <title>JavaScript Apply</title>
          <script src="/examples/media/example.js"></script>
      </head>
      
---
      
### 기본타입 
      
1. 숫자(number) 
      
      정수, 실수 구분없이 실수로 표현 / 매우 작거나 큰 단위는 e 표기법을 사용가능
      
      ex) 10, 10.0, 10e6, 10e-6
      
2. 문자열(string)
      
      큰따옴표, 작은따옴표로 둘러싸인 문자의 집합
      
      숫자와 문자열을 더해서 연결시킬 수 있다                   
      
3. 불리언(boolean)
      
      참(true)과 거짓(false)를 나타낸다
      
4. 심볼(symbol)
      
      ECNASCript6부터 새롭게 추가된 타입
      
      유일하고 변경할 수 없는 타입

* typeof 연산자
      
      피연산자의 타입을 반환하는 연산자
      
      ex) typeof 10; // number타입
      
5. undefined
      
      자바스크립트에서 null이란 object타입이며, 아직 값이 정해지지 않은 것을 의미한다
      
      undefined란 null과 달리 '타입'이 정해지지 않은 것을 의미한다
      
      초기화하지 않은 변수나 존재하지 않는 값에 접근할 때 반환한다
      ```
      ex)  var num; // 초기화하지 않았으므로 undefined를 반환한다
      
           typeof text; // 정의되지 않는 변수에 접근하면 undefined 값을 반환함
      ```
객체타입
      
6. 객체(object)
      
      자바스크립트의 기본 타입은 객체이다
      
      객체는 여러 프로퍼티(property)나 메소드(method)를 같은 이름으로 묶어놓은 일종의 집합체다
      ```
      ex) var dog = {name:"해피";age:3};
      
          document.getElementById("result").innerHTML = "강아지의 이름은 "+ dog.name + "이고, 나이는 " + dog.age + "살 입니다.";
      ```

      
      
      
    
