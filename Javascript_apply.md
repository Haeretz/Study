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
  
(<head>태그 속의 자바스크립트 코드 예제)
  
       <head>
          <meta charset="UTF8">
          <title>JavaScript Apply</title>
          <script>
              function printData() {
                  document.getElementById("date").innerHTML = Date();
              }
          </script>
       </head>
