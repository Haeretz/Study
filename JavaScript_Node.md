## Node 
---
HTML DOM은 노드(node)라고 불리는 계층적 단위에 정보를 저장한다   
HTML DOM은 이러한 노드를 정의하고, 그들 사이의 관계를 설명해 주는 역할을 한다  

![node구조](https://github.com/Haeretz/JavaScript_Study/blob/main/node%EA%B5%AC%EC%A1%B0.jpg)

HTML 문서의 정보는 노드트리라고 불리는 계층적 구조에 저장된다
노드트리는 최상위 레벨인 루트 노드부터 시작하여, 가장 낮은 레벨인 텍스트 노드까지 뻗어 내려간다
JavaScript에서는 HTML DOM을 이용하여 노드트리에 포함된 모든 노드에 접근할 수 있다

---
### 노드의 종류

W3C HTML DOM 표준에 따르면, HTML문서의 모든 것은 노드이다

|노드|설명|
|--|--|
|문서노드(document node)|HTML 문서 전체를 나타내는 노드|
|요소노드(element node)|모든 HTML요소는 요소 노드이며, 속성 노드를 가질 수 있는 유일한 노드|
|속성노드(attribute node)|모든 HTML 요소의 속성은 속성노드이며, 요소 노드에 관한 정보를 가지고 있다<br/>하지만 해당 요소노드의 자식노드에는 포함되지 않음|
|텍스트노드(Text node)|HTML 문서의 모든 텍스트는 텍스트 노드이다|
|주석노드(comment node)|HTML 문서의 모든 주석은 주석노드이다|

---
### 노드간의 관계

노드트리의 모든 노드는 서로 계층적 관계를 맺고 있다

![노드구조2](https://github.com/Haeretz/JavaScript_Study/blob/main/node%EA%B5%AC%EC%A1%B02.jpg)

* 최상위 레벨인 루트노드를 제외한 모든 노드는 부모노드를 단 하나만 가질 수 있다
* 모든 요소노드는 자식노드를 가질 수 있다
* 형제노드란 같은 부모노드를 가지는 모든 노드를 말한다
* 조상노드는 부모노드를 포함해 계층적으로 현재 노드보다 상위에 존재하는 모든 노드를 말한다
* 자손노드는 자식노드를 포함해 계층적으로 현재 노드보다 하위에 존재하는 모든 노드를 말한다

---
### 노드로의 접근

1. getElementByTagName() 메소드를 이용하는 방법

getElementByTagName() 메소드는 특정 태그 이름을 가지는 모든 요소를 노드 리스트의 형태로 반환한다

따라서 이 메소드가 반환하는 노드 리스트를 이용하면 원하는 노드에 접근할 수 있다

2. 노드간의 관계를 이용해 접근하는 방법

* parentNode : 부모노드
* childNodes : 자식노드 리스트
* firstChild : 첫 번째 자식노드
* lastChild : 마지막 자식 노드
* nextSibling : 다음 형제 노드
* previousSibling : 이전 형제 노드

위와 같은 프로퍼티를 이용하여 원하는 노드에 접근할 수 있다

---
### 노드에 대한 정보

노드에 대한 정보는 다음과 같은 프로퍼티를 통해 접근할 수 있다

1. nodeName
2. noodeValue
3. nodeType

이 프로퍼티들은 특별히 다른 인터페이스를 이용하지 않고도, 해당 노드의 정보에 직접 접근할 수 있는 방법을 제공한다

> nodeName

> 노드 고유의 이름을 저장하므로, 읽기 전용 프로퍼티이다
> |노드|프로퍼티 값|
> |--|--|
> |문서노드|'#document'|
> |요소노드|태그이름(대문자)|
> |속성노드|속성이름|
> |텍스트노드|'#text'|

(예제)

　document.getElementById("document").innerHTML = document.childNodes[1].nodeName;   //HTML

　document.getElementById("HTML")=document.childNodes[1].childeNodes[0].nodeName;    //HEAD

>nodeValue

>nodeValue 프로퍼티는 노드의 값을 저장한다
> |노드|프로퍼티 값|
> |--|--|
> |요소노드|undefined|
> |속성노드|해당 속성의 속성값|
> |텍스트노드|해당 텍스트 문자열|

(예제)

　// 아이디가 "heading"인 요소가 첫 번째 자식 노드의 노드값을 선택함
 
 　var headingText = document.getElementById("heading").firstChild.nodeValue;
  
  　document.getElementById("text1").innerHTML = headingText;
   
   　document.getElementById("text1").firstChild.nodeValue = headingText;
    
>nodeType

>nodeType은 노드 고유의 타입을 저장하므로, 읽기 전용 프로퍼티다
> |노드|프로퍼티 값|
> |--|--|
> |요소노드|1|
> |속성노드|2|
> |텍스트노드|3|
> |주석노드|8|
> |문서노드|9|

// 아이디가 "heading"인 요소가 첫 번째 자식 노드의 노드값을 선택함
　var headingType = document.getElementById("heading").firstChild.nodeType;
 
 　document.getElementById("head").innerHTML = headingType; //3
  
  　document.getElementById("document").innerHTML= document.nodeType; //9
   
---
### 빈 택스트 노드의 처리

파이어폭스나 기타 브라우저들은 띄어쓰기나 줄 바꿈을 텍스트 노드로 취급한다

하지만 익스플로러는 띄어쓰기나 줄 바꿈을 텍스트 노드로 취급하지 않는다


이 차이를 없애는 가장 쉬운 방법은 nodeType프로퍼티를 이용해 선택된 요소의 타입을 검사하는 것이다

(예제)

　  var lastNode;

function findLastChild(parentNode) {

    lastNode = parentNode.lastChild;

    while (lastNode.nodeType != 1) {

        lastNode = lastNode.previousSibling;

    }

}

function printLastChild() {

    var parentNode = document.getElementById("parentNode");

    findLastChild(parentNode);

    document.getElementById("nodename").innerHTML = lastNode.nodeName;
}

마지막 자식 노드를 찾은 후에, 찾은 노드의 타입이 요소 노드가 아니면 그 앞의 노드를 다시 검사한다

---

## 노드의 관리

---

### 노드의 추가

다음 메소드를 사용하면 특정 위치에 새로운 노드를 추가할 수 있다.

1. appendChild()
2. insertBefore()
3. insertData()

> appendChild() 
> 새로운 노드를 해당 노드의 자식 노드리스트의 맨 마지막에 추가한다
> (예제)
> function appendNode() {
>   var parent = document.getElementById("list"); //아이디가 'list'인 요소를 선택함
>   var newitem = document.getElementById("item"); //아이디가 'item'인 요소를 선택함
>   parent.appendChild(newItem); }                  //해당 요소의 맨 마지막 자식 노드로 추가함

---

> insertBefore() 
> 새로운 노드를 새로운 노드를 특정 자식 노드 바로 앞에 추가한다
> (원형) 
> 부모노드.insertBefore(새로운자식노, 기준자식노드);
> 새로운 자식 노드 : 자식 노드 리스트에 새롭게 추가할 자식 노드를 전달한다
> 기준 자식 노드 : 새로운 노드를 삽입할 때 기준이 되는 노드로 이 노드 바로 앞에 새로운 노드가 추가된다
> (예제)
> function appendNode() {
>   var parent = document.getElementById("list");
>   var criteriaItem = document.getElementById("criteria");
>   var newItem = document.getElementById("item");
>   parent.insertBefore(newItem,criteriaItem); //해당 노드를 기준이 되는 자식 노드의 바로 앞에 추가함

---

> insertData() 메소드
> 텍스트 노드의 텍스트 데이터에 새로운 텍스트를 추가한다
> (원형)
> 텍스트노드.insertData(오프셋, 새로운데이터);
> 1. 오프셋 : 오프셋 값은 0부터 시작하며, 기존 데이터의 몇 번째 위치부터 추가할지를 전달한다
> 2. 새로운 데이터 : 새로이 삽입할 텍스트 데이터를 전달한다
> (예제)
> var text = document.getElementById("text").firstChild;
> function appendText() {
>  text.insertData(6," 나른한");} //텍스트 노드의 6번째 문자부터 "나른한" 이란 데이터를 추가함

---

### 노드의 생성

생성할 노드의 종류에 따라 다음과 같은 메소드를 사용할 수 있다
1. createElement()
2. createAttribute()
3. createTextNode()

---

### 요소 노드의 생성

createElement()를 사용해 새로운 요소 노드를 만들수 있다

(예제)

    function createNode() {

　   var criteriaNode = document.getElementById("text");
    
　   var newNode = document.getElementById("p"); //새로운 p요소를 생성함
    
　   newNode.innerHTML = "새로운 단락입니다."; 
    
　   document.body.insertBefore(newNode, criteriaNode);} //새로운 요소를 기준이 되는 요소 바로 앞에 추가함
 
 ---
 
 ### 속성노드의 생성
 
 createAttribute()를 사용하여 새로운 속성노드를 만들수 있다
 
 만약 같은 이름의 속성 노드가 존재하면 기존의 속성 노드는 새로운 속성노드롤 대체된다
 
 이미 존재하는 요소노드에 속성노드를 생성하고자 할 때에는 setAttribute()로 할 수 있다
 
 (예제)
 
    function createNode() {
 
   　var text = document.getElementById("text");
  
  　 var newAttribute = document.createAttribute("style"); // 새로운 style 속성 노드를 생성
   
  　 newAttribute.value = "color:red";  
    
     text.setAttributeNode(newAttribute); }  // 해당 요소의 속성 노드로 추가함
     
---

### 텍스트 노드의 생성

createTextNode()를 이용해 새로운 텍스트 노드를 만들 수 있다.

(예제)

     function createNode() {
     
       var elementNode = document.getElementById("text");
       
       var newText = document.createTextNode("새로운 텍스트 노드를 생성"); //새로운 텍스트 노드를 생성
       
       elementNode.appendChild(newText); }  // 해당 요소의 자식 노드로 추가함
       
---

### 노드의 제거

1. removeChild()
2. removeAttribute()

---

### removeChild() 

자식 노드 리스트에서 특정 자식 노드를 제거한다

이 메소드는 노드가 제거되면 제거된 노드를 반환한다

노드가 제거될 때 그 노드의 자식들도 다 같이 제거된다

(예제)

    var parent =document.getElementById("list");
    
    var removeItem = document.getElementById("item");
    
    parent.removeChild(removedItem); //지정된 요소를 삭제함 
    
---

### removeAttribute() 

속성의 이름을 이용해 특정 속성노드를 제거한다

(예제)

    var text= document.getElementById("text");
    text.removeAttribute("style");    //해당 요소의 style 속성을 제거
    
---

### 노드의 복제

cloneNode()를 사용하면 특정 노드를 복제할 수 있다

기존의 존재하는 노드와 똑같은 노드를 생성해 반환한다

(원형)

복제할 노드.cloneNode(자식노드복제여부);

(예제)

    function cloneElement() {
    
     var parent = document.getElementBtId("list");
     
     var originItem = document.getElementById("item");
     
     parent.appendChild(originItem.cloneNode(true)); }  // 해당 노드를 복제하여 리스트의 맨 마지막에 추가
     
---

## 노드의 조작 

---

### 노드의 값 변경 

nodeValue프로퍼티를 사용하면 특정 노드의 값을 변경할 수 있다

setAttribute()는 속성노드의 값을 변경할 수 있다

---

### 요소 노드의 텍스트 

요소 노드의 자신이 직접 만든 텍스트값을 가지지 않는다

요소노드의 텍스트는 요소 노드의 자식 노드인 텍스트노드에 저장된다

따라서 요소 노드의 텍스트 값을 확인하거나 변경하고자 할 때는 요소 노드에 포함된 텍스트 노드에 접근해야 한다

---

### 텍스트 노드의 값 변경

nodeValue 프로퍼티를 사용해 텍스트 노드의 값을 변경할 수 있다

(예제)

    var para = document.getElementById(text");
    
    function changeText() {
    
     para.firstChild.nodeValue = "텍스트 변경 완료"); } 
     
---

### 속성 노드의 값 변경

속성노드는 nodeValue 프로퍼티, setAttribute() 메소드를 사용하여 값을 변경할 수 있다

(예제)

     var para;
     
     function changeAttribute() {
     
      // 모든 p 요소둥에서 첫 번쩨 요소에 클래스 속성값으로 para를 설정함 
      
     document.getElementByTagName("p")[0].setAttribute("class", "para"); }
     
     // 클래스가 설정되면 해당 클래스에 설정되어 있던 스타일이 자동으로 
