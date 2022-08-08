## JSP 
### JSP란 

정적인 HTML의 동적인 Java코드를 넣어 만든 Server Side 스크립트다

즉, 사용자가 입력한 컨텐츠를 가지고 동적인 웹페이지를 만든다

servelet의 기능 + 추가적인 기능을 구현한다

---
### JSP의 동작

1. JSP가 실행되면 WAS는 내부적으로 JSP파일을 Java Servlet(.java)으로 변환


2. WAS는 변환한 Servlet을 동작해 필요한 기능을 수행한다

  - Servlet의 동작
  - 1) WAS는 사용자 요청에 맞는 적절한 Servlet파일을 컴파일(.class파일)한다
  - 2) .class 파일을 메모리에 올려 Servlet 객체를 만든다
  - 3) 메모리에 로드될 때 Servlet 객체를 초기화하는 init()메소드가 실행된다
  - 4) WAS는 Request가 올 때마다 thread를 생성하여 처리한다
  - 5) 각 thread는 Servlet의 단일 객체에 대한 Service() 메서드를 실행한다
  - 6) service() 메소드는 요청에 맞는 적절한 메소드를 호출한다

3. 수행 완료 후 생성된 데이터를 웹 페이지와 함깨 클라이언트로 응답한다

---

### JSP의 특징

- 스크립트 언어이기 때문에 자바 기능을 그대로 사용할 수 있다
- Tomcat(WAS)이 이미 만들어놓은 객체를 사용한다
   - Ex) request,response, session 등
- 사용자 정의 태그를 사용해, 보다 효율적으로 웹 사이트를 구성할 수 있다
- HTML 코드 안에 Java코드가 있기 때문에 HTML코드를 작성하기 쉽다
- Servlet과 다르게 JSP는 수정된 경우 재배포할 필요 없이 Tomcat(WAS)가 알아서 처리한다

#### Predenfined Value(또는 Implicit Object)

- 미리 정의된 객체로, WAS가 제공하는 객체를 의미한다
  - request : the HttpServletRequest Object
  - response : the HttpServletResponse Object
  - session : the HttpSession Object
  - out : the PrintWriter Object
  - application : the ServletContext Object
