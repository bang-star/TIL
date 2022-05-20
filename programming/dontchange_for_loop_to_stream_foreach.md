# for-loop to Stream.forEach()로 바꾸지 말아야 할 3가지 이유

## 1. 성능
    
 1. [Java performance tutorial – How fast are the Java 8 streams](https://jaxenter.com/java-performance-tutorial-how-fast-are-the-java-8-streams-118830.html)을 통해 자세한 성능을 확인 할 수 있다.
 2. 성능에 치명적인 영향을 미치는 코드는 많지 않으며, 그래서 성급한 최적화는 해서는 안된다.
 3. Stream.forEach()를 사용하면 전통적인 for-loop를 사용할 때보다 오버헤드가 훨씬 심각하게 발생하기 때문에, 모든 for-loop를 stream.forEach()로 대체하면 애플리케이션 전체에 걸쳐 누적되는 CPU 싸이클 낭비는 무시하지 못할 수준이 될 수 있다.
 4. 단순히 반복문 처리 스타일의 선택만으로 CPU소모량이 10%~20%정도 더 많아진다면, 그 선택은 근본적으로 잘못된 것이다. 반복문 각각을 놓고 보면 큰차이가 없지만, 시스템 전체로 보면 피하는 것이 좋다.
 5. 성급한 최적화라도 무조건 회피하는 것은 훨씬 더 좋지 않다. 어떤 상황(context)인지 잘 숙고해서 바른 결정을 내리는 것이 중요하다. 

 > 성능에 대해서는 [Top 10 Easy Performance Optimisazions in Java](https://blog.jooq.org/top-10-easy-performance-optimisations-in-java/) 를 참고하자.

<br />
<hr>
<br />

## 2. 가독성

- SW 엔지니어인 우리는 코드 스타일을 아주 중요한 것으로 여기며, 때로 이런 주제로 토론을 하기도 한다. 왜냐하면 SW는 유지관리하기가 어렵기 때문이다. 특히나 다른 사람이 작성한 코드는 더욱 그렇다. 그 다른 사람이 Java로 전향하기 전에 오로지 C로만 코딩해온 사람이라면.. 더욱 힘들 것이기 때문이다.

- 좋고 나쁜 코드가 아닌 협업을 위한 것이므로 습관을 고치면 좋다. range와 forEach(), 람다(lamda)를 중첩시키는 건 그다지 익숙한 풍경이라고 할 순 없겠고, 팀내에서도 인지적 마찰(cognitie friction)이 빚어질 가능성이 높다.

<br />
<hr>
<br />

# 3. 디버깅
 - 성능 - 떨어진다 에서 얘기한 것처럼 modern 방식에 성능 이슈가 존재하는 이유가 여기에서 직접적으로 드러난다. 내부 반복(Internal iteration)을 사용하면 겉으로는 드러나지 않지만, 내부적으로 JVM과 라이브러리가 할 일이 많아진다. 
 - 유지관리 관점에서보자면, 함수형 프로그래밍 스타일은 절차형 프로그래밍에 비해 훨씬 어렵다. 특히 레거시 코드에서 이 두 스타일을 분별없이 혼용하고 있다면 더욱 어렵다.

<br />
<hr>
<br />

## 참고
[3 Reasons why You Shouldn’t Replace Your for-loops by Stream.forEach()](https://blog.jooq.org/3-reasons-why-you-shouldnt-replace-your-for-loops-by-stream-foreach/)