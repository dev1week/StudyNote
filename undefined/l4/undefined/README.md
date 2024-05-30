# 포트 : 응용계층과 연결하기

## 개요&#x20;

> 패킷이 실행중인 특정 애플리케이션까지 전달되려면 패킷에 특정 애플리케이션을 식별할 수 있는 정보가 있어야합니다.&#x20;



## 분류&#x20;

> 포트 번호를 통해 특정 애플리케이션을 식별합니다.&#x20;

### 종류&#x20;

> 범위에 따라 크게 3가지 종류로 나뉩니다.&#x20;

| 포트 종류    | 포트 번호 범위     |
| -------- | ------------ |
| 잘 알려진 포트 | 0\~1023      |
| 등록된 포트   | 1024\~49151  |
| 동적 포트    | 49152\~65535 |

서버로서 동작하는 프로그램은 일반적으로 잘 알려진 포트와 등록된 포트로 동작하는 경우가 많습니다. 반면에 클라이언트로서 동작하는 프로그램은 동적 포트 번호 중에서 임의의 번호가 할당되는 경우가 많습니다.&#x20;

<figure><img src="../../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>


