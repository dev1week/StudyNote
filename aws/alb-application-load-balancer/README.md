---
description: 7계층에서 동작하는 로드밸런서 입니다. 트래픽을 균형있게 나누어줍니다.
---

# ALB - Application Load Balancer



## 개요&#x20;

> 트래픽을 여러 대상에 자동으로 분산시켜 안정적인 운용을 할 수 있습니다.&#x20;

* EC2뿐만 아니라 컨테이너(ECS), 서버리스(Lambda) 등으로 다양한 서비스와 연계하여 부하를 분배할 수 있습니다.&#x20;
* 서로 다른 EC2에 대한 하나의 엔드포인트를 제공합니다.&#x20;
* 부하 분산 대상에 대한 헬스 체크, 고정 세션, ssl Offload, 다운서버 제외 기능을 제공합니다.&#x20;







## 구성&#x20;

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption><p><a href="https://docs.aws.amazon.com/ko_kr/elasticloadbalancing/latest/application/introduction.html">https://docs.aws.amazon.com/ko_kr/elasticloadbalancing/latest/application/introduction.html</a></p></figcaption></figure>

* 위 사진과 같이 Load Balancer, Listener, Target Group으로 나누어져 있습니다.&#x20;
* 기본적으로 VPC에 탑재되며 사용자 요청을 받고, 이를 VPC 내의 리소스에 적절히 부하분산합니다.&#x20;
* 외부의 요청을 받아들이는 리스너, 요청을 분산 전달할 수 있는 리소스의 집합인 대상그룹으로 구성됩니다.&#x20;
* ELB는 다수의 리스너와 대상 그룹을 거느릴 수 있습니다.&#x20;

{% content-ref url="undefined.md" %}
[undefined.md](undefined.md)
{% endcontent-ref %}



## 기능&#x20;

1. 앱의 트래픽을 여러 가용영역으로 분산합니다.&#x20;
2. 리스너를 이용해 RL, 호스트, 헤더, 메소드를 기반으로 규칙을 구성하여 요청을 처리할 수 있습니다.&#x20;
3. 트래픽 부하에 따라 자동으로 스케일 업, 다운을 수행할 수 있습니다.&#x20;
4. 하나 이상 타겟 그룹에 라우팅할 수 있으며 각 그룹별 가중치 설정이 가능합니다.&#x20;
5. SSL Offloading을 지원합니다.&#x20;
6. 디폴트 알고리즘은 라운드 로빈이며, 최소 미해결 요청 라우팅 알고리즘을 지원합니다.&#x20;
7. 교차 영역 로드 밸런싱을 통해 AZ의 모든 타겟 그룹에 트래픽을 분산합니다.&#x20;



## 오토 스케일링과 조합&#x20;

### 오토 스케일링&#x20;

> 오토 스케일링은 트래픽이 몰릴 때 인스턴스 수를 늘림으로 서버사이즈를 조절합니다. \
> 트래픽이 적을 때는 인스턴스를 감소시켜 비용낭비를 막습니다.&#x20;





