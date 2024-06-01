# 구성요소



## Listener&#x20;

> 프로토콜과 포트를 기반으로 요청을 받아 검사하고 이를 적절한 타겟으로 전달합니다.&#x20;

* 로드 밸런서는 최소 1개 이상의 리스너를 필요로합니다.&#x20;
* 최대 10개까지 설정할 수 있습니다.&#x20;
* SSL 인증서를 게시하여 SSL Offload를 실시할 수 있습니다.&#x20;



## 규칙&#x20;

> 리스너와 타겟 그룹 사이 트래픽 분배를 위한 라우팅 규칙에 해당됩니다.&#x20;

* 우선순위, 액션, 조건 등의 정보를 담고 있습니다.&#x20;
* 조건이 만족되었을 때 지정한 액션을 수행할 수 있습니다.
*   리스너의 규칙은 다음과 같이 IF와 THEN으로 이루어져있습니다.

    \-:> IF의 조건이 만족하면 THEN 작업을 수행합니다.&#x20;

<figure><img src="../../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>



### IF

<table><thead><tr><th width="200"> 규칙</th><th width="349">설명</th><th>예시</th></tr></thead><tbody><tr><td>host header</td><td>요청의 호스트 이름을 기반으로 라우팅</td><td>test.com</td></tr><tr><td>http header</td><td>요청의 HTTP 헤더 기반으로 라우팅</td><td>User-Agent: Chrome</td></tr><tr><td>http request method</td><td>요청의 HTTP 메소드 기반으로 라우팅</td><td>GET, PUT</td></tr><tr><td>path pattern</td><td>요청 URL의 경로 패턴을 기반으로 라우팅</td><td>/img/*</td></tr><tr><td>query string</td><td>쿼리 문자열의 키/값 페어 또는 값 기반으로 라우팅</td><td>?name=product</td></tr><tr><td>source IP</td><td>요청의 소스 IP 주소 기반으로 라우팅</td><td></td></tr></tbody></table>



### THEN&#x20;

|   |   |   |
| - | - | - |
|   |   |   |
|   |   |   |
|   |   |   |

## 대상 그룹&#x20;

> &#x20;리스너가 전달한 요청을 처리하기 위한 부하 분산 대상의 모임입니다.&#x20;

* 등록된 서비스가 요청을 처리할 수 있는지 체크하는 헬스체크 기능을 제공합니다.&#x20;
* 그룹 내 요청 처리가 가능한 인스턴스가 몇개인지 확인하는 모니터링 기능을 제공합니다.&#x20;
* 이 대상 그룹을 오토스케일링 그룹으로 만들 수 있습니다.&#x20;



### GUI를 통해 확인해보기&#x20;

<figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>



