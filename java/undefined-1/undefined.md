# 람다 표현식 문법





다음과 같은 익명 구현 객체를 람다식을 이용해 획기적으로 코드를 줄일 수 있다.&#x20;

```java
Operate operate = new Operate() {
    public int operate(int a, int b) {
        return a + b;
    }
};

// 람다식으로 줄이기
Operate operate = (a, b) -> {
    return a + b;
};

// 더 짧게 줄이기 (리턴 코드만 있다면 생략이 가능)
Operate operate = (a, b) -> a + b;
```

### 익명 구현객체는 다음 문서를 참고하시길 바랍니다.&#x20;

{% content-ref url="../undefined/undefined.md" %}
[undefined.md](../undefined/undefined.md)
{% endcontent-ref %}



### 람다식 표현의 익명 구현 객체를 만들 때 제약&#x20;



