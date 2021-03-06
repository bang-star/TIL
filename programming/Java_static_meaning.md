# static의 의미

## 정적이란?
- 정적(Static)은 고정된이란 의미를 가지고 있다. 
- Static이라는 키워드를 사용하여 변수와 메소드를 만들 수 있는데 다른 말로 정적 필드와 정적 메소드라고 하고 둘을 합쳐 정적 멤버(클래스 멤버)라고 한다.
- 정적 필드와 정적 메소드는 객체(인스턴스)에 소속된 멤버가 아니라 클래스에 고정된 멤버입니다.
- 클래스의 로딩이 끝나는 즉시 바로 사용할 수 있습니다.

<br />
<hr />
<br />

## 정적 멤버의 생성
![다운로드](https://user-images.githubusercontent.com/63120360/168941814-e29cf109-5dde-4d5a-861d-3102895d9cf0.png)

- Static 키워드를 통해 생성된 정적 멤버들은 Heap영억이 아닌 Static 영역에 할당됩니다. 
- Static 영역에 할당된 메모리는 모든 객체가 공유하여 하나의 멤버를 어디서든지 참조할 수 있는 장점을 가지지만 GC(Garbage Collector)의 관리 영역 밖에 존재하기에 Static 영역에 있는 멤버들은 프로그램의 종료시까지 메모리가 할당된 채로 존재하게 됩니다.
- static을 너무 남발하게 되면 만들고자 하는 시스템 성능에 악영향을 줄 수 있습니다.

## 정적 멤버 선언
1. 필드나 메소드는 생성 시 인스턴스로 생성할 것인지 정적으로 생성할 것인지에 대한 판단 기준은 공용으로 사용하느냐 아니냐로 생각하면 된다.
2. 자동으로 인스턴스로 생성되며 정적으로 생성하려면 필드와 메소드 선언 시 static이라는 키워드를 추가적으로 붙이면 됩니다.

```Java
  static int num = 0                      // 타입 필드 - 초기값
  public static void static_method(){}    // static 리턴 타입 메소드
```

### 정적 필드 사용 예시
```Java
class Number{
  static int num = 0;   // 클래스 필드
  int num2 = 0;         // 인스턴스 필드
}

public class Static_ex {
  public static void main(String[] args){
        Number number1 = new Number(); //첫번째 number
    	Number number2 = new Number(); //두번쨰 number
    	
    	number1.num++; //클래스 필드 num을 1증가시킴
    	number1.num2++; //인스턴스 필드 num을 1증가시킴
    	System.out.println(number2.num); //두번째 number의 클래스 필드 출력
    	System.out.println(number2.num2); //두번째 number의 인스턴스 필드 출력
  }
}
```

> Number이라는 클래스안에 클래스 변수 num과 인스턴스 변수 num2를 생성하였고 두개의 Number인스턴스 number1과 number2를 생성했을때 number1에서 num1과 num2를 각각 1씩 증가시키고 number2에서 num1와 num2를 각각 출력시켰을때는 num1은 1, num2는 0이 출력되었습니다. 왜 이런 현상이 나타났느냐면 인스턴스 변수는 인스턴스가 생성될 때마다 생성되므로 인스턴스마다 각기 다른 값을 가지지만 정적 변수는 모든 인스턴스가 하나의 저장공간을 공유하기에 항상 같은 값을 가지기에 나타난 현상입니다.


### 정적(Static) 메서드 사용 예시
``` Java
class Name{
    static void print() { //클래스 메소드
	System.out.println("내 이름은 홍길동입니다.");
    }

    void print2() { //인스턴스 메소드
	System.out.println("내 이름은 이순신입니다.");
    }
}

public class Static_ex {
	
    public static void main(String[] args) {
        Name.print(); //인스턴스를 생성하지 않아도 호출이 가능
    	
        Name name = new Name(); //인스턴스 생성
        name.print2(); //인스턴스를 생성하여야만 호출이 가능
    }
}
```
> 정적 메소드는 클래스가 메모리에 올라갈 때 정적 메소드가 자동적으로 생성됩니다. 그렇기에 정적 메소드는 인스턴스를 생성하지 않아도 호출을 할 수 있습니다. 정적 메소드는 유틸리티 함수를 만드는데 유용하게 사용됩니다.
