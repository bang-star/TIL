# Dependency Injection

## DI란?
- 의존하는 클래스에 대한 인스턴스를 직접 생성하지 않고, 컨테이너로부터 생성된 빈을 Setter나 생성자를 통해 외부로부터 주입받는 것을 의미한다.
- 스프링 프레임워크 버전 4.3 이후에는 @Autowired도 생략되면서 생성자에 사용한 Bean만 선언하면 된다. 코드가 간결해졌다.

1. 생성자를 이용한 방법

```Java
public class ClassName {
	private final IMacBook mac;

	@Autowired
	public ClassName(IMacBook mac) {
		this.mac = mac;
	}
}​
```

2. setter를 통한 전달
```Java
public class ClassName {
	private IMacBook mac;
	
	@Autowired
	public void setMacBook(IMacBook mac) {
		this.mac = mac;
	}
}​
```


3. Field Injection - 일반적인 변수 선언만으로 전달

```Java
public class ClassName {

	@Autowired
	private IMacBook mac;
	
}​
```
<br />

```
    위 세 가지 중에서 Intellij에서는 첫 번째 방법을 사용하라고 권장한다. 이유는 아래와 같다.
    NullPointerException를 방지할 수 있다.
    주입받을 필드를 final로 선언 가능하다.
    스프링에서는 테스트 코드 작성이 쉬워지며, 순환 참조 방지가 된다.
```

## DI는 왜 사용할까? 
- 가장 큰 이유는 의존성을 외부에서 주입하기 위해 사용한다.

<br />

``` Java
    class OS{
        private Window window;
        private IMacBook macos;

        public OS(){
            this.window = new window();
            this.macos = new Mac();
        }

        public startOS(){
            this.window.boot();
            this.macos.boot();
        }
    }
```

        현재 위 코드에서 boot 메소드를 호출하기 위해서는 클래스를 생성해야할 필요가 있다. 
        여기서 OS 클래스는 window, macos 클래스의 의존성을 가진다고 말할 수 있다.
        위와 같이 의존성은 곧 결합도를 의미하는데, 결합도가 높아질 경우 많은 문제가 발생한다.

        첫 번째, 반복된 코드가 계속해서 발생하게 된다.
        두 번째, 변경하기 위해서는 많은 부분을 고쳐야한다. -> 비용 증가
        세 번째, 프로그램에서 클래스를 재사용하기 힘들다.

        이와 같이 결합도가 높아지면 응집도가 낮아질 수 있다.

        응집도가 낮아지면 
        첫 번째 이해하기 힘들다.
        두 번째 재사용성이 떨어진다.
        세 번째 유지보수가 힘들다.

        그러므로 소프트웨어 공학의 전통적인 이론에 따르면, 결합도는 낮고 응집도는 높게 구성해야한다.



