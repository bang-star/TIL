# Comparable과 Comparator의 이해


## Comparable과 Comparator의 비교

<br />

  - Comparable과 Comparator는 모두 인터페이스이다.

    즉, Comparable 혹은 Comparator을 사용하고자 한다면 인터페이스 내에 선언된 메소드를 반드시 '구현'해야한다.

    - API 공식 문서
    
        - [Comparable](https://docs.oracle.com/javase/8/docs/api/java/lang/Comparable.html#method.summary)

            Comparable 인터페이스에는 compareTO(T o) 메소드가 하나 선언되어 있다.

        - [Comparator](https://docs.oracle.com/javase/8/docs/api/java/util/Comparator.html#method.summary)

            Comparator 인터페이스에는 메소드가 많지만, 실질적으로 구현해야 하는 것은 Compare(T o1, T o2) 하나이다.

        <br />

         > 정리하면 Comparable 인터페이스를 사용하려면 compareTo 메소드를 구현해야하고, Comparator 인터페이스를 사용하려면 compare 메소드를 구현해야 한다.


<br />
<hr />
<br />

## Comparable과 Comparator의 차이와 사용방법

<br />

### 1. Comparable과 Comparator의 차이

<br />

  - 두 인터페이스는 무엇을 하는가?

    - 보통 객체를 정렬을 하기 위해 사용한다고 알고 있을텐데, 이것은 용도에 불과하다.

        정답은 "객체를 비교할 수 있도록 만든다"는 것이다.

<br />

  - 왜 객체를 비교할 수 있도록 하는 것일까?

    - primitive 타입의 실수 변수(byte, int, double etc ...)의 경우 부등호를 갖고 쉽게 두 변수를 비교할 수 있었다.

        이와 같이 primitive type은 자바 자체에서 제공되기에 별다른 처리 없이 비교가 가능하다. 즉, 기본 자료형이기 때문에 부등호로 쉽게 비교 가능하다.

    - 새로운 클래스 객체를 만들어 비교하고자 한다면 어떻게 될까?

        예시로 학생의 나이와 학급 정보를 갖고 있는 클래스를 만든다고 가정하자.

        ```Java
        public class Test {
            public static void main(String[] args)  {
        
                Student a = new Student(17, 2);	// 17살 2반
                Student b = new Student(18, 1);	// 18살 1반
                
                /*
                어떻게 비교..?
                
                if(a > b) ..?
                */
                
            }
        }
        
        class Student {
        
            int age;			// 나이
            int classNumber;	// 학급
            
            Student(int age, int classNumber) {
                this.age = age;
                this.classNumber = classNumber;
            }
        }
        ```


        - 두 객체(a, b)를 어떻게 비교할 것인가? 
        - 부등호로 비교하려면 나이를 기준으로 비교되는 건가?
        -  학습을 기준으로 비교되는 건가?

        <br />

        본질적으로 객체는 사용자가 기준을 정해주지 않는 이상 어떤 객체가 더 높은 우선순위를 갖는지 판단할 수가 없다. 

        이러한 문제점을 해결하기 위해 만든 것이 Comparable과 Comparator이다.

<br />

  - Comparable과 Comparator의 역할은 비슷한 것 같은데 무슨 차이가 있을까?

  - Comparable의 compareTo(To o)메소드는 파라미터(매개변수)가 1개이고, Comparator의 compare(T o1, T o2) 메소드는 파라미터가 왜 두 개인걸까?


  - 차이점
   
    1. Comparable은 "자기 자신과 매개변수 객체를 비교"하는 것이고, Comparable는 "두 매개변수 객체를 비교"한다는 것이다.

        쉽게 말하자면 Comparable은 자기 자신과 파라미터로 들어오는 객체를 비교하는 것이고, Comparator는 자기 자신의 상태가 어떻든 상관없이 파라미터로 들어오는 두 객체를 비교하는 것이다. 즉, 본질적으로 비교한다는 것 자체는 같지만, 비교 대상이 다르다는 것이다.

    2. Comparable은 lang 패키지에 있기 때문에 import를 해줄 필요가 없지만, Comparator는 util 패키지에 있기 때문에 import가 필요하다.


<br />

### 2. Comparable과 Comparator의 사용법

  - Comparable

    "자기 자신과 매개변수 객체를 비교"하는 용도로 사용한다.

    <img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbgjmaA%2Fbtq3Fnxx3RH%2F7zsHFMkhuuH7pcdj3GJUGK%2Fimg.png">

    <br />

    ```Java
    public class ClassName implements Comparable<Type> { 
        ...
    
        // 필수 구현 부분
        @Override
        public int compareTo(Type o) {
            /*
            비교 구현
            */
        }
    }
    ```

    이때, 필수 구현 부분인 compareTo() 메소드가 객체를 비교할 기준으로 정의해주는 부분이다.
    
    Comparable은 자기 자신과 매개변수 객체를 비교한다고 했다. 즉, 자기자신은 ClassName으로 생성한 객체 자신이 되고, 매개변수 객체는 ClassName.compareTo(o); 를 통해 들어온 파라미터 o가 비교 할 객체가 되는 것이다.

    > 정리하면 Comparable의 compareTo는 자기 자신과 매개변수를 비교하고, compareTo는 정수를 반환하며, 자기 자신을 기준으로 상대방과의 차이 값을 비교하여 반환한다.

    - 주의사항

        compareTo를 구현할때 Overflow 혹은 Underflow가 발생할 여지가 있는지를 반드시 확인하고 사용해야 한다. 

        특히 primitive 값에 대해 위와 같은 예외를 만약 확인하기 어렵다면 <, >, == 으로 대소비교를 해주는 것이 안전하며 일반적으로 권장되는 방식이다.

    <br />

  - Comparator

    - "두 매개변수 객체를 비교"를 담당

        즉, 자기 자신이 아니라 파라미터(매개 변수)로 들어오는 두 객체를 비교하는 것이다.

    <br />

    - compare 메소드 매커니즘 자체는 compareTo와 같지만, 차이점은 자기 자신과 비교되느냐 안되느냐의 차이다.


<br />
<hr />
<br />

### Comparator 활용

  - Comparator를 통해 compare 메소드를 사용려면 compare메소드를 활용하기 위한 객체가 필요하게 된다.

    무슨 말인가 하면, a, b, c 객체가 생성되어있고, 이들을 비교를 하고 싶다면 어느 한 객체를 통해 compare메소드를 사용해야한다는 것이다.

    ```Java
    public class Test {
        public static void main(String[] args)  {
    
            Student a = new Student(17, 2);		// 17살 2반
            Student b = new Student(18, 1);		// 18살 1반
            Student c = new Student(15, 3);		// 15살 3반
            Student comp = new Student(0, 0);	// 비교만을 위해 사용할 객체
                
            int isBig = comp.compare(a, b);
            int isBig2 = comp.compare(b, c);
            int isBig3 = comp.compare(a, c);
            
        }
    }
    ```

    <br />

    위 코드는 Student 클래스에서 변수로 두고 있던 age와 classNumber 변수는 굳이 쓸모가 없음에도 생성되어버린다는 단점이 있다.

    즉, 원하는 것은 Comparator 비교 기능만 따로 두고 싶은 것이다.

    Comparator 기능만 따로 두고싶다면 어떻게 해야할까?

    답은 "익명 객체(클래스)를 활용한다"

    ```Java
    public class Anonymous {
        public static void main(String[] args) {
        
            Rectangle a = new Rectangle();
            
            // 익명 객체 1 
            Rectangle anonymous1 = new Rectangle() {
            
                @Override
                int get() {
                    return width;
                }
            };
            
            System.out.println(a.get());
            System.out.println(anonymous1.get());
            System.out.println(anonymous2.get());
        }
        
        // 익명 객체 2
        static Rectangle anonymous2 = new Rectangle() {
            
            int depth = 30;
            @Override
            int get() {
                return width * height * depth;
            }
        };
    }
    
    class Rectangle {
        
        int width = 10;
        int height = 20;
        
        int get() {	
            return height;
        }
    }
    ```

    <br />

    보통의 경우 다음과 같이 생성할 것이다.

        Rectangle a = new Rectangle();

    하지만, 익명객체의 경우는 다음과 같이 생성된다.

        Rectangle a = new Rectangle() { //...구현부...// };

    왜 익명 객체인 것일까? 얼핏보면 같은 객체 생성 방식인 것 같지만, 우리가 보아야 할 것은 { } 블럭 안의 구현부이다.

    우리가 객체를 구현한다는 것은 무엇일까? 바로 변수를 선언하고, 메소드를 정의하며 하나의 클래스(객체)로 만든다는 것을 의미한다.

    말 자체는 어렵지만 쉽게 생각해보면 위 Rectangle 클래스처럼 일반적인 클래스 구현 방식과, interface 클래스를 implements 하여 interface의 메소드를 재정의하거나, class 를 상속(extends)하여 부모의 메소드, 필드를 사용 또는 재정의 하는 것들 모두 객체를 구현하는 것이다. 이 때, 구현을 하는 클래스들은 모두 '이름'이 존재한다.

    그러나 한 번 Rectangle anonymous2 = new Rectangle() {...} 이 부분을 한 번 봐보자. 구현부에서 분명히 변수를 선언하기도 하고, Rectangle 클래스의 메소드 get()을 '재정의(Override)'를 했다.

    즉, 쉽게 생각하여 'Rectangle을 상속받은 하나의 새로운 class라는 것이다.' 

    분명 새로운 class인데 이름이 정의되지 않고 있다.

    <br />

    우리가 원하는 것은 무엇이었을까? 바로 Comparator 의 기능만 사용하고 싶은 것이다. 즉, Comparator의 구현을 통해 compare 만 사용하고 싶은 것이라는 뜻이다.

    즉, 이름은 정의 되지 않지만, Comparator을 구현하는 익명객체를 생성하면 되는 것이다.

    이 때, Comparator 구현은 이 전에 class Student implements Comparator { ... } 에서 구현했던 방식을 그대로 차용하면 된다.


    ```Java
    import java.util.Comparator;
 
    public class Test {
        public static void main(String[] args) {
        
            // 익명 객체 구현방법 1
            Comparator<Student> comp1 = new Comparator<Student>() {
                @Override
                public int compare(Student o1, Student o2) {
                    return o1.classNumber - o2.classNumber;
                }
            };
        }
    
        // 익명 객체 구현 2
        public static Comparator<Student> comp2 = new Comparator<Student>() {
            @Override
            public int compare(Student o1, Student o2) {
                return o1.classNumber - o2.classNumber;
            }
        };
    }
    
    
    // 외부에서 익명 객체로 Comparator가 생성되기 때문에 클래스에서 Comparator을 구현 할 필요가 없어진다.
    class Student {
    
        int age;			// 나이
        int classNumber;	// 학급
        
        Student(int age, int classNumber) {
            this.age = age;
            this.classNumber = classNumber;
        }
    
    }
    ```


    익명 객체의 경우 필요에 따라 main함수 밖에 정적(static) 타입으로 선언해도 되고, main안에 지역변수처럼 non-static으로 생성해도 된다.

    외부에서 Comparator을 구현하는 익명객체가 생성되었기 때문에, Student 클래스 내부에서 우린 Comparator을 구현해줄 필요가 없어졌다.

    즉, 이 전에 a.compare(b, c) 이런식이 아니라, 위에서 생성한 익명객체를 가리키는 comp 를 통해 comp.compare(b, c) 이런 식으로 해주면 된다는 것이다.

    익명객체를 통해 여러가지 비교 기준을 정의할 수 있다는 것이 큰 장점인 것이다.

    Comparable도 익명객체로 할 수 있지 않나요?라고 물을 수 있다. 물론 생성이 가능은 하다.

    하지만 좀만 고민해보면 굳이 Comparable을 익명객체로 생성 할 필요도 없고 오히려 복잡해진다. 이유는 단순하다.

    Comparable과 Comparator의 차이는 계속 말했듯이 "자기 자신"과 하나의 매개변수를 비교하느냐, 두 개의 매개변수를 비교하느냐의 차이다.

    Comparable에서 자기 자신은 무엇인가? 익명 객체가 될 것이다. Student객체가 아니라는 것이다. 즉, 익명의 객체와 Student가 비교하는 것이지, Student와 Student가 비교되는 것이 아니라는 것이다. 한 마디로 자기 동일한 타입의 자신의 객체와 어떤 객체를 비교하고자 하면 Comparable을 익명객체로 선언한다고 한들, 동일한 타입 비교는 불가능하다는 것이다.

<br />
<hr />
<br />


### 정리

  - Comparable의 특징

    1. 자기 자신과 매개변수를 비교

    2. compareTo 메소드를 반드시 구현

    3. compareTo 메소드 구현시 Overflow 혹은 Underflow가 발생할 여지가 있는지를 반드시 확인해야 함.








 


    






    