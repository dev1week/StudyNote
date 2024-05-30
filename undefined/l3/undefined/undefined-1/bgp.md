# BGP

## 개요&#x20;

> 대표적인 EGP로, AS 간의 통신이  가능한 대표적인 프로토콜입니다.&#x20;

* AS 간의 통신을 위한 BGP는 eBGP라고 합니다.&#x20;
* AS 내의 통신을 위한 BGP는 iBGP입니다.&#x20;



## 원리&#x20;

AS 간에 정보를 주고 받기 위해서는 다음 두가지  조건을 만족해야합니다. &#x20;

1. AS 내에서 eBGP를 사용하는 라우터가  하나 이상 있어야합니다.&#x20;
2. 다른 AS의 BGP 라우터와 연결되어야합니다.&#x20;



### 피어링과 피어&#x20;

<figure><img src="../../../../.gitbook/assets/image (2) (1).png" alt=""><figcaption></figcaption></figure>

#### 피어

> BGP 메시지를 주고 받을 수 있도록 연결된 BGP 라우터입니다.&#x20;

#### 피어링&#x20;

> AS와 BGP 연결을 유지하기 위해 BGP 라우터끼리 연결되는 과정을 의미합니다.&#x20;



### BGP의 속성과 정책&#x20;

> 경로 결정 과정에서 수신지 주소와 더불어 다양한 속성과 정책을 고려합니다.&#x20;

#### AS-PATH 속성&#x20;

> 메시지가 수신지에 이르는 과정에서 통과하는 AS들의 목록을 의미합니다.&#x20;

* 메시지가 AS를 거칠 때마다 AS-PATH에는 거쳐간 AS를 추가합니다.&#x20;

이 속성을 통해 엿볼 수 있는 eBGP의 특징이 크게 두 가지 있습니다.&#x20;

1.  BGP는 AS 간 라우팅을 할 때 거치게 될 라우터가 아닌 AS의 수를 고려합니다.&#x20;

    \->AS-PATH 길이가 더 짧은 경로라 할지라도 거치게 될 라우터 홉 수가 더 많아질 수 있습니다.&#x20;
2.  BGP는 RIP처럼 거리가 아닌 경로를 고려합니다.&#x20;

    \-> 메시지가 어디를 거쳐 어디로 가는지 경로를 고려하기  때문에 벡터 라우팅 프로토콜입니다.

#### NEXT-HOP

> 다음으로 거칠 홉(=라우터)의 IP 주소를 나타냅니다.&#x20;



#### LOCAL-PREF

> 지역 선호도의 약자로 AS 외부 경로에 있어 AS 내부에서 어떤 경로를 선호할지에 대한 척도를 나타냅니다.&#x20;

* 해당 속성의 값이 클수록 우선으로 선택됩니다.&#x20;
* 경로를 선택하는 과정에서 LOCAL\_PREF 값은 일반적으로 다른 속성들보다 우선시 됩니다.&#x20;
* AS 관리 주체가 설정하는 정책의 영향을 받습니다.&#x20;