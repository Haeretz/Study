## JSP 문법

### JSP Expression
```
<%= expression %>
```
- JSP Expression element는 String으로 변환되어 Servlet의 출력에 삽입된다
- 동적인 페이지를 생성한다
- 끝에 세미콜론을 붙이지 않는다

### JSP Scriptlet
```
<% code fragment %>
```
- 간단한 값이 아닌 조금 더 복잡한 것을 수행하고자 할 떄 JSP Scriptlet을 사용한다
- 임의의 JAVA 코드를 삽입할 수 있다
- JSP Scriptlet Tag는 메소드가 아닌 변수만 선언할 수 있다

### JSP Declaraton
```
<%! declaration %>
```
- JSP Declaration을 사용하면 Servlet 클래스에 삽입되는 메소드나 필드를 정의할 수 있다
- JSP Scriptlet Tag와 달리 JSP Declaration Tag는 메소드와 변수 모두 선언할 수 있다

### JSP Comment 
```
<%-- comment --%>
```
- 주석의 개념

### JSP Directive
```
<%@ directive %>
```
- JSP 페이지의 전체적인 구조에 영향을 미친다
- 전체 구조에 대해 WAS에 지시를 내린다
- 지시어에 들어가는 것 : Page, include, taglib
  1. Page 
    - <%@ page attribute = "value" %>
    - page 지시어는 Container에 명령을 제공하는데 사용된다
  2. include
    - <%@ include file = "relative_url" %>
    - include 지시어는 변환 단계에서 다른 외부 파일의 내용을 현재 JSP에 병합하도록 Container에 지시한다
    - 웹 페이지에서 header와  footer의 구성은 거의 동일하기 때문에 외부에서 형식을 만든 후  include 지시어를 이용하여 main.jsp에 병합한다
  3. taglib
    - <%@ taglib uri = "uri" prefix = "prefixOfTag" %>
    - JSP API를사용하면 HTML 또는 XML 태그처럼 보이는 사용자 정의 태그를 정의할 수 있다
    - taglib는 사용자가 정의한 동작을 구현한 사용자 정의태그 집합이다

### JSP Action 

JSP Action XML 구문 안의 구조들을 사용하여 WAS의 동작을 제어한다

1. <jsp:forward> action
   - 다른 리소스(JSP.html 또는 servlet과 같은 정적 페이지)로 요청을 전달하는 데 사용한다
2. <jsp:include> action
   - 현재 JSP페이지에 다른 리소스를 포함시키는데 사용한다
3. <jsp:useBean> action
   - 해당하는 Bean이 이미 존재하는지 확인
   - 객체가 없으면 지정된 객체를 생성
4. <jsp:setProperty> action
   - Bean의 속성을 설정한다
5. <jsp:getProperty> action
   - 주어진 속성값을 가져오는데 사용되며 이를 문자열로 변환하고 동적인 웹 페이지를 생성하는 데 해당 내용을 사용할 수 있다

용도 
1. 동적으로 파일을 삽입하고
2. JavaBean 구성 요소를 재사용하고 
3. 사용자를 다른 페이지로 전달(forward)수 있다
```
ex) 1. forward <jsp:forward page="/display.jsp"/>
    
    2. include <jsp:include page ="/jsp/common/uppermenu.jsp" flush="true" />
    
    3. useBean        [index.html]
    4. getProperty    <form action = "process jsp" method="post">
    5. setProperty    Name:<input type = "text" name="name"><br>
                      Password : <input type="password" name ="password"> <br>
                      Email : <input type="text" name="email"><br>
                      <input type="submit" name="register">
                      </form>
                      
                      [User.java]
                      package beans.user;
                      
                      public class User {
                        private String name, password, email;
                        // setter and getter 
                      }
                      
                      [Process.jsp]
                      <jsp:useBean id="user" class="beans.user"></jsp:useBean>
                      <jsp:setProperty property="*" name="user"/>
                      
                      Record:<br>
   Bean 생성후         <jsp:getProperty property="name" name="user"/> <br>
   property를 적용     <jsp:getProperty property="password" name="user"/><br>
   1. bean 객체를 생성  <jsp:getProperty __property="email"__ name="user"/> <br>
   2. 사용자의 입력을 세팅                     ↳ name 객체의 email필드를 읽어온다 
   3. 각 property를 출력
```

---

### JSP에서 동적인 코드를 호출하는 방법

- use Beans 
  - beans로 구조화된 별도의 Utility class(java class)를 작성한다
  - jsp:useBean, jsp:getProperty, jsp:setProperty를 사용하여 utility class를 호출한다

- Use the MVC architecture
  - MVC 아키텍처를 사용 
  - servlet(Controller)이 요청에 응답하고 적절한 데이터를 검색하여 결과를 Beans(model)에 저장한다
  - 이 결과를 JSP 페이지(View)로 전달하여 결과를 표시한다
  - 즉, JSP 페이지는 Bean을 사용한다

- Use the expression Language
  - shorthand syntax를 이용하여 간단하게 객체 속성(property)에 접근하고 출력한다
  - 즉, jsp
  

