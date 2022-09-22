# 자료구조별 특징

<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FefLNM6%2FbtrgVOqM1ww%2Fq9Y1KFRs7y81CHkXtK1vy1%2Fimg.jpg">

<br />

## List

  - List는 저장공간이 필요에 의해 자동으로 늘어난다. (순서O)

  - 특징
    
    순서가 있고, 중복을 허용한다.

  - 장점

    가변적으로 공간이 자동으로 늘어남.

  - 단점

    원하는 데이터가 뒤쪽에 위치하는 경우 속도의 문제

  - 방식

    equals()를 이용한 데이터 검색

  - 종류

    - ArrayList 
    
       - 객체 내부에 있는 배열에 데이터를 저장한다.

       - 상당히 빠르고 크기를 맘대로 조절할 수 있는 배열

       - 단방향 포인터 구조로 자료에 대한 순차적인 접근에 강점을 둔다.

     - Vector

        - ArrayList와 동일학데 사용이 가능하다.

        - ArrayList의 구형 버전이며, 모든 메소드가 동기화 되어 있지만, 잘 사용되지 않는다.

        - ArrayList와 차이점은 한 데이터에 동시접속이 발생했을 때, 처리가 가능한 기능이 있나 없나의 차이점이 있다. 

        - 동시 접속을 고려하여 만들어진 리스트가 Vector이다.

        - ArrayList는 동시 접속을 고려하지 않고 가볍다는 장점이 있다.

     - LinkedList

        - 양방향 포인터 구조로 데이터의 삽입, 삭제가 빈번할 경우 빠른 성능을 보장한다.

        - 스택, 큐, 양방향 큐 등을 만들기 위한 용도로 사용된다.

        - Iterator를 사용하다.

            ```
            Iterator 추출 전용 인터페이스
            
            - 데이터를 추출하기 위한 데이터 임시 저장공간
            - 주로 순서가 없는 자료구조의 값들을 추출할 때 사용
            - 보통 hasNext와 next메소드를 이용한 while문으로 값을 추출한다.

            사용하는 이유는 linked 특성상 항상 처음부터 같은 경로를 반복적으로 지나면서 데이터의 위치를 검색해야하기 때문에 마지막으로 접근한 데이터를 기준으로 다음 데이터를 알아내는 것이 더 쉽다는 장점이 있다.
            ```

<br />
<hr />
<br />

## Set 

  - Set

    - 집합, 순서가 없다. 집합이므로 중복된 데이터가 들어갈 수 없다.

    - 중복되지 않는 데이터를 구할 때 사용하면 유용한다.

    - 특징

        - 순서가 없고, 중복을 허용하지 않는다.
            
    - 장점

        - 빠른 속도

     - 단점

        - 단순 집합의 개념으로 정렬하려면 별도의 처리가 필요하다.

     - 종류

        - HashSet

            순서를 보장하지 않는 set

         - TreeSet

            Binary Search Tree 구조
            
            추가와 삭제에는 시간이 좀 더 걸리지만, 정렬 및 탐색에 성능이 좋음
            
            오름차순을 데이터를 저장

         - LinkedHashSet

            데이터가 들어간 순서대로 저장하는 Set

    <br />
    
```
 ▶ hashSet의 key값은 hashcode 비교에 의해 중복여부가 확인된다. hashCode()를 가지고 비교하고 ==로 비교해서 true를 리턴하거나 equals()로 비교해서 true를 리턴하는지 체크하고 element를 덮어 쓸 것인지 결정하면 된다.

 Hashset은 Iterator를 사용한다
왜냐하면, set은 순서가 없기 때문에 데이터에 순서를 정해 추출해야한다.
``` 

<br />
<hr />
<br />

## Map : 키와 데이터를 같이 저장

 - 특징 
    
    - Map이란 Key와 Value로 이뤄진 데이터의 집합
    
    - Key의 중복은 허용되지 않고, Value의 중복은 가능하다.

 - 장점 
    
     - 빠른 속도

 - 단점
    
     - Key의 검색 속도가 검색 속도를 좌우
 
  - 종류
  
    - HashMap 
    
        - index번호 대신 키값으로 값을 찾는 맵형태의 자료구조도 iterator 클래스를 이용해서 키값을 순서대로 iterator에 저장해두면 순서대로 데이터 추출이 가능하다.
        
        - 순서를 보장하지 않는 map, Key와 Value로 null이 허용된다.


    - HashMap

        - 순서를 보장하지 않는 map, Key와 Value로 null이 허용된다.


    - HashTable

        - 동기화를 지원하는 map, Key와 Value로 null이 허용되지 않는다.


    - TreeMap

       - 이진 검색 Tree 구조의 Map, 저장시 Key기준으로 오름차순 저장된다.


    - LinkedHashMap

        - 들어간 순서대로 저장되는 Map
