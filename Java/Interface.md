# Interface

  - "인터페이스 내에 선언된 메소드를 '반드시 구현'해야하는데 왜 compare 메소드만 구현하는가?"
    
    ▶ interface는 함수의 껍대기만 있는 클래스라고 볼 수 있다. 

        예시로 자동차를 설계할 때, "자동차"라는 것 자체는 추상적인 개념이다. 자동차는 바퀴가 4개 있고, 핸들과 기어 있는 동력 물체라는 개념이 존재한다. 이러한 추상적인 개념을 interface 라고 보면 된다.
    
        이러한 개념을 구체화, 즉 구현을 하여 핸들은 어떤 모양으로 할 것인지 바퀴는 어느 크기, 어느 위치에 둘 것인지 구체적으로 만들어 K5, K7 등 하나의 제품이 만들어진다. 이를 바로 class 라고 보면 된다. 이 구조를 파악해보면 인터페이스는 어떤 사물에 대해 기본적인 '필수요소'들을 선언만 해놓은 것이고, 이러한 필수요소들을 구체적으로 구현하는 것은 클래스라고 보면 된다. 

        즉, interface에 선언된 메소드(바퀴, 핸들, 기어, 동력 장치)들이 있고, 이 인터페이스를 구현하는 클래스는 인터페이스에 선언된 메소드(바퀴, 핸들, 기어, 동력 장치)를 반드시 구체화 하도록 강제하고 있다. 이를 오버라이드(Override) 또는 재정의라고 불린다.

        그래서 interface 파일의 경우 메소드(함수)를 선언만 해놓을 뿐 함수의 내용은 구체화 하지 않는데, 이를 추상 메소드라 한다.

    ```Java
    interface Car{
        void setHandle();
        void setWheel();
        
        int gear();
    }
    ```

     인터페이스를 구현하고자 하면 아래와 같이 '반드시 구현'해주어야 한다.

     ```Java
     class K5 implements Car {
    
        @Override
        void setHandle(int size) {
            handleSize = size;
        }
    
        @Override
        void setWheel() {
            WheelCount = 4;
        }
    
        @Override
        int gear() {
            return nowGear;
        }
    }
     ```

<br />

  - Java8부터는 Interface에서도 일반 메소드(함수)를 구현할 수 있도록 변경되었다. 거의 대부분 default 또는 static으로 선언된 메소드들을 보면 함수를 구현하고 있다.

    <br />

    <img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FdonyzB%2Fbtq3zM6CXiO%2FeCX7EIRQglpytqapalnook%2Fimg.png">

    <br />

  - 기존 구현된 함수를 반환하거나 등 함수의 내용이 {...} 블록 안에 구현이 되어있는 것을 볼 수 있다.

    정리하면 default 또는 static으로 선언된 메소드가 아니라면 이는 추상메소드로 반드시 재정의를 해주어야 한다.

    default와 static의 차이는 default로 선언된 메소드는 재정의(Override)를 할 수 있고, static은 재정의를 할 수 없다는 차이다.