# Thread Local

![](../.gitbook/assets/threadlocal.jpg)

* Java Web Application Server는 기본적으로 ThreadPool을 사용하고 있고 이때, ThreadLocal에 있는 데이터를 올바르게 반환하지 않을 경우 다른 Thread가 해당 데이터를 참조 할 수 있으므로 초기화에 유의 해야 한다.

