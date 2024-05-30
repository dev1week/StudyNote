# 포트 기반 NAT

## 사전지식&#x20;

#### NAT&#x20;

> IP를 변환하는 기술입니다.\
> 주로 외부에서 사용할 공인 IP와 내부에서 사용할 사설 IP간 주소를 변환합니다.

{% content-ref url="../../l3/ip/ip-ip/nat-ip-less-than-greater-than-ip.md" %}
[nat-ip-less-than-greater-than-ip.md](../../l3/ip/ip-ip/nat-ip-less-than-greater-than-ip.md)
{% endcontent-ref %}



## NAT 변환 테이블&#x20;

변환 테이블에는 변환의 대상이 되는 IP 주소쌍이 명시되어 있습니다.&#x20;

<figure><img src="../../../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>

### 동작과정&#x20;

<figure><img src="../../../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

그림에서 사설 IP와 공인 IP를 일대일로 대응합니다. 공인 IP는 고유한 주소인데 여러개의 사설 IP 주소가 하나의 공인 IP로 변환될 수 있을까요? 바로 포트를 사용하기 때문입니다.&#x20;







## NAPT&#x20;

> 포트 기반의 NAT 입니다. APT라고 부르기도합니다.&#x20;



* 하나의 공인 IP를 여러 사설 IP가 공유할 수 있게끔 합니다.
*   NAT 테이블에 변환할 IP 주소쌍과 더불어 포트 번호도 함께 기록하고 변환합니다.&#x20;

    <figure><img src="../../../.gitbook/assets/image (13).png" alt=""><figcaption><p>IP가 같더라도 포트 번호가 다르면 내부의 호스트를 특정할 수 있습니다.</p></figcaption></figure>

### 동작원리&#x20;

<figure><img src="../../../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>



