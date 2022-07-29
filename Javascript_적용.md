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
      10, 10.0, 10e6, 10e-6
2. 문자열(string)
              
3. 불리언(boolean)
4. 심볼(symbol)
5. undefined

객체타입
      
6. 객체(object)
      
      
    
