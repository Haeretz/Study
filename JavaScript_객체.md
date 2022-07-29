## JavaScrupt 객체(Object)
---

### 객체란? 

실생활에서 우리가 인식할 수 있는 사물로 이해할 수 있다

---

### 객체의 예

-고양이

프로퍼티(property)
- cat.name="나비"
- cat.family="코리안 숏 헤어"
- cat.age=0.1
- cat.weight=300

메소드(Method)
- cat.mew()
- cat.eat()
- cat.sleep()
- cat.play()

---
### 자바스크립트 객체

객체 = 이름과 값으로 구성된 프로퍼티의 정렬되지 않은 집합
```
ex)

  var cat="나비";
  
  var kitty = {name="나비", family="코리안 숏 헤어", age:1, weight:0.1};
  
  cat // 나비
  
  kitty.name; //나비
```
---
### 객체의 프로퍼티 참조 

문법 

객체이름.프로퍼티이름

객체이름["프로퍼티이름"]
```
ex)

    var person = {
      name:"홍길동",
      birthday:"030219",
      pId:"12345",
      fullId: function() {
        return this.birthday + this.pId;
      }
    };
    person.name   //홍길동
    person["name"]   //홍길동
```
---
### 객체의 메소드 참조

문법 

객체이름.메소드이름()
```
ex)
    var person = {
      name:"홍길동",
      birthday:"030219",
      pId:"12345",
      fullId: function() {
        return this.birthday + this.pId;
      }
    };
    
    person.fullId() // 03021912345
    
    person.fullId // funcion () {return this.birthday + this.pId;}  
    // 메소드를 참조할 때 뒤에 괄호를 안넣으면 해당 메소드의 정의가 그대로 참조된다
```

---
## 객체의 생성

1. 리터럴 표기(literal notation)을 이용한 방법
2. 생성자 함수(constructor function)을 이용한 방법
3. Object.create() 메소드를 이용한 방법

위와 같은 방법으로 생성되어 메모리에 대입된 객체를 인스턴스라고 한다

---

### 리터럴 표기를 이용한 객체의 생성

가장 쉬운 방법

문법 

   var 객체이름 = {   
    프로퍼티1 이름 = 프로퍼티 1 의 값,  
    프로퍼티2 이름 = 프로퍼티 2 의 값,  
    ... 
    };

---

### 생성자를 이용한 객체의 생성

new 연산자를 사용해 객체를 생성하고 초기화할 수 있다   
이때 사용되는 메소드를 생성자(constructor)라고 하며, 이 메소드는 새롭게 생성되는 개체를 초기화하는 역할을 한다    
자바스크립트는 원시 타입을 위한 생성자를 미리 정의하여 제공해준다    
```
ex) 
    var day = new Date();  // new 연산자를 사용해 Date 타입의 객체를 생성함
    
    documnet.write("올해는" + day.getFullYear() + "년 입니다.");
```
자바스크립트에서 제공하는 생성자를 사용할 수 있고, 사용자가 직접 객체 생성자 함수를 작성하여 사용할 수 도 있다







    




