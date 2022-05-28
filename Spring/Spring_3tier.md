# Spring 3 tier

## 1. 스프링의 구성

<br />

![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FdCW3D0%2FbtrkoGoi0am%2FQqDQopTWCJ36jXaQr969mk%2Fimg.png)

 - 기본적인 계층으로는 프리젠테이션 계층(Presentation Layer), 서비스 계층(Service Layer), 데이터액세스 계층(Data Access Layer) 3가지 계층과 모든 계층에서 사용되는 도메인 모델 클래스로 구성되어 있다.
 - 각각의 계층은 계층마다 독립적으로 분리하여 구현하는 것이 가능해야하고, 각 계층에서 담당해야할 기능들이 있다. 
 - 위의 세가지 계층들은 독립적으로 분리할 수 있도록 구현해야하고, 일반적으로 각 계층 사이에는 인터페이스를 이용하여 통신하는 것이 일반적이다. 

 <br />

### 1. 프리젠테이션 계층 (Presentation Layer)
    - 프리젠테이션 계층은 브라우저상의 웹 클라이언트의 요청 및 응답을 처리한다. 
    - 서비스 계층과 데이터 액세스 계층에서 발생하는 Exception에 대한 처리를 하고, 
    - 최종 UI에서 표현해야할 도메인 모델을 사용한다. 
    - 최종 UI에서 입력한 데이터에 대한 유효성 검증 기능을 프리젠테이션 계층에서 제공한다.
    - 비즈니스 로직과 최종 UI 를 분리하기 위해서 컨트롤러 기능을 제공한다. 
    - @Controller 어노테이션을 사용한다. 

 <br />

### 2. 서비스 계층 (Service Layer)
    - 서비스 계층은 애플리케이션 비지니스 로직 처리와 비지니스와 관련된 도메인 모델의 적합성 검증한다.
    - 트랜잭션 처리를 한다. 
    - 서비스 계층은 프리젠테이션 계층과 데이터 액세스 계층 사이를 연결하는 역할을 한다. 
    - 따라서 다른 계층들과 통신하기 위한 인터페이스를 제공한다. 
    - Service 인터페이스와 @Service 어노테이션을 사용한다. 

<br />

### 3. 데이터 액세스 계층 (Data Access Layer)
    - 데이터 액세스 계층은 영구 저장소의 데이터를 조작하는 데이터 액세스 로직을 객체화한다. 
    - 데이터의 CRUD(등록, 조회, 수정, 삭제)를 한다. 
    - ORM(Object Relational Mapping) 프레임워크(Mybatis, Hibernate)를 주로 사용하는 계층 
    - @Repostiory 어노테이션 사용 

<br />

### 4. 도메인 모델 클래스 (Domain main Class)
    - 관계형 데이터베이스의 엔티티와 비슷한 개념을 가지는 것으로 VO(Value Object) 또는 DTO(Data Transfer Object)객체에 해당한다. 
    - 도메인 모델 클래스는 3개의 계층 전체에 걸쳐 사용된다.
    - private로 선언된 멤버변수와 getter, setter 메서드를 가진 클래스를 의미한다. 

<br />
<hr />
<br />

## 2. Spring Framework 구조

<br />

![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FKn1lN%2Fbtq5fDsegsV%2FpMxVSu0gPJqqLTzEYFsuHk%2Fimg.png)

<br />

1. Spring Core

    Spring Core는 Spring Container을 의미합니다. core라는 말 그대로 Container는 Spring Framework의 핵심이며 그중 핵심은 Bean Factory Container입니다.  그 이유는 바로 Bean Factory는 IOC패턴을 적용하여 객체 구성 부터 의존성 처리까지 모든 일을 처리하는 역할을 하고 있기 때문입니다.
 
2. Spring Context

    Spring context는 Spring Framework의 context 정보들을 제공하는 설정 파일입니다. Spring Context에는 JNDI, EJB, Validation, Scheduiling, Internaliztaion 등 엔터프라이즈 서비스들을 포함하고 있습니다.
 
3. Spring AOP

    Spring AOP module은 Spring Framework에서 관점지향 프로그래밍을 할 수 있고 AOP를 적용 할수 있게 도와주는 Module입니다. 해당 AOP에 대한 내용은 위에서 설명 했기 때문에 넘어 가도록 하겠습니다.
 
4. Spring DAO

    DAO란 Data Access Object의 약자로 Database Data에 접근하는 객체입니다. Spring JDBC DAO는 추상 레이어를 지원함으로써 코딩이나 예외처리 하는 부분을 간편화 시켜 일관된 방법으로 코드를 짤 수 있게 도와줍니다.
 
5. Spring ORM

    ORM이란 Object relational mapping의 약자로 간단하게 객체와의 관계 설정을 하는 것입니다. Spring에서는 Ibatis, Hibernate, JDO 등 인기있는 객체 관계형 도구(OR도구)를 사용 할 수 있도록 지원합니다.
 
6. Spring Web

    Spirng에서 Web context module은 Application module에 내장되어 있고 Web기반의 응용프로그램에 대한 Context를 제공하여 일반적인 Web Application 개발에 필요한 기본적인 기능을 지원합니다. 그로인해 Jakarta Structs 와의 통합을 지원하고 있습니다.
 
7. Spring MVC

    Spring에서는 MVC에서는 Model2 구조로 Apllication을 만들 수 있도록 지원합니다. MVC (Model-View-Controller) 프레임 워크는 웹 응용 프로그램을 작성하기위한 완전한 기능을 갖춘 MVC를 구현합니다. MVC 프레임 워크는 전략 인터페이스를 통해 고급 구성 가능하며 JSP, Velocity, Tiles, iText 및 POI를 포함한 수많은 뷰 기술을 지원하고 있습니다.
