## Azure Virtual Machines

Azure에서 제공하는 클라우드 컴퓨팅 서비스이다.

### 가용성 옵션

#### 가용성 영역(Availability Zones)

<div align="center">
    <img src="https://user-images.githubusercontent.com/22683489/169691754-cd6f5a57-d277-421f-98e4-16f1002ba220.png"/>
</div>

하나의 지역 내에서 동일한 가상 머신을 물리적으로 분리된 공간에 배치할 것인지를 설정하는 것으로, 특정 가용성 영역에서 문제가 발생하면 다른 가용성 영역을 통해 장애 극복(Failover)을 수행한다.

#### 가용성 집합(Availability Sets)

<div align="center">
    <img src="https://user-images.githubusercontent.com/22683489/169691780-981e3558-dc1c-4ced-b0fc-c2c17d398cc1.png"/>
</div>

가상 머신의 논리적 그룹을 나눌 것인지 설정하는 것으로, 전원과 네트워크 스위치를 공유하는 단위인 장애 도메인(Fault Domain)과 동시에 재부팅할 수 있는 단위인 업데이트 도메인(Update Domain)으로 구성된다.