# 람다



## 개요&#x20;

> 람다 표현식은 나중에 한 번 이상 실행할 수 있도록 전달하는 코드 블록입니다.&#x20;



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

