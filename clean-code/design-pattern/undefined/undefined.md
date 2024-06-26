---
description: 구현 방식의 패밀리를 정의하고, 각 패밀리를 별도의 클래스에 넣어 객체를 상호교환합니다.
---

# 전략 패턴



## 문제&#x20;

### 네비게이션의 자동 경로 계획 기능&#x20;

당신은 사용자가 주소를 입력하면 목적지로 가는 가장 빠른 경로를 볼 수 있는 기능을 개발해야합니다.

### 개발시 발생하는 문제들&#x20;

<figure><img src="../../../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>

도로 경로, 도보 경로, 대중 교통 사용 시, 자전거를 사용하는 경로 등 **새 경로 알고리즘을 추가할 때마다** 유지보수하기 매우 어려워집니다.&#x20;

1. 간단한 버그를 수정하거나, 알고리즘 중 하나를 변경하면 전체 클래스에 영향을 미쳐 이미 작동하는 코드에서 오류가 발생하기 시작했습니다.&#x20;
2. 하나의 클래스에서 관리하기 때문에 병합 충돌 위험이 커집니다.&#x20;



## 전략 패턴&#x20;

> 특정 작업을 다양한 방식으로 수행하는 클래스를 선택한 후 모든 알고리즘을 전략이라는 별도의 클래스로 추출합니다.&#x20;

## 클래스 다이어그램&#x20;

<figure><img src="../../../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>





## 설명&#x20;

<figure><img src="../../../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>

### 콘텍스트&#x20;

* 전략을 선택하기 위한 필드가 있어야합니다.&#x20;
* 콘텍스트는 작업을 실행하는 대신, 연결된 전략객체에 작업을 위임합니다.&#x20;

### 클라이언트&#x20;

* 원하는 전략을 콘텍스트에 전달합니다.&#x20;
* 일반 인터페이스(Strategy)를 통해 모든 전략을 실행할 수 있습니다.&#x20;
* 선택된 전략 내에 캡슐화된 알고리즘을 작동시킬 단일 메서드만 노출합니다.&#x20;



\-> 콘텍스트가 구상 전략들에 의존하지 않게 되므로, 콘텍스트 또는 다른 전략들의 코드를 변경하지 않고도 새 알고리즘들을 추가하거나, 기존 알고리즘을 수정할 수 있습니다.&#x20;





## 코드 예시&#x20;

### 전략 인터페이스&#x20;

```java
interface Strategy {
    int execute(int a, int b);
}
```

* 전략 인터페이스는 어떤 알고리즘의 공통적인 작업을 선언합니다.&#x20;
* 컨텍스트는 이 인터페이스를 사용하여 구상 전략에 의해 구현된 알고리즘을 호출합니다.&#x20;

### 구상 전략&#x20;

```java
class ConcreteStrategyAdd implements Strategy {
    public int execute(int a, int b) {
        return a + b;
    }
}

class ConcreteStrategySubtract implements Strategy {
    public int execute(int a, int b) {
        return a - b;
    }
}

class ConcreteStrategyMultiply implements Strategy {
    public int execute(int a, int b) {
        return a * b;
    }
}
```

* 전략 인터페이스의 구현체입니다.&#x20;

### 컨텍스트

```java
class Context {
    // 콘텍스트는 전략 객체 중 하나에 대한 참조를 유지합니다. 콘텍스트는 전략의
    // 구상 클래스를 알지 못하며, 전략 인터페이스를 통해 모든 전략과 함께
    // 작동해야 합니다.
    private Strategy strategy;

    // 일반적으로 콘텍스트는 생성자를 통해 전략을 수락하고 런타임에 전략이 전환될 수 있도록 세터도 제공합니다.
    public void setStrategy(Strategy strategy) {
        this.strategy = strategy;
    }

    // 콘텍스트는 자체적으로 여러 버전의 알고리즘을 구현하는 대신 일부 작업을 전략 객체에 위임합니다.
    public int executeStrategy(int a, int b) {
        return strategy.execute(a, b);
    }
}
```

* 클라이언트들이 관심을 갖는 인터페이스를 정의합니다.&#x20;

### 클라이언트&#x20;

```java
class ExampleApplication {
    public static void main(String[] args) {
        Context context = new Context();

        // 숫자 입력을 위한 예제, 실제로는 Scanner 등을 사용하여 입력을 받을 수 있음
        int firstNumber = 10; // 예시 입력 값
        int secondNumber = 5; // 예시 입력 값
        String action = "addition"; // 예시 입력 값 (실제로는 사용자 입력 받아야 함)

        if (action.equals("addition")) {
            context.setStrategy(new ConcreteStrategyAdd());
        } else if (action.equals("subtraction")) {
            context.setStrategy(new ConcreteStrategySubtract());
        } else if (action.equals("multiplication")) {
            context.setStrategy(new ConcreteStrategyMultiply());
        }

        int result = context.executeStrategy(firstNumber, secondNumber);

        // 결과 출력
        System.out.println("Result: " + result);
    }
}
```

* 클라이언트 코드는 구상 전략을 선택하고 컨텍스트에 전달합니다.&#x20;



## 구현방법&#x20;

1. 자주 변경되는 알고리즘을 식별합니다.&#x20;
2. 모든 알고리즘에 공통인 전략 인터페이스를 선언합니다.&#x20;
3. 모든 알고리즘을 각기 다른 클래스로 추출합니다. (전략 인터페이스를 구현합니다.)&#x20;
4. 컨텍스트 클래스에서 전략에 대한 참조를 저장하기 위한 필드를 추가합니다.&#x20;
   1. 해당 필드의 값을 대체하기 위한 세터를 제공합니다.&#x20;
   2. 컨텍스트는 전략 인터페이스를 통해서만 전략 객체와 통신해야합니다.&#x20;
   3. 컨텍스트는 인터페이스를 정의할 수 있으며, 이 인터페이스는 전략이 컨텍스트의 데이터에 접근할 수 있도록 합니다.&#x20;
   4. 컨텍스트의 클라이언트들은 컨텍스트를 적절한 전략과 연관시켜야합니다.&#x20;



## 적용하기&#x20;

1.  **객체 내에서 한 알고리즘의 다양한 변형들을 사용하고 싶을 때 사용합니다.**&#x20;


2.  **런타임 중에서 알고리즘 전환이 필요한 경우 사용합니다.**&#x20;

    : 특정 하위 행동들을 다양한 방식으로 수행할 수 있는 다른 하위 객체들과 연관시켜 객체의 행동들을 런타임에 간접적으로 변경할 수 있습니다.&#x20;
3.  **구현 방식만 차이가 있는 비슷한 클래스들이 많은 경우 사용합니다.**&#x20;

    : 전략 패턴은 다양한 행동들을 별도의 클래스 계층 구조로 추출하고 원래 클래스들을 하나로 결합합니다.&#x20;
4.  **비즈니스 로직 내에서 중요하지 않은 알고리즘의 구현 세부사항들로부터 고립합니다.**&#x20;

    : 전략 패턴으로 코드, 데이터, 알고리즘의 의존관계를 고립시킬 수 있습니다.
5.  **매우 큰 조건문이 있을 경우 사용하기 좋습니다.**&#x20;

    : 알고리즘을 같은 인터페이스를 구현하는 별도의 클래스로 추출하여 조건문을 제거할 수 있습니다.&#x20;



## 장단점&#x20;

### 장점&#x20;

* 런타임 시점에 알고리즘을 선택할 수 있습니다.&#x20;
* 알고리즘을 사용하는 코드는 알고리즘 구현체를 몰라도 됩니다.&#x20;
* 상속을 합성으로 대체할 수 있습니다.&#x20;
* 개방 폐쇄 원칙 컨텍스트를 변경하지 않고 새로운 전략을 도입할 수 있습니다.&#x20;

### 단점&#x20;

* 알고리즘이 몇 개 밖에 되지 않고 거의 변하지 않는다면, 패턴과 함께 사용되는 새로운 클래스들과 인터페이스로 굳이 복잡하게 만들 필요는 없습니다.&#x20;
*   익명함수가 존재합니다.&#x20;

    : 클래스와 인터페이스를 추가할 필요 없이, 전략 객체와 동일한 이점을 누릴 수 있습니다.&#x20;



## 다른 패턴과의 관계

### 브리지와 상태, 어댑터&#x20;

* 위의 모든 패턴은 다른 객체에 작업을 위임하는 합성을 기반으로 합니다.&#x20;

### 커맨드

* 둘 다 어떤 작업으로 객체를 매개변수화합니다.&#x20;

#### 커맨드&#x20;

* 모든 작업을 객체로 변환할 수 있습니다.&#x20;
* 작업의 매개변수들은 해당 객체의 필드가 됩니다.&#x20;

#### 전략&#x20;

* 일반적으로 같은 작업을 수행하는 다양한 방법을 설명하므로 단일 컨텍스트 클래스 내에서 알고리즘을 교환할 수 있도록 합니다.&#x20;





### 템플릿

#### 템플릿은 상속이 기반입니다.&#x20;

* 자식 클래스들에서 알고리즘의 부분을 확장해 변경할 수 있습니다.&#x20;
* 클래스 수준에서 작동하므로 정적입니다.

#### 전략패턴은 합성이 기반입니다.&#x20;

* 객체 행동의 일부분들을 다양한 전략을 제공하여 변경할 수 있습니다.&#x20;
* 객체 수준에서 작동하므로 런타임시 변경가능(=동적)합니다.



### 상태

* 상태는 전략의 확장입니다.&#x20;
* 두 패턴 모두 합성을 기반으로 합니다.&#x20;
* 전략 패턴은 객체를 완전히 독립적으로 만듭니다.&#x20;
*   상태는 구상 상태들 사이의 의존 관계를 제한하지 않습니다.

    : 구상 상태들이 콘텍스트의 상태를 변경할 수 있습니다.&#x20;





## Ref.

{% embed url="https://refactoring.guru/ko/design-patterns/strategy/java/example" %}

