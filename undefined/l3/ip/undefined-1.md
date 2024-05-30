# 예약주소



## 루프백 주소&#x20;

> 자기 자신을 가리키는 특별한 주소입니다.&#x20;

* 가장 일반적으로 사용되는 주소는 127.0.0.1 이고 로컬 호스트라 부릅니다.&#x20;
* 루프백 주소로 전송된 패킷은 자기 자신에게 되돌아오므로 자기 자신을 마치 다른 호스트인 양 간주하여 패킷을 전송합니다.&#x20;
* 테스트나 디버깅 용도로 사용됩니다.&#x20;



## 0.0.0.0/8&#x20;

> 이 네트워크의 호스트입니다.&#x20;

*   DHCP Discover 메시지를 전송하는 시점에 클라이언트는 IP 주소를 할당되지 않아, 송신지 IP는 0.0.0.0으로 설정됩니다.&#x20;

    \-> 호스트가 IP 주소를 할당받기 전에 임시로 사용합니다.&#x20;

    \-> 호스트 입장에서는 지칭할 IP 주소가 없기 때문에 이 네트워크의 호스트로 자신을 지칭합니다.&#x20;



## 디폴트 라우트&#x20;

> 0.0.0.0/0으로, 모든 임의의 IP 주소를 의미합니다.&#x20;

* 패킷이 이동할 경로를 결정하는 라우팅에서 활용되는데, 디폴트 라우트를 나타내기 위해서 사용합니다.&#x20;
*   디폴트 라우트는 패킷을 어떤 IP 주소로 전달할지 결정하기 어려울 경우 기본적으로 패킷을 전달할 경로를 의미합니다.&#x20;

    \-> 어디로 패킷을 전달해야할지 명확하지 않을 경우 이곳으로 패킷을 이동시킵니다.&#x20;
