# Garbage Collection

## 1. Garbage Collection, GC

<br />

![image](https://user-images.githubusercontent.com/63120360/169747653-56f05f4a-3ce5-4cad-9c31-25e466f01e30.png)

<br />

  1. Minor GC
  - 새로 생성된 대부분의 객체는 Eden 영역에 위치한다.
  - Eden 영역에서 GC가 한 번 발생한 후 살아남은 객체는 Survivor 영역 중 하나로 이동된다.
  - 이 과정을 반복하다가 계속해서 살아남아 있는 갳게는 일정시간 참조되고 있다는 뜻이므로 Old영역으로 이동시킨다.

  2. Major GC
  - Old 영역에 있는 모든 객체들을 검사하여 참조되지 않은 객체들을 한꺼번에 삭제한다.
  - 시간이 오래 걸리고 실행 중 프로세스가 정지된다. 이것을 "stop-the-world"라고 하는데 Major GC가 발생하면 GC를 실행하는 스레드를 제외한 나머지 스레드는 모두 작업을 멈춘다. 
  - GC 작업을 완료한 이후에야 중단했던 작업을 다시 시작한다.

  ```
    "가비지 컬렉션은 어떤 원리로 소멸시킬 대상을 선정하는가?"
  ```

  - 알고리즘에 따라 동작 방식이 매우 다양하지만 공통적인 원리가 있다.
  - Garbage Collector는 힙 내의 객체 중에서 Garbage를 찾아내고 찾아낸 Garbage를 처리해서 힙의 메모리를 회수한다.
  - 참조되고 있지 않은 객체를 Garbage라고 하며 객체가 Garbage가 아닌지 판단하기 위해서 reachability로 판단한다.
  - 하나의 객체는 다른 객체를 참조하고, 다른 객체는 또 다른 객체를 참조할 수 있기 때문에 참조 사슬이 형성이 되는데, 이 참조 사슬 중 최초에 참조한것을 Root Set이라고 칭한다.

<br />

![image](https://user-images.githubusercontent.com/63120360/169747681-ca83e983-b200-4969-bf84-7de96c79258b.png)

<br />

  * 1 : 힙 내의 다른 객체 의한 참조
  * 2 : Java 스택, 즉 Java 메서드 실행 시에 사용하는 지역변수와 파라미터들에 의한 참조
  * 3 : 네이티브 스택(JNI, Java Native Interface)에 의해 생성된 객체에 대한 참조
  * 4 : 메서드 영역의 정적 변수에 의한 참조
  * 2,3,4 는 Root Set이다. 즉, 참조 사슬 중 최초에 참조한 것이다.

  * 인스턴스가 Garbage 컬렉션의 대상이 되었다고 해서 바로 소멸이 되는 것은 아니다. 빈번한 Garbage 컬렉션의 실행은 시스템에 부담이 될 수 있기에 성능에 영향을 미치지 않도록 Garbage 실행 타이밍은 별도의 알고리즘을 기반으로 계산이 되며, 이 계산 결과를 기반으로 Garbage 컬렉션이 수행된다.

  1. Serial GC
  - 적은 메모리와 CPU 코어 개수가 적을 때 적합한 방식으로  Young 에서

  2. Parallel GC
  - 기본적인 GC 알고리즘 Serial GC와 동일하지만 Parallel GC는 GC를 처리하는 스레드가 여러 개라서 보다 빠른 GC를 수행할 수 있다.
  - 메모리가 충분하고 코어의 개수가 많을 때 유리하다.


<br />
<hr />
<br />

## 참조
1. [Garbage Collection](https://asfirstalways.tistory.com/159?category=660807)
