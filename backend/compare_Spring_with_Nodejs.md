# Compare_Spring_with_Nodejs

    (서론)
    1일차에는 원래 스프링 프레임워크는 어떤 특징 혹은 장점을 가지고 있나요?(3가지 이상) 에 대한 답변을 하는 것이다.
    하지만 우리 조는 더 나아가서 NodeJS와 비교하여 학습하기로 결정하였다.

<hr/>

## 1. Spring
<br />

### 1.1 Spring 이란?
 - 스프링 프레임워크가 등장하기 전에는 EJB라는 기술을 통해 웹 애플리케이션을 개발하였는데, 개발자들에게 있어서 이 기술은 여러가지 복잡성으로 인해 사용하기 꽤나 까다로웠습니다. 이러한 닩머을 보완하기 위한 기술들이 개발되기 시작했고, 그 과정에서 호평받은 기술이 스프링이다.

> 스프링라는 이름의 유래는 Java EE의 스펙을 구현한 EJB가 기술의 복잡도가 증가해서 성능이 느렸던 것을 탈피하여, EJB 시절을 "겨울"에 빗대어 겨울 후의 "봄"으로 새로운 시작한다는 것을 의미한다.

 - Spring Boot는 위의 Spring을 더 쉽게 사용하여 상용화 가능한 애플리케이션을 만들수 있도록 돕는 도구이다. Spring은 초기에 세팅해야 할 것이 많아, 초보자들에게 진입장벽이 높고 할애되는 시간이 많은데, 이러한 문제를 해결하고자 등장한 Framework가 Spring Boot이다.
<br />

### 1.2 프레임워크 vs 라이브러리
  
  1. 프레임워크
  - 프레임워크는 뼈대나 기반 구조를 뜻하고, 제어의 역전(IOC) 개념이 적용된 대표적인 기술입니다.
  - 소프트웨어에서의 프레임워크는 '소프트웨어의 특정 문제를 해결하기 위해서 상호 협력하는 클래스와 인터페이스의 집합'이라 할 수 
  있으며, 완성된 어플리케이션이 아닌 프로그래머가 완성시키는 작업을 해야합니다.

  2. 라이브러리
  - 라이브러리는 단순 활용가능한 도구들의 집합을 말합니다.
  > 즉, 개발자가 만든 클래스에서 호출하여 사용, 클래스들의 나열로 필요한 클래스를 불러서 사용하는 방식
  
  <br />

  ![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbhvcLo%2Fbtq66VGlc9A%2F1LYV9wEBr2KKWoMwA9IgpK%2Fimg.jpg)

  <br />

    프레임워크와 라이브러리의 차이는 위 사진으로 설명할 수 있습니다. 관건은 애플리케이션의 흐름을 누가 쥐고 있느냐입니다.
    프레임워크는 전체적인 흐름을 스스로가 쥐고 있으며 사용자는 그안에서 필요한 코드를 짜 넣지만,
    라이브러리는 사용자가 전체적인 흐름을 만들며 라이브러리를 가져다 쓰는 것이라고 할 수 있습니다.
    정리하면, 라이브러리는 가져와서 사용하고 호출하는 측에 전적으로 주도성이 있고
    프레임워크는 그 틀안에 이미 제어 흐름에 대한 주도성이 있다는 것입니다.


<br />

### 1.3 Spring 프레임워크
  
 > 자바 엔터프라이즈 개발을 편하게 해주는 오픈 소스 경량급 애플리케이션 프레임워크
 
    1. 애플리케이션 프레임워크
    - 일반적으로 라이브러리나 프레임워크는 특정 업무 분야나 한 가지 기술에 특화된 목표를 가지고 있다.
    (예시) 웹 계층을 MVC 구조로 손쉽게 만들 수 있게 한다거나, 포맷과 출력장치를 유연하게 변경할 수 있는 애플리케이션의 로그 기능을 제공하는 것이 있다. 그래서 프레임워크는 애플리케이션의 특정 계층에서 주로 동작하는 한 가지 기술 분야에 집중된다.

    - 애플리케이션 프레임워크는 특정 계층이나, 기술, 업부 분야에 국한되지 않고 전 영역을 포괄하는 범용적인 프레임워크를 의미한다.
    즉, 애플리케이션 프레임워크는 개발의 전 과정을 빠르고 편리하며 효율적으로 진행하는데 일차적인 목표를 두는 프레임워크

    2. 오픈소스 경량급
    - 경량급은 기존의 EJB처럼 툴의 도움 없이는 다루기 힘든 난해한 설정파일 구조와 까다로운 패키징, 불편한 서버 배치 등으로 인한 부담을 없애고, 쉽게 해당 기능들을 사용할 수 있게 되었음을 의미한다.

  1. 차별성
    
    1) 복잡함에 반기를 들어서 만들어진 프레임워크
    - 엔터프라이즈급의 시스템이 실패하는 이유를 '복잡성'으로 보고 이를 해결하기 위해 나온 경량화된 프레임워크
    - 일반적인 Java 클래스와 인터페이스를 이용하는 구조를 사용하고 EJB에 비해 가벼움
    - 진입 장벽이 높지 않고 빠른 시간에 엔터프라이즈급의 시스템 구축이 가능

    2) 프로젝트 전체 구조 설계에 유용한 프레임워크
    - 이전에 다른 프레임워크들은 웹이나 데이터베이스 등의 전문적인 영역에 대해서만 지원하는 경우가 많았음
    - 스프링은 어느 한 분야에만 집중하지 않고 전체를 설계하는 용도로 사용 가능
    - 제어의 역행(IoC) 개념
    
    3) 다른 프레임워크들의 포용
    - 전체 구조에 집중하여 설계되었기 때문에 다른 프레임워크와 공존하는 방식으로 사용 가능
    - 다른 프레임워크들과의 통합을 지원하여 최소한의 수정이 가능
    - 기본 뼈대를 흔들지 않고 여러 종류의 프레임워크를 혼용해서 사용 가능
    
    4) 개발 생산성과 도구의 지원
    - 스프링은 이론적으로 개발자가 이해해야하는 부분이 많지만 결과적으로 코드의 양은 줄어듬
    - XML 설정을 이용하여 유지보수가 용이함
    - STS, Eclipse, Intellij 등의 플러그인도 지원하여 새로운 개발 도구에 대한 별도의 적응 없이도 개발이 가능

  
  2. 주요 특징
    
  - POJO(Plain Old Java Object) 기반의 구성

      ```
      스프링은 내부적으로 객체 간의 관계를 구성할 때 별도의 API 등을 사용하지 않는 POJO(Plain Old Java Object) 만으로 구성이 가능하도록 되어있습니다. 따라서, 일반적인 Java 코드를 이용하여 객체를 구성하는 방식 그대로 스프링에서 사용 가능합니다.이것은 특정한 라이브러리나 컨테이너에 기술에 종속적이지 않다는 것을 의미합니다. 이로 인하여 개발자는 가장 일반적인 형태로 코드를 작성하고 실행할 수 있기 때문에 높은 생산성과 유연한 테스트를 할 수 있는 장점을 갖게 됩니다.
      ```

  - DI(Dependency Injection, 의존성 주입)을 통한 객체 간의 관계 구성
    ```
    1. IOC(제어의 역행)
    - 조립된 코드의 최종 호출은 개발자가 결정하는 것이 아니라 프레임워크 내부에서 결정된 대로 이루어지게 하는 것

    2. 의존성 주입
    - '의존성 주입(DI, Dependency Injection)' 은 제어의 역행이 일어나는 것을 전제 조건으로 하여 스프링 내부의 객체(스프링에서는 bean이라는 용어로 표현)들 간의 관계를 관리할 때 사용됩니다. 의존성 주입은 말 그대로 특정 객체에 필요한 객체를 외부에서 결정하여 연결시키는 것을 의미합니다.

    3. 의존성 주입의 종류
    1) 생성자를 통한 방법
    2) setter를 이용한 방법

    4. 의존성 주입에 대한 특징
    1) 메서드나 객체(bean)의 호출 작업은 제어의 역행(IoC)를 통해 외부에서 이루어짐 (외부는 객체를 기준으로 봤을 때를 의미)
    2) 제어의 역행(IoC)을 전제 조건으로 의존성 주입이 일어남.
    3) 의존성을 가진 객체에 대해 스프링에서 의존성 주입(DI)이 발생하도록 함.
    4) 의존성 주입(DI)의 특징으로 인하여 POJO 개발이 가능
    ```

  - AOP(Aspect Oriented Programming) 지원
    ```
    - 대부분의 시스템에서 비즈니스 로직은 아니지만 보안, 로그, 트랜잭션과 같이 반드시 처리가 필요한 부분을 스프링에서는 횡단 관심사(cross-concern)라고 합니다. AOP는 이러한 횡단 관심사를 별도 모듈로 분리하는 프로그래밍 패러다임이다.

    - 스프링에서는 이러한 관심사를 비즈니스 로직과 분리하여 중복된 코드를 줄이고 개발자가 비즈니스 로직에 집중하도록 만들어준다.
    ```
  - 편리한 MVC 구조
  - WAS에 독립적인 개발환경

<br />
<hr />
<br />



## 2. NodeJS
<br />

### 2.1 Node.js란?
> Node.js는 Chrome V8 JavaScript 엔진으로 빌드 된 JavaScript 런타임입니다.


즉, 노드를 통해 다양한 자바스크립트 애플리케이션을 실행할 수 있으며, 서버를 실행하는데 제일 많이 사용된다.

- Node.js는 JavaScript를 서버에서도 사용할 수 있도록 만든 프로그램이다.
- Node.js는 V8이라는 JavaScript 엔진 위에서 동작하는 자바스크립트 런타임(환경)이다.
- Node.js는 서버사이트 스크립트 언어가 아니다. 프로그램(환경)이다.
- Node.js는 웹서버와 같이 확장성 있는 네트워크 프로그램을 제작하기 위해 만들어졌다.
- Node.js는 확장성 있는 네트워크 애플리케이션(특히 서버 사이드) 개발에 사용되는 소프트웨어 플랫폼이다.
- Node.js는 자바스크립트를 활용하며 Non-blocking I/O와 단일 스레드 이벤트 루프를 통한 높은 처리 성능을 가지고 있다.
- Node.js는 내장 HTTP 서버 라이브러리를 포함하고 있어 웹 서버에서 아파치 등의 별도의 소프트웨어 없이 동작하는 것이 가능하며 이를 통해 웹 서버의 동작에 있어 더 많은 통제를 가능케 한다.

> 즉, Node.js를 통해 웹어플리케이션이 더욱 발전하게 되었으며, 정적인 홈페이지 뿐만 아니라 쇼핑몰, 티켓 예매사이트, 블로그 등 데이터가 변해가는 사이트를 만들 수 있으며, 여러 개발자가 만든 프로그램과 게임을 웹상에서 구동시켜 안드로이드폰, 아이폰, 윈도우PC, 맥 등 플랫폼의 제약에서 벗어나 어디든 상관없이 실행 가능하게 해준다.

<br />

### 2.2 특징
1. 쓰레드 기반 동기방식(Blocking I/O)
  - 하나의 쓰레드가 request를 받으면 모든 처리가 완료될때까지 기다리다가 처리결과가 완료되면 다시 응답을 보냄
  - 기존 업무 처리가 완료되기 전에 또다른 request가 있으면 새로운 쓰레드가 업무를 처리함.
  - 동시 request가 많은 경우 많은 쓰레드가 필요하게 되어 서버 과부하가 걸리게 된다.


2. 단일쓰레드 이벤트 루프 기반 비동기방식( Non-Blocking I/O) 
  - 하나의 쓰레드가 request를 받으면 바로 다음 처리에 요청을 보내놓고 다른 작업을 처리하다가 먼저 요청한 작업이 끝나면 이벤트를 받아서 응답을 보낸다.
  - 동시 request가 오더라도 처리가 완료될때까지 기다리지 않아도 되기 때문에 서버 부하가 적다.


### 2.3 장점과 단점
  
  1. 장점 
  - 한 가지 언어로 서버와 클라이언트의 로직을 처리할 수 있다.
  - 배우기 쉽고, 개발을 빠르게 진행할 수 있다.
  - Non-blocking I/O와 단일 스레드 이벤트 루프를 통한 높은 처리 성능
  - 로컬에서 서버만 켜봐도 얼마나 가볍게 돌아가는지 알 수 있다.
  - 이벤트 기반 비동기방식이라 서버 무리가 적다.
  - npm을 이용해 자신이 필요한 라이브러리와 패키지를 검색해서 설치하고 사용할 수 있기 때문에 개발속도와 효율성이 크게 향상

  2. 단점
  - 이벤트 기반 비동기방식이라 서버단 로직이 복잡한 경우 콜백함수의 늪에 빠질 수 있다.
  
    예를 들어, 한번의 요청에 대해 DB에서 조회한 결과값에 따라 다른 로직을 처리해야 하며, 이런 로직이 여러개인 경우 콜백함수 늪 (Callback Hell) 에 빠진다.

  - 코드를 순차적으로 실행하는 것이 아니라 비동기 방식으로 이벤트를 보내고, 응답(이벤트)이 오면 처리하는 방식이기 때문에 java 개발을 했던 방식으로 설계하고 프로그래밍하면 큰 문제가 발생한다. 
  - 단일 쓰레드(Single Thread)이기 때문에 하나의 작업 자체가 많이 걸리는 웹서비스에는 어울리지 않다. 
  - 코드가 수행되어야 코드에 에러가 있는지 알 수 있으며, 에러가 날 경우 프로세스가 내려가기 때문에 테스트가 엄청 중요하다. 

### 2.4 NodeJS의 사용처
  1. Node.js 가 어울리는 웹서비스
  - 간단한 로직. 
  - 대용량(동시에 여러 request를 처리)
  - 빠른 응답시간 요구
  - 빠른 개발 요구
  - 비동기방식에 어울리는 서비스(네트워크 스트리밍 서비스, 채팅 서비스 등)
 
  2. Node.js 가 어울리지 않는 웹서비스
  - 단일 처리가 오래 걸리는 경우 : 싱글 쓰레드이기 때문
  - 서버 체크로직이 많은 경우 : 비동기방식이기 때문에 CallBack Hell에 빠지지 않기 위해
  - 업무 복잡도/난이도가 높은 경우 : 에러가 나면 서버가 죽기 때문에 코드 품질 중요

<br />
<hr />
<br />


## 참고
1. [스프링 프레임워크에 대한 간단한 소개](https://freestrokes.tistory.com/79)
2. [Node.js vs. Spring Boot — Which Should You Choose?](https://betterprogramming.pub/node-js-vs-spring-boot-which-should-you-choose-2366c2f76587)