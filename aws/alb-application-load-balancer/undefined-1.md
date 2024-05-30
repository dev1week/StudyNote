# 도메인 기반 접근(작성중)



## 개요&#x20;

> ELB는 IP 고정이 불가능합니다. 따라서 도메인 기반으로 사용해야합니다.

* &#x20;자동 확장, 축소에 따라 ELB 접근 IP가 변경됩니다.
* &#x20;ELB에 접근하는 경우 ELB를 생성할 때에 생성되는 도메인 이름을 사용해 접근하도록 구성해야합니다.&#x20;

{% hint style="info" %}
단, NLB는 Elastic IP로 고정할 수 있습니다.
{% endhint %}





## ELB의 요청 처리 과정&#x20;

<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

1. 사용자가 로드 밸런서에 접근하기 위해 Amazon의 DNS 서버에 로드밸런서 도메인 해석을 요청합니다.&#x20;
2. Amazon DNS 서버가 로드밸런서 노드 IP 리스트를 사용자에게 전달합니다.&#x20;
3. 사용자는 전달받은 IP 중 하나를 선택하여 로드밸런서에 접근합니다. (+port)&#x20;
4. 사용자는 로드밸런서의 리스너에 접근하게 되며 리스너는 이 요청을 받아들여 적절한 대상그룹으로 전달합니다.&#x20;
5. 리스너로부터 전달받은 요청을 서비스가 처리 후 사용자에게 반환합니다.&#x20;





[https://inpa.tistory.com/entry/AWS-%F0%9F%93%9A-ELB-Elastic-Load-Balancer-%EA%B0%9C%EB%85%90-%EC%9B%90%EB%A6%AC-%EA%B5%AC%EC%B6%95-%EC%84%B8%ED%8C%85-CLB-ALB-NLB-GLB#1.\_%EB%B6%80%ED%95%98\_%EB%B6%84%EC%82%B0\_%EC%B2%98%EB%A6%AC](https://inpa.tistory.com/entry/AWS-%F0%9F%93%9A-ELB-Elastic-Load-Balancer-%EA%B0%9C%EB%85%90-%EC%9B%90%EB%A6%AC-%EA%B5%AC%EC%B6%95-%EC%84%B8%ED%8C%85-CLB-ALB-NLB-GLB#1.\_%EB%B6%80%ED%95%98\_%EB%B6%84%EC%82%B0\_%EC%B2%98%EB%A6%AC)
