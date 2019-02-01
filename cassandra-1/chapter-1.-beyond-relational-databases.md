# Chapter 1. Beyond Relational Databases

대용량 데이터 베이스 처리시 기존 RDBMS의 문제점

* Vertical Scaling시 물리적으로 메모리나 CPU를 증대시켜야 해 시간이 필요하다.
* 여러대의 박스에 설치할 경우 데이터 복제 및 정합성, Fail over 시나리오가 필요하다.
* DBMS 시스템에 로깅이나 저널링이 고려된 Configuration이 필요하다.
* XML 처리와 같은 자원이 많이 필요한 레벨에 대한 관리가 필요하다.
* 점점 더 커지는 시스템의 경우 분산 캐시의 정합성에 대한 고려가 필요하다.
* 우리가 실제 세상에서 살다 보면 이론과는 다른 요구사항을 받에 되고 어플리케이션에 무엇을 제공해야 하는지 느낀다.  우선순위가 높은 쿼리에 대한 이해를 하다 보면 업무 특성에 따라 비정규화 같은 중복이 필요하다.

[Codd’s 12 Rules for relational data ](https://ko.wikipedia.org/wiki/%EC%BB%A4%EB%93%9C%EC%9D%98_12_%EA%B7%9C%EC%B9%99)\(커드의 12 규칙\)





