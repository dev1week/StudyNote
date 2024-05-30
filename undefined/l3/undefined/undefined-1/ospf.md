# OSPF

## 개요

> 링크 상태 라우팅 프로토콜입니다. \
> OSPF는 링크 정보를 비롯한 현재 네트워크 상태를 그래프의 형태로 LSDB에 저장합니다. 라우터는 LDSB를 기반으로 현재 네트워크 구성을 지도처럼 그린 뒤 최적경로를 선택합니다.&#x20;



## 작동 원리&#x20;

* 라우터 간 경로 정보를 주기적으로 교환하며 라우팅 테이블을 갱신하는 RIP와 달리, **OSPF는 네트워크 구성이 변경되었을 때 라우팅 테이블이 갱신**됩니다.&#x20;
* 최적 경로를 결정하기 위해 대역폭을 기반으로 메트릭을 계산합니다.&#x20;
  * 대역폭이 낮을 수록 메트릭이 낮은 경로입니다.&#x20;

### 문제점&#x20;

* 네트워크 구성이 변경될 때마다 라우팅 테이블이 갱신될 경우 네트워크 구조가 커졌을 때 LSDB에 모든 정보를 저장하기 어렵습니다.&#x20;
* 최적 경로를 계산하는 연산 부담이 커집니다.&#x20;

### 해결책 : 에어리어&#x20;

<figure><img src="../../../../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

* AS를 에어리어라는 단위로 나눠, 에어리어 내에서만 링크 상태를 공유합니다.&#x20;
* 에어리어에는 번호가 부여되어있습니다.&#x20;
* 에어리어 경계에 있는 ABR이라는 라우터가 에어리어간의 연결을 담당합니다.&#x20;



### LDSB

> 링크 상태 데이터베이스의 약자로, 그래프 형태로 네트워크 상태를 저장합니다.&#x20;

* 라우터들의 연결 관계, 연결 비용 등 현재 네트워크 상태를 그래프로 표현하기 위한 데이터가 저장되어 있습니다.&#x20;
