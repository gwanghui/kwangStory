# Chapter 6. The Cassandra Architecture

## Data Centers and Racks

* 카산드라는 물리적으로 독립적인 공간에 시스템을 분산시킬수 있다.
* 카산드라는 2레벨로 그룹핑을 한다. \(Data Center, Rack\)
  * Rack : 물리적인 하나의 장비에 있고 서로 가까이에 존재하는 논리적 노드들의 집합
  * Data Center : Rack의 논리적 집합 \(아마도 같은 빌딩이고, 신뢰할수 있는 네트워크로 연결되어있는\)

![](../.gitbook/assets/6-1.PNG)

* 카산드라는 하나의 데이터 센터에 하나의 Rack이 있는 디폴트 설정으로 존재한다.

## Gossip And Failure Detection

* 탈 중앙화와 분할 내성을 지원함 \( decentralization and partition tolerance\)
* Gossip Protocol\(epidemic protocols\) 으로 같은 클러스터에 있는 서로 다른 노드들의 상태를 유지한다.
* Gossiper가 매초마다 수행된다.
* 




