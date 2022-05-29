# Bean

## 1. Bean이란?
- Bean은 Spring Bean Container에 존재하는 객체를 의미한다.
- Bean Container는 의존성 주입을 통해 Bean객체를 사용할 수 있도록 해준다.
- Bean은 보통 싱글톤 패턴으로 존재한다.
- Beans는 우리가 컨테이너에 공급하는 설정 메타 데이터에 의해 생성된다.

<br />
<hr />
<br />

## 2. Bean은 어떻게 생성되는 것일까?

1. Component Scan
- 스프링부트로 애플리케이션을 만들게 되면 가장 상위 클래스에 @SpringBootApplication 이 있다.
- SpringBootApplication을 자세히 보면 @ComponentScan은 @Component 이나 sterotype(@service, @Controller, @Repository 등) 어노테이션이 부여된 class를 찾아 자동으로 Bean으로 등록해주는 역할을 한다.
- 여기서 @ComponentScan을 해주는 범위가 해당 어노테이션이 붙은 위치보다 하위의 class들만 스캔해주기 때문에 @SrpingBootApplication의 우치가 가장 상위 위치에 있어야한다.
- @Service, @Controller, @Repository 등의 어노테이션들을 확인해보면 @Component가 있는 것을 확인할 수 있다.
- 추가적으로 Bean으로 등록하고 싶은 class가 있다면 @Component 어노테이션을 붙여줘도 상관 없다.


2. @Configuration에서 @Bean으로 등록
- @Configuration 어노테이션을 사용해서 직접 @Bean을 등록해주는 방법이다. 
- Bean 어노테이션을 사용하면 자동으로 빈으로 등록된다.

```Java
@Configuration
public class HttpConfig {

    @Bean
    public RestTemplate createRestTemplate(){
        return new RestTemplate();
    }
}
```