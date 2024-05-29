# 익명 클래스

## 개요&#x20;

이름이 없는 클래스를 의미한다.&#x20;

이름이 없다는 것은 기억되지 않아도 된다는 것이며, 나중에 불러질 이유가 없음을 내포한다. 즉, 프로그램에서 일시적으로 한번만 사용되고 버려지는 객체라 보면 된다.&#x20;



#### 일반적인 객체 생성하기&#x20;

보통 어느 클래스의 자원을 상속 받아 재정의하여 사용하기 위해서는 먼저 자식이 될 클래스를 만들고 상속 후 객체 인스턴스 초기화를 통해 가능하다.&#x20;

```java
// 부모 클래스
class Animal {
    public String bark() {
        return "동물이 웁니다";
    }
}

// 자식 클래스
class Dog extends Animal {
	@Override
    public String bark() {
        return "개가 짖습니다";
    }
}

public class Main {
    public static void main(String[] args) {
        Animal a = new Dog();
        a.bark();
    }
}
```

#### 일반적인 방법과 대비되는 익명 클래스의 특성&#x20;

익명 클래스는 클래스 정의와 동시에 객체를 생성할 수 있다.&#x20;

아래 예시를 확인하면 익명으로 인라인으로 한번에 선언하여 사용할 수 있다. \
익명클래스를 통해서 상속받은 클래스를 작성해야하는 부담을 줄일 수 있다. \
(위 예시에서는 Animal을 상속 받은 Dog 클래스를 작성해야한다.)&#x20;

```java
// 부모 클래스
class Animal {
    public String bark() {
        return "동물이 웁니다";
    }
}

public class Main {
    public static void main(String[] args) {
        // 익명 클래스 : 클래스 정의와 객체화를 동시에. 일회성으로 사용
        Animal dog = new Animal() {
            @Override
            public String bark() {
                return "개가 짖습니다";
            }
        }; // 단 익명 클래스는 끝에 세미콜론을 반드시 붙여 주어야 한다.
        	
        // 익명 클래스 객체 사용
        dog.bark();
    }
}
```



## 용도&#x20;

> 새로운 클래스를 익명으로 사용하는 것이 아니라, **이미 정의되어 있는 클래스의 멤버를 재정의하여 사용할 필요**가 있고, **일회성으로 이용**해야할 때 사용한다.&#x20;



## 유의점&#x20;

### 오버라이딩 된 메서드는 외부에서 사용할 수 없다.&#x20;

```java
// 부모 클래스
class Animal {
    public String bark() {
        return "동물이 웁니다";
    }
}

public class Main {
    public static void main(String[] args) {
        Animal dog = new Animal() {
            // @Override 메소드
            public String bark() {
                return "개가 짖습니다";
            }
            
            // 새로 정의한 메소드
            public String run() {
                return "달리기 ㄱㄱ싱";
            }
        };
        
        dog.bark();
        dog.run(); // ! Error - 외부에서 호출 불가능
    }
}

```



```
Animal dog = new Animal()
```

을 사용할 때 생성되는 객체는 Animal 클래스의 익명클래스이다. 부모인 Animal 클래스 자체에는 run() 메서드가 선언되어 있지 않기 때문에 사용하지 못한다.&#x20;



### 내부 클래스에서 사용할 수 있는 외부 변수는 final 상수이다.&#x20;

익명 클래스도 내부 클래스의 일종이기 때문에, 외부의 지역 변수를 이용하려고 할 때, 똑같이 내부 클래스의 제약을 받는다.&#x20;





## 선언 위치&#x20;

> 어디에 선언하느냐에 따라 구분한다.&#x20;

### 클래스 필드로 이용&#x20;

```java
class Animal { ... }

class Creature {
    // 필드에 익명자식 객체를 생성 하여 이용
    Animal dog = new Animal() {
        public String bark() {
            return "멍멍";
        }
    };

    public void method() {
        dog.bark();
    }
    
    public void method2() {
        dog.bark();
    }
}
```

특정 클래스 내부에서 여러 메서드로 이용할 때 사용해볼만 하다.&#x20;



### 지역 변수로서 이용&#x20;

```java
class Animal { ... }

class Creature {
	// ...
    
    public void method() {
    	// 지역 변수같이 클래스를 선언하여 일회용으로 사용
        Animal dog = new Animal() {
            public String bark() {
                return "멍멍";
            }
        };
        dog.bark();
    }
}
```

메서드에서 일회용으로 사용하고 버려질 클래스일 경우 사용해볼만 하다.&#x20;



### 메서드 아규먼트로 이용&#x20;

```java
class Animal { ... }

class Creature {
	// ...
    
    public void method(Animal dog) { // 익명 객체 매개변수로 받아 사용
        dog.bark();
    }
}

public class Main {
    public static void main(String[] args) {
        Creature monster = new Creature();
        
        // 메소드 아규먼트에 익명 클래스 자체를 입력값으로 할당
        monster.method(new Animal() {
            public String bark() {
                return "멍멍";
            }
        });
    }
}
```

#### 조건&#x20;

1. 메서드 매개변수로서 클래스 자료형을 이용할 때&#x20;
2. 일회성으로만 사용할 때&#x20;

위 두가지 조건을 충족할 때 사용해볼만하다.&#x20;





## 익명 클래스 컴파일&#x20;

> 자바파일명${익명 객체 정의 순번}.class 로 컴파일 됩니다.&#x20;

Main.java 파일에서 Animal 클래스의 익명 객체를 정의했다면, 컴파일 후 Main.class, Animal.class, Animal$1.class 이렇게 3개의 파일이 생긴다.&#x20;



