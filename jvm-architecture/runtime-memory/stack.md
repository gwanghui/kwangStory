# Stack

### The Java Stack

새로운 쓰레드가 실행되면 JVM은 새로운 쓰레드를 위한 독립적인 stack을 생성해 Java Stack에 저장합니. JVM은 Stack에 Push,Pop Frame 2가지 Operation밖에 사용하지 않습니다.

thread에 의해 실행되는 method를 current method라고 하며 이때 저장한 stack frame을 current stack frame, 이때 current method에 의해 호출된 class를 current class, current class에 정의된 Constant pool을 current constant pool이라고 합니다.

스레드가 Java 메소드를 호출하면 가상 시스템은 스레드의 Java 스택에 새 프레임을 작성하고 푸시합니다. 그런 다음이 새 프레임이 현재 프레임이됩니다. 메소드가 실행되면 프레임을 사용하여 매개 변수, 로컬 변수, 중간 계산 및 기타 데이터를 저장합니다.

메소드는 두 가지 방법 중 하나로 완료 할 수 있습니다. 메서드가 반환하여 완료되면 정상 완료 라고합니다 . 예외를 throw하여 완료하면 갑작스럽게 완료 되었다고합니다 . 메소드가 정상적으로 종료했는지 갑자기 실패했을 경우, Java 가상 머신은 메소드의 스택 프레임을 팝 해 버립니다. 그러면 이전 메서드의 프레임이 현재 프레임이됩니다.  
  
스레드의 Java 스택에있는 모든 데이터는 해당 스레드에 대해 비공개입니다. 스레드가 다른 스레드의 Java 스택에 액세스하거나 변경할 수있는 방법은 없습니다. 따라서 Java 프로그램의 로컬 변수에 대한 다중 스레드 액세스를 동기화 할 필요가 없습니다. 스레드가 메소드를 호출하면 메소드의 로컬 변수는 호출하는 스레드의 Java 스택에있는 프레임에 저장됩니다. 단 하나의 스레드 만이 메소드를 호출 한 스레드 인 로컬 변수에 액세스 할 수 있습니다.

메소드 영역 및 힙과 마찬가지로 Java 스택 및 스택 프레임도 메모리에서 연속적 일 필요는 없습니다. 프레임은 인접한 스택에 할당되거나 힙이나 둘 중 일부 조합에 할당 될 수 있습니다. Java 스택 및 스택 프레임을 표현하는 데 사용되는 실제 데이터 구조는 구현 설계자의 결정입니다. 구현을 통해 사용자 또는 프로그래머는 최대 또는 최소 크기뿐만 아니라 Java 스택의 초기 크기를 지정할 수 있습니다.

### The Stack Frame

스택 프레임은 로컬 변수, 피연산자 스택 및 프레임 데이터의 세 부분으로 구성됩니다. 로컬 변수와 피연산자 스택의 크기는 단어 단위로 측정되며 각각의 개별 메소드의 필요성에 따라 달라집니다. 이러한 크기는 컴파일시 결정되며 각 메서드의 클래스 파일 데이터에 포함됩니다. 프레임 데이터의 크기는 구현에 따라 다릅니다.  
  
Java 가상 머신은 Java 메소드를 호출 할 때 클래스 데이터를 점검하여 로컬 변수와 피연산자 스택에서 메소드가 필요로하는 단어의 수를 판별합니다. 메서드에 적합한 크기의 스택 프레임을 생성하고 이를 Java 스택에 푸시합니다.

### Local Variables 

로컬 변수에서 long 또는 double을 참조하기 위해 명령어는 두 개의 연속 된 항목 중 첫 번째 항목이 차지하는 인덱스를 값으로 제공합니다. 예를 들어, long배열 항목 3과 4를 차지하는 경우 명령은 long인덱스 3을 참조합니다 . 로컬 변수의 모든 값은 워드로 정렬됩니다. 이중에서 항목 long 및 double는 모든 색인에서 시작할 수 있습니다.  
  
로컬 변수 섹션에는 메서드의 매개 변수와 로컬 변수가 들어 있습니다. 컴파일러는 매개 변수를 선언 된 순서대로 먼저 로컬 변수 배열에 배치합니다. 그림 stack-1은  다음 두 가지 방법에 대한 로컬 변수 섹션을 보여줍니다.

```java
class Example3a { 
    public static int runClassMethod(int i, long l, float f, double d, Object o, byte b) { 
        return 0; 
    } 
    public int runInstanceMethod(char c, double d, short s, boolean b) { 
        return 0; 
    } 
}
```

![stack-1\) Method parameters on the local variables section of Java stack](../../.gitbook/assets/fig5-9.gif)



