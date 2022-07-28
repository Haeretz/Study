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







