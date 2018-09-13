# Runtime Memory

Runtime Data Area는 JVM이 프로그램을 수행하기 위해 운영체제로부터 할당 받는 메모리 영역이다. 

Runtime Data Areas는 각각의 목적에 따라 5 개의 영역으로 나뉘게 된다.

* PC Register
* Stack
* Native Stack
* Heap
* Method Area

안드로이드 dalvik과 일반 자바의 가장 큰 차이는 register based 방식의 VM과 Stack Based 방식의 VM인 것이다.

![](../../.gitbook/assets/2018-09-13-8.57.04%20%281%29.png)

