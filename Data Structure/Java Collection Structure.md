# Java Collection 구조 정리

## 1. Collection Interface

  - Iterator 인터페이스를 상속한 Collection은 가장 기본이 되는 인터페이스로 add(), size(), iterator() 메소드를 가지고 있다.

  - Collection 인터페이스 List와 Set 인터페이스의 많은 공통된 부분을 Collection 인터페이스에서 정의하고, 두 인터페이스는 그것을 상속받는다.

    <img src="https://user-images.githubusercontent.com/22147400/191710001-79f50511-8c1b-4829-a2e3-9a513c8d7af9.png">

    <br />

### Collections 란?

  - Collection 인터페이스와 달리 Java 1.2이상부터 Collections라는 static클래스가 존재합니다.

  - Collections는 컬렉션 프레임워크에 속하는 클래스를 지원해주는 다양한 메소드가 존재합니다.

### Collections 클래스의 메소드

  ![image](https://user-images.githubusercontent.com/22147400/191710546-2d7f1154-ef01-46e8-b71f-283b5340537c.png)

  - List자료형중 Stack과 ArrayList를 사용한 Collection의 메소드

    ```Java
    public static void main(String[] args) {

		// List의 Class 중 ArrayList, Stack을 사용하여 코드
		ArrayList<Integer> list = new ArrayList<>();
		Stack<Integer> s = new Stack<>();

		//초기화
		for (int i = 0; i < 10; i++)
			list.add(i);

		for (int i = 0; i < 10; i++)
			s.push(i);
		
		// max() , min() 최대 최소 찾기
		System.out.println("s max() : " + Collections.max(s));
		System.out.println("list min() : " + Collections.min(list));
		
		//sort()
		Collections.sort(s); //오름차순
		Collections.reverse(s); //내림차순
		Collections.sort(s, Collections.reverseOrder()); // 내림차순 

		System.out.print("\n역순 출력 : ");
		for(int i : s)
			System.out.print(i+" ");
		System.out.println("\n");
		
		
		// 섞기(Shuffling) 랜덤하게 섞는다
		Collections.shuffle(s);
		System.out.print("랜덤 출력 : ");
		for(int i : s)
			System.out.print(i+" ");
		System.out.println("\n");

		// binarySearch() -> 해당값의 index를 반환 (실패시 -1 반환)
		// 오름차순 정렬이 되어있어야 사용가능하다.
		Collections.sort(s); //오름차순
		System.out.print("정방향 정렬 : ");
		for(int i : s)
			System.out.print(i+" ");
		System.out.println("\n\n이진탐색 5값의 위치: "+Collections.binarySearch(s, 5));
		
		// 두 리스트가 다른지 확인 disjoint
		// 두 리스트중 공통값이 있으면 False
		ArrayList<Integer> list2 = new ArrayList<>(Arrays.asList(99,88));
		System.out.println("\ndisjoint (완전히 다른가?) : "+ Collections.disjoint(list, list2));
		
		
	}
    ```

  - Collection이란 말대로 데이터의 그룹 집합체라는 의미를 가진다.

  - 자바에 Collection 자료구조는 크게 List , Set , Map 3가지로 나눌 수 있다.

    - Collection 인터페이스를 상속하는 자료구조는 List , Set

    - Map은 기본적으로 Key, Value 라는 다른 구조를 가지기 때문에, 독립적인 인터페이스가 구현

  - 자료구조별 대략적인 특징

    ![image](https://user-images.githubusercontent.com/22147400/191711332-6a657af7-6346-4cec-b6d8-aac8b39b6345.png)

    ![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F1ARMT%2Fbtq8AQQN3tN%2FfZWTby4rJSRpj27lWoyXp1%2Fimg.png)

<br />
<hr />
<br />

## 2. Collection 하위 인터페이스

### 1. List 인터페이스

  - 특징

    - 중복 : 중복 가능 , index가 순차적 Key로 유일성을 가짐
    
    - 순서 : 순서 보장 
    
    - 정렬 : 정렬 가능 , Collections.sort()를 통해 제공됨
    
    - 동기화 (Thread-Safe) : 동기화 불가능, 불안전함

  - 종류
    
    - ArrayList
        
        - 단방향 포인터 구조로 각 데이터에 대한 인덱스를 가지고 있어 조회 기능에 성능이 뛰어남
        
        - 배열과 달리 초기크기를 지정하지 않아도 되므로, 삽입과 삭제가 자유롭지만 느리다.

    - LinkedList
        
        - 양방향 포인터 구조로 데이터의 삽입, 삭제가 빈번할 경우 데이터의 위치정보만 수정 하면 되기에 유용
        
        - 스택, 큐, 양방향 큐 등을 만들기 위한 용도로 쓰임

        - 삽입 / 삭제시 빠름

        - 데이터 검색성능이 나쁘다.  처음부터 순차적으로 노드를 순화해야 되기 때문에 느림

    - Vector
        
        - 과거에 대용량 처리를 위해 사용했으며, 내부에서 자동으로 동기화처리가 일어나 비교적 성능이 좋지 않고 무거워 잘 쓰이지 않음


   - 주요 메소드

        ![image](https://user-images.githubusercontent.com/22147400/191712948-9753ed81-3b2f-4263-99d8-82353ed70b4b.png)

    - 시간 복잡도

        - ArrayList

            - add : O(1)

            - remove : O(n)

            - get : O(1)

            - Contains : O(n)

            - iterator.remove : O(n)

        - LinkedList

            - add : O(1)

            - remove : O(1)

            - get : O(n)

            - Contains : O(n)

            - iterator.remove : O(1)
<br />

### 2. Set 인터페이스

  - 특징
  
    - 중복 : 중복 불가능 , 유일성을 가짐
    
    - 순서 : 예측 불가능
    
    - 정렬 : 정렬 불가능 ->  TreeSet 클래스 가능
    
    - 동기화 (Thread-Safe) : 동기화 불가능, 불안전함

  - 종류
    
    - HashSet
        
        - 가장빠른 임의 접근 속도
        
        - 순서를 예측할 수 없음

        - HashMap과 Set 인터페이스를 상속하여 빠른 연산이 가능한 자료형

        - 정렬이 불가능함

    - LinkedHashSet

        - LinkedList로 연결된 HashSet이라 할 수 있고, 입력 순서를 보장

    - TreeSet

        - 삽입과 동시에 정렬되는 상태를 유지함.

        - HashSet 보다는 삽입이 느림

        - Tree와 Set을 상속한 연산이 느려도 다양한 정렬을 지원하는 자료형

        - 정렬 특화되어 있으므로, 최대값, 최솟값 반환 메소드와 통계메소드를 제공함

  - 주요 메소드
    
    ![image](https://user-images.githubusercontent.com/22147400/191713653-060c4c1e-588d-4347-9093-3837da851356.png)


<br />

### 3. Map 인터페이스

 - 특징
 
    - 키(Key), 값(Value)의 쌍으로 이루어진 자료구조,

    - 순서가 없고, 키(Key)는 유일성을 가지고, 값(Value)의 중복은 허용한다.

    - 중복 : 중복 불가 , index가 순차적 Key로 유일성을 가짐
    
    - 순서 : 보장 불가 
    
    - 정렬 : 정렬 불가 
    
    - 동기화 (Thread-Safe) : 동기화 불가능, 불안전함

    - 삽입 / 삭제 / 조회 연산이 광장히 빠르지만, 순서를 보장하지 않고, 정렬이 불가하다는 단점을 가지고 있다.

      - 이러한 단점을 보완하기 위해서 자바에서는 HashMap , LinkedHashMap, TreeMap 세 가지의 클래스를 지원한다.

 - 종류 
        
     - Hashtable
        
        - HashMap보다는 느리지만 동기화 지원
        
        - null불가

        - 과거에 사용하던 클래스로 현재는 더 이상 지원하지 않는 클래스이니, 사용을 지양

    - HashMap
    
        - 중복과 순서가 허용되지 않으며 null값이 올 수 있다.

        - 해시함수를 이용한 Map임
        
        - 삽입 / 삭제 / 조회 연산의 O(1)을 보장하는 아주 빠른 자료구조

        - 삽입 데이터의 순서를 보장하지 않음

        - 정렬이 불가함

        - 주요 메소드

          ![image](https://user-images.githubusercontent.com/22147400/191766968-f683bb31-44b8-4070-b14b-6a4e334ca07f.png)

          <br />

          ```Java
          import java.util.HashMap;
          import java.util.HashSet;
          import java.util.Map;

          public class HashMapExam {
            public static void main(String[] args) {
              // 객체생성
              HashMap<Integer,Integer> map = new HashMap<>();

              // put() 삽입연산으로 초기화
              for (int i = 0; i < 10; i++)
                map.put(i, i*i);
              
              // KeySet()
              HashSet<Integer> set = new HashSet<Integer>(map.keySet());
              System.out.print("keySet() : ");
              for(int i : set)
                System.out.print(i+" ");
              
              // get() 조회
              System.out.println("\n\n4의 value : " + map.get(4)+"\n");
              
              // remove() 삭제
              System.out.println("remove(4) : " + map.remove(4)+"\n");

              // getOrDefault - 가져올때 값이 없으면 Default값을 가져옴
              System.out.println("map.getOrDefault(4, 16) : " + map.getOrDefault(4, 16)+"\n");

              // containsKey
              System.out.println("containsKey(4) : " + map.containsKey(4)+"\n");
              
              // containsValue
              System.out.println("containsValue(16) : "+ map.containsValue(16)+"\n");
              
              // size() 크기
              System.out.println("size : " + map.size()+"\n");
              
              //replace() 변경 , put도 가능
              map.replace(5, 5);
              System.out.println("map.replace 수행후  get(5) : " + map.get(5)+"\n");
              
              // 응용 put은 변경에도 쓰임, getOrDefault는 초기화에 많이쓰임
              map.put(4, map.getOrDefault(4, 16));		// key 5에  4가 가지고 있는값을 얻어와 넣어주려하는데 4가 없으면 16이란 값을 넣어주는경우
              System.out.println("getOrDefault로 4 다시 생성 : " + map.get(4) +"\n");
              
              // Map의 단일객체 Entry 
              System.out.println("Map.Entry<>로 받는  entrySet() 메소드");
              for(Map.Entry<Integer,Integer> m : map.entrySet()) {
                map.put(m.getKey(), m.getKey()*m.getValue()); // 세제곱값으로 초기화		
                System.out.print(map.get(m.getKey())+" ");
              }
              System.out.println("\n");
              
              // clear 모두제거 
              map.clear();
              System.out.println("clear() 수행\n");
              
              // isEmpty() 비었는지 확인
              System.out.println("isEmpty? : " + map.isEmpty()+"\n");		
            }
          }
          ```

    - TreeMap
        
        - 정렬된 순서대로 키(Key)와 값(Value)을 저장하여 검색이 빠름

        - 삽입 / 삭제가 굉장히 느리지만, 삽입순서를 보장함
        
        - Map이지만 유일하게 정렬이 가능함.

        - 주요 메소드

          - Map.Entry 인터페이스는 Map 인터페이스의 내부 인터페이스로 맵에 저장되는 엔트리의 조작을 위한 메소드가 정의되어 있습니다. 

          - HashMap의 모든 메소드를 사용가능하므로 생략하고, TreeMap에서만 사용가능한 메소드이다.

            ![image](https://user-images.githubusercontent.com/22147400/191767318-bea28f85-8e40-4de4-a36d-c7b5a03b7e8b.png)

            ```Java
            import java.util.HashSet;
            import java.util.Map;
            import java.util.TreeMap;
            public class TreeMapExam {
              public static void main(String[] args) {
                // TreeMap 객체생성
                TreeMap<Integer,Integer> map = new TreeMap<>();

                // 삽입과 동시에 정렬되는 자료구조
                for (int i = 10; i > 0; i--)
                  map.put(i, i*i);					//100,91,64,...9,4,1
                // 출력
                System.out.println("삽입과 동시에 정렬됨 : ");
                for(int i : map.keySet())
                  System.out.print(map.get(i)+" ");		//1,4,9,...64,91,100
                
                // 역순 출력
                System.out.println("\n\n역순 출력 : ");
                for(int i : map.descendingKeySet())
                  System.out.print(map.get(i)+" ");		//100,91,64,...9,4,1
                
                
                System.out.println("\n\n최소값을 받아오는 다양한 메소드의  사용 : ");
                System.out.print(map.pollFirstEntry().getKey()+" ");
                System.out.print(map.firstEntry().getKey()+" ");
                Map.Entry<Integer,Integer> m = map.firstEntry();
                System.out.print(m.getValue()+" ");
                System.out.print(map.firstKey()+" ");
              }
            }
            ```
 
     - LinkedHashMap

        - 삽입 / 삭제가 Map보다 느림

        - 삽입 순서를 보장함

        - 정렬은 불가함

<br />
<hr />
<br />

## REFER 

  - [Collection 정리](https://bangu4.tistory.com/194)