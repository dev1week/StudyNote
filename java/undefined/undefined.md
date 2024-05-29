# 인터페이스 익명 구현 객체



## 개요&#x20;

> 익명 클래스의 진가는 인터페이스를 익명 객체로 선언하여 사용할 때이다.&#x20;

익명 클래스는 일회성 오버라이딩용이다. 즉, **인터페이스를 일회용으로 구현하여 사용할 필요가 있을 때 , 익명 구현 객체로 선언**하여 사용할 수 있다.&#x20;

```java

interface IAnimal {
    public String bark(); // 추상 메소드
    public String run();
}

public class Main {
    public static void main(String[] args) {
        // 인터페이스 익명 구현 객체 생성
        IAnimal dog = new IAnimal() {
            @Override
            public String bark() {
                return "개가 짖습니다";
            }
            
            @Override
            public String run() {
                return "개가 달립니다";
            }
        };
        
        // 인터페이스 구현 객체 사용
        dog.bark();
        dog.run();
    }
}
```



### 원리

인터페이스 자체로는 객체를 만들 수 없다. 위 코드는 자식 클래스를 생성해서 implements하고 클래스를 초기화한 것이다.&#x20;

원래는 클래스가 인터페이스를 구현한 후 인터페이스를 구현한 클래스로 객체를 만들어야하는데, 위의 코드는 인터페이스를 바로 구현해서 구현한 클래스명 없이 객체를 만들기 때문에 익명 구현 객체라 부른다.&#x20;





## 한계점&#x20;

> 오로지 하나의 인터페이스만 구현하여 객체를 생성할 수 있다.&#x20;

인터페이스의 가장 큰 장점은 다중 상속을 구현할 수 있는 것이다. 하지만 익명 객체는 둘 이상의 인터페이스를 갖거나, 하나의 클래스를 상속 받고 동시에 인터페이스를 구현하는 형태로 구현할 수 없다.&#x20;



### 비슷하게는 만들 수 있다.&#x20;

```java
interface IAnimal {
}

interface ICreature {
}

abstract class myClass {
}

public class Main {
    public static void main(String[] args) {
    
    	// 인터페이스 두개를 구현한 일회용 클래스 (일회용 이라도 어쩔수 없이 따로 선언)
        class useClass1 implements IAnimal, ICreature {
        }

        // 클래스와 인터페이스를 상속, 구현한 일회용 클래스 (일회용 이라도 어쩔수 없이 따로 선언)
        class useClass2 extends myClass implements IAnimal {
        }

        useClass1 u1 = new useClass1() {
        };

        useClass2 u2 = new useClass2() {
        };
    }
}
```











