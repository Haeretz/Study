## DOM 요소
---

HTML 요소를 다루기 위해서는 우선 해당 요소를 선택해야 한다
1. HTML 태그 이름을 이용한 선택<br/>  
  
  getElementsByTagName() 메소드는 HTML태그 이름을 이용하여 HTML요소를 선택한다  
  ```
  ex)
  var selectedItem = document.getElementsByTagName("li");  // 모든 'li' 요소를 선택함
  
  for(var i=0; i<selectedItem.length;i++){
  
  selectedItem.item.style.color = "red";}   // 선택된 모든 요소의 텍스트 색상을 변경함 
  ```
2. 아이디를 이용한 선택
  
  getElementById() 메소드는 아이디를 이용하여 HTML 요소를 선택한다
  ```
  ex) var selectedItem = document.getElementById("even"); // 아이디가 "even"인 요소를 선택함
  
  selectedItem.stlye.color = "red"; //선택된 요소의 텍스트 색상을 변경함
  ```
3. 클래스를 이용한 선택 
  getElementByName() 메소드는 HTML요소의 name속성을 이용하여 HTML 요소를 선택한다 
  ```
  ex) 
  var selectedItem = document.getElementByClassName("odd"); //클래스가 odd인 모든 요소를 선택함
  
  for(var i=0; i<selectedItem.length;i++) {                                                
  
    selectedItem.item(i).style.color="red"}; //선택된 모든 요소의 택스트 색상을 변경함  
  ```
4. name 속성을 이용한 선택
  
  getElementByName() 메소드는 HTML요소의 name속성을 이용하여 HTML요소를 선택한다 
  ```
  ex)
    var selectedItem = document.getElementsByName("first"); //name 속성 값이 first인 모든 요소를 선택함 
    
    for(var i=0; i<selectedItem(i).style.color = "red"; //선택된 모든 요소의 텍스트 색상을 변경함.  
  ```
5. CSS 선택자를 이용한 선택  

  querySelectorAll() 메소드는 CSS선택자(아이디, 클래스.속성, 속성값 등)를 이용하여 HTML요소를 선택한다
  ```
  ex)
      var selectItem = document.querySelectorAll("li.odd");  //클래스가 "odd"인 요소 중에서 'li' 요소만을 선택함  

        for(var i=0; i<selectedItem.length; i++) { 
        
        selectedItem.item(i).style.color="red"}; // 선택된 모든 요소의 텍스트 색상을 변경함  
  ```
6. HTML객체 집합(object collection)을 이용한 선택

  HTML DOM에서제공하는 객체 집합(Object Collection)을 이용하여 HTML 요소를 선택할 수 있다
  ```
  ex)
  var title = document.title; // <title> 요소를 선택함  
  
  document.write(title); 
  ```
  ---
 ### DOM 요소의 내용변경
  ---
  HTML DOM을 이용하면 HTML 요소의 내용(content)이나 속성값 등을 손쉽게 변경할 수 있다 
  ```
  ex) 
  var str = document.getElementById("text");
  
  str.innerHTML = "이 문장으로 바뀌었습니다!";
  ```
  
  ### DOM 요소의 스타일 변경
  ---
  HTML DOM을 이용하면 HTML 요소의 스타일도 변경가능하다
  ```
    ex) 
    var str = document.getElementById("text");  
    
    function changRedColor() { str.style.color = "red";}  
    
    function changeBlackColor() { str.style.color="black";} 
  ```
