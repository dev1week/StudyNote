# 람다



## 개요&#x20;

> 메서드를 하나의 식으로 표현합니다.&#x20;



### 예시&#x20;

#### 메서드

```java
int min(int x, int y){
    return x<y?x:y; 

}
```

#### 람다 표현식&#x20;

```java
(x,y) -> x<y?x:y; 
```



메서드를 람다식으로 표현하면, 클래스를 작성하고 객체를 생성하지 않아도 메서드를 사용할 수 있습니다.&#x20;



## 익명 클래스 :자바에서 람다 사용하기

자바에서는 클래스의 선언과 동시에 객체를 생성합니다.&#x20;

객체에서 생성없이 메서드를 사용하기 위해서는 익명 클래스를 사용해야합니다.&#x20;

#### 람다 표현식

```
(x,y) -> x<y?x:y; 
```

#### 익명 클래스&#x20;

```java
new Object() {

    int min(int x, int y) {

        return x < y ? x : y;

    }

}
```





## 람다의 장점&#x20;

1.  **간결한 코드**: 람다 표현식을 사용하면 코드를 간결하게 작성할 수 있습니다. 익명 클래스(anonymous class)를 대체하여 불필요한 코드 작성을 줄여줍니다.

    ```java
    java코드 복사// Before Java 8
    new Thread(new Runnable() {
        @Override
        public void run() {
            System.out.println("Hello World!");
        }
    }).start();

    // With Lambda Expression
    new Thread(() -> System.out.println("Hello World!")).start();
    ```
2. **가독성 향상**: 코드가 간결해지면서 가독성이 향상됩니다. 람다 표현식은 의도를 명확하게 표현할 수 있어, 다른 사람이 코드를 읽고 이해하기 쉬워집니다.
3.  **함수형 프로그래밍 지원**: 자바에서 함수형 프로그래밍 패러다임을 사용할 수 있게 해줍니다. 람다 표현식과 함께 스트림 API를 사용하면 컬렉션 데이터를 처리하는 데 매우 유용합니다.

    ```java
    java코드 복사List<String> names = Arrays.asList("John", "Jane", "Jack");
    names.stream()
         .filter(name -> name.startsWith("J"))
         .forEach(System.out::println);
    ```
4.  **병렬 처리 용이**: 스트림 API와 결합하여 병렬 처리를 쉽게 할 수 있습니다. 이를 통해 멀티코어 프로세서를 효과적으로 활용할 수 있습니다.

    ```java
    java코드 복사List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);
    int sum = numbers.parallelStream()
                     .filter(n -> n % 2 == 0)
                     .mapToInt(Integer::intValue)
                     .sum();
    ```
5.  **콜백 함수의 간편한 구현**: 이벤트 처리나 비동기 작업에서 콜백 함수를 간편하게 구현할 수 있습니다.

    ```java
    java코드 복사JButton button = new JButton("Click me");
    button.addActionListener(event -> System.out.println("Button clicked!"));
    ```
6. **변수 범위와 익명 함수**: 람다 표현식은 익명 함수로 사용되기 때문에, 이를 통해 지역 변수 범위 내에서 사용하기 쉽습니다. 다만, final 또는 effectively final 변수만 람다에서 참조할 수 있습니다.









### 예시 1: Runnable&#x20;

> 별도의 스레드에 작업을 위임하는 코드입니다.&#x20;

1. 아래 코드 예시처럼 Runnable 인터페이스를 구현합니다.&#x20;

```java
class Worker implements Runnable {

    public void run() {
    
        for (int i = 0; i < 1000; i++)
        
        doWork();
    
    }

//중략 
}
```



2\. 구현된 내용을 Runnable의 run 메서드에 집어 넣습니다.&#x20;

```java
Worker w = new Worker();

new Thread(w).start();
```



### 예시 2: Comparator&#x20;

> 문자열을 기본 사전 순서 대신 길이순으로 정렬하는 예제입니다.&#x20;

1. Comparatoer 인터페이스를 구현합니다.&#x20;

```java
class LengthComparator implements Comparator<String> {

    public int compare(String first, String second) {
    
        return Integer.compare(first.length(), second.length());
    
    }

}
```

2. sort 메서드에 Compartor 객체를 전달합니다.

```java
Arrays.sort(strings, new LengthComparator());

```



## 예시의 공통점&#x20;

1. 코드 블록을 어딘가에 전달(스레드 풀,  sort 메서드) 다.
2. 코드가 얼마 후 호출된다.&#x20;

