## 프로토타입(Prototype)
---
### 상송(inheritance)

새로운 클래스에서 기존 클래스의 모든 프로퍼티와 메소드를 사용할 수 있는 것을 의미한다

상속을 통해 새로운 프로그램의 요구에 맞게 기존 클래스를 수정하여 재사용할 수 있다

따라서 이런 상속은 추상화, 캡슐화와 더불어 객체 지향 프로그래밍을 구성하는 중요한 특징 중 하나가 된다

프로토타입 기반이기 때문에 상속의 개념이 클래스 기반의 객체지향언어와 약간 다르다

자바스크립트에서는 현재 존재하는 객체를 프로토타입으로 사용하여, 해당 객체를 복제하여 재사용하는 것을 상속이라 한다

---
### 프로토타입(prototype)

자바스크립트의 모든 객체는 프로토타입이라는 객체를 가지고 있다

모든 객체는 그들의 프로토타입으로부터 프로퍼티와 메소드를 상속받는다

이처럼 자바스크립트의 모든 객체는 최소한 하나 이상의 다른 객체로부터 상속을 받으며,

이 때 상속되는 정보를 제공하는 객체를 프로토타입이라고 한다

---

### 프로토타입 체인(prototype chain)

자바스크립트에서는 객체 이니셜라이저를 사용해 생성된 같은 타입의 객체들은 모두 같은 프로토타입을 가진다

또한, new연산자를 사용해 생성한 객체는 생성자의 프로토타입을 자신의 프로토타입으로 상속받는다

```
ex) 

    var obj = new Object();  // 이 객체의 프로토타입은 Object.prototype
    
    var arr = new Array();   // 이 객체의 프로토타입은 Array.prototype
```

하지만 Object.prototype은 어떠한 프로토타입도 가지지 않으며, 프로퍼티도 상속받지 않는다

자바스크립트의 모든 객체는 Object.prototype 객체를 프로토타입으로 상속받는다

위와 같이 프로토타입이 상속되는 가상의 연결 고리를 프로토타입 체인(prototype chain)이라고 한다

---

### 프로토타입의 생성

프로토타입을 생성하는 가장 기본적인 방법은 객체 생성자 함수(Object constructor function)를 작성하는 것이다

생성자 함수를 작성하고 new연산자를 사용해 객체를 생성하면, 같은 프로토타입을 가지는 객체들을 생성할 수 있다
```
ex) 

    function Dog(color, name, age) {
      this.color = color;
      this.name = name;
      this.age=age;
    }
    
    var myDog = new Dog("흰색", "마루", 1);  // 이 객체는 Dog라는 프로토타입을 가진다
    
    document.write("우리집 강아지는" + myDog.name+"라는 이름의 "+myDog.color+"털이 매력적인 강아지입니다.");
```

---

### 객체에 프로퍼티 및 메소드 추가

이미 생성된 객체에 새로운 프로퍼티나 메소드를 추가하는 방법
```
ex) 

    function Dog(color,name,age) {
      this.color= color;
      this.name=name;
      this.age=age;
    }
    var myDog = new Dog("흰색","마루",1);
    
    myDog.family = "시베리안허스키"; // 품종에 관한 프로퍼티를 추가
    
    myDog.breed = function() {    // 털색을 포함한 품종을 반환해 주는 메소드를 추가
```

---
### 프로토타입에 프로퍼티 및 메소드 추가

프로토타입의 경우에는 생성자 함수에 직접 추가해야만 이후에 생성되는 모든 다른 객체에도 적용할 수 있다
```
ex)

    function Dog(color, name, age) {
      this.color = color;
      this.name= name;
      this.age = age;
      this,family ="시베리안 허스키";
      this.breed = functrion() {
        return this.color + " " + this.family;
      };
    }
    
    var myDog = new Dog("흰색", "마루", 1);
    
    var hisDog = new Dog("갈색", "콩이",3);
    
    documnet.write("우리집 강아지는 " + myDog.family + "이고, 친구네 집 강아지도 " + hisDog.family + "입니다");
    
    
      return this.color + " " + this.family;
      
    }
    
    documnet.write("우리집 강아지는 "+myDog.breed()+"입니다.");
```

---

### prototype 프로퍼티

현재 존재하고 있는 프로토타입에 새로운 프로퍼티나 메소드를 보다 쉽게 추가할 수 있다
```
ex) 

    function Dog(color, name, age) {
      this.color=color;
      this.name=name;
      this.age=age;
    }
    
    Dog.prototype.family = "허스키";
    
    Dog.prototype.breed = function() {
      return this.color + " " + this.family;
    };
    
    var myDog = new Dog("흰색","미루",1);
    
    var hisDog = new Dog("갈색", "콩이", 3);
    
    document.write("우리집 강아지는"+myDog.family + "이고 친구네집 강아지도"+hisDog.family+"입니다");
    
    documnet.write("우리 집 강아지의 품종은 " + myDog.breed()+ "입니다");
    
    document.write("친구네 집 강아지의 품종은" + hisDog.breed() + "입니다");
```

직접 생성한 프로토타입의 프로퍼티나 메소드를 추가하거나 삭제할 수 있지만, 

표준객체의 프로토타입을 건드리게 되면 심각한 오류가 발생할 수도 있기 때문에 수정해서는 안된다.



