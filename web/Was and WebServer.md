# Was and Web Server

<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fby53Lq%2Fbtq6MaWGeKj%2FNbPjy9mOAtoKIPiHmWLk01%2Fimg.png" width=800>

<br />

## 1. Web Server
 - 웹 서버(Web Server)는Web server"는 하드웨어, 소프트웨어 혹은 두 개가 같이 동작하는 것을 의미할 수 있습니다

 1. 하드웨어 측면에서
    - web server는 web server의 소프트웨어와 website의 컴포넌트 파일들을 저장하는 컴퓨터입니다. (컴포넌트 파일에는 HTML 문서, images, CSS stylesheets, 그리고 JavaScript files가 있습니다.) 
    - Web server는 인터넷에 연결되어 웹에 연결된 다른 기기들이 웹 서버의 데이터(컴포넌트 파일들)를 주고받을 수 있도록 합니다.

<br />

2. 소프트웨어 측면에서,
    - web server는 기본적으로 웹 사용자가 어떻게 호스트 파일들에 접근하는지를 관리합니다. 이 문서에서 web server는 HTTP서버로 국한합니다. 
    - HTTP 서버는 URL(Web addresses)과 HTTP(당신의 브라우저가 웹 페이지를 보여주기 위해 사용하는 프로토콜)의 소프트웨어 일부입니다.

<br />

### 1.1 Web Server의 기능
 
  - 웹 서버의 주된 기능은 웹 페이지(그림, CSS, JS를 포함한 HTML)를 클라이언트로 전달하는 것
  - 웹 브라우저 또는 웹 크롤러로 부르는 클라이언트는 HTTP를 통해 리소스를 요청하며 서버는 해당 리소스를 반환하거나 처리할 수 없을 경우 에러 메시지를 전달한다. 이러한 리소스는 일반적으로 서버의 보조 기억 장치에 있는 실제 파일을 가리키지만 반드시 그런 것은 아니며 웹 서버가 어떻게 수행하느냐에 따라 달라질 수 있다.
  - 주된 기능은 컨텐츠를 제공하는 것이지만 클라이언트로부터 전달 받는 것도 웹 서버의 기능에 속한다.
  - 보통 대다수의 웹 서버는 Active Server Page(ASP), PHP 등의 서버 사이드 스크립트 언어를 지원하는다. 

  ```
  * 서버 사이드 언어
  - 서버 소프트웨어의 변경 없이도 웹 서버가 수행할 동작을 분리된 서버 사이크 스크립트 언어에 기술할 수 있다는 의미이다.
  - 동적으로 생성된 HTML 문서는 동적 컨텐츠라 하고, 주로 데이터베이스의 정보를 조회해서 보여주거나 수정하기 위해 사용된다.
  ```

<br />

### 1.2 Web Server의 동작
  
  1. 브라우저가 웹 서버에서 불려진 파일을 필요로 할때, 브라우저는 HTTP를 통해 파일을 요청합니다. 
  2. 요청이 올바른 웹 서버(하드웨어)에 도달하였을 때, HTTP 서버(software)는 요청된 문서를 HTTP를 이용해 보내줍니다. 

<br />

  <img src="https://mdn.mozillademos.org/files/8659/web-server.svg">

  > 웹 서버를 공개하기 위해서는 정적 혹은 동적 웹서버가 필요하다.

<br />

### 1.3 Static and Dynamic 

<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Ftpz0I%2Fbtq6Jxyt4Eb%2FVChj16qbobRKgssEuz6WD0%2Fimg.png" width=800>


  1. 정적 
  - 정적 웹 서버 혹은 스택은 HTTP 서버(소프투에어)가 있는 컴퓨터(하드웨어)로 구성
  - 서버가 그 불려진 파일을 당신의 브라우저에게 전송하기 때문에, 정적이라 부른다

  2. 동적
  - 동적 웹 서버는 정적 웹서버와 추가적인 소프트웨어(대부분 일반적인 애플리케이션 서버와 데이터베이스)로 구성
  - 애플리케이션 서버가 HTTP 서버를 통해 당신의 브라우저에게 불려진 파일들을 전송하기 전에, 애플리케이션 서버가 업데이트하기 때문에 동적이라 부른다.
  
<br />

### 1.4 Web Server의 종류
  1. Apache WEB SERVER

  <img src="https://t1.daumcdn.net/cfile/tistory/9968714A5EC61A6727">

  - 가장 대표적인 HTTP 서버는 Apache 입니다 1995년 이후 단 한번도 1위의 자리를 놓친적이 없었으나 최근 들어 Nginx에게 밀리는 추세이며, 거의 모든 운영체제에서 효율적으로 운영되지만 Linux와 사용될때 가장 최적화 됩니다.

  - 장점
    
    1. 오픈소스로 무료
    2. 다양한 모듈 제공
    3. 강력한 커뮤니티로 인한 방대한 자료
    4. 확장성
    5. 보안 수준 우수

<br />

  - 단점
    
    1. 많은 기능들로 인해 느린 측면
    2. 오버헤드 발생

<br />

  2. Apache WEB SERVER

  <img src="https://t1.daumcdn.net/cfile/tistory/992E5C4D5EC626D902">

  - Nginx는 메일 프록시, 리버스 프록시 서버로 무료 오픈 소스로 사용할 수 있는 HTTP 서버입니다
  - 최소한의 리소스로 많은 수의 동시 사용자를 처리로 대규모 웹 트래픽 처리 상황이 발생할 때 고효율을 발휘합니다

  - 장점
    
    1. 오픈소스로 무료
    2. Apache에 비해 가볍다
    3. 프록시 기능이 뛰어나다.

  - 단점
    
    1. 커뮤니티의 자료 부족
    2. 확장 모듈이 Apache에 비해 부족

<br />

  3. IIS Web Server

    - IIS는 Microsoft에서 제공하는 소프트웨어이며 유료
    - 익숙한 GUI를 통해 접근성 용이

    1. 장점
    - Microsoft에서 지원
    - ASP, MSSQL 등과 같은 다른 Microsoft 서비스와 쉽게 통합 가능
    - 간편한 GUI

    2. 단점
    - 가격이 비싸다.
    - Windows Server에서만 동작
    - Apache와 Nginx에 비해 더디고 느리다.
    

<br />
<hr />
<br />

## 2. WAS

```
웹 애플리케이션 서버(WAS)는 웹 애플리케이션과 서버 환경을 만들어 동작시키는 기능을 제공하는 소프트웨어 프레임워크이다.
- 인터넷 삿에서 HTTP를 통해 사용자 컴퓨터나 장치에 애플리케이션을 수행해 주는 미들웨어(소프트웨어 엔진)으로 볼 수 있다.
- 웹 애플리케이션는 동적 서버 컨텐츠를 수행하는 것으로 일반적인 웹서버와 구별이 되며, 주로 데이터베이스 서버와 같이 수행
- 한국에서는 일반적으로 "WAS', 공공기관에서는 "웹 응용 서버", 영어권에서는 "Application Sever"(AS)로 부른다.
```

### 2.1 WAS의 기본 기능

    1. 프로그램 실행 환경과 데이터베이스 접속 기능을 제공
    2. 여러 개의 트랜잭션을 관리
    3. 업무를 처리하는 비즈니스 로직을 수행
    4. Web Service 플랫폼으로서의 역할 병행

### 2.2 차이점

<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fc5IWzl%2Fbtq6VrRPs2b%2FV6zPdmMfYZcxlhByT38KO0%2Fimg.png" width=800>


    - Web Server는 주로 웹브라우저의 HTTP 요청에 대한 응답으로 HTML 페이지, 파일, 이미지, 비디오 같은 정적 웹 컨텐츠 제공

    - Application Server는 일반적으로 웹 콘텐츠도 전달할 수 있지만,
    주요 작업은 최종 사용자 클라이언트와 서버 측 애플리케이션 코드(비즈니 로직이라고 하는 것)간의 상호 작용을 활성화하여 트랜잭션과 동적 콘텐츠를 생성하고 전달하는 것
    - 결과, 의사 결정 지원 또는 실시간 분석, 애플리케이션 서버용 클라이언트는 애플리케이션의 최종 사용자 UI, 웹 브라우저 또는 모바일 앱일 수 있으며 클라이언트-서버 상호 작용은 다양한 통신 프로토콜을 통해 발생할 수 있다.

### 2.4 모호성
> 웹 브라우저가 선택한 애플리케이션 클라이언트로 부상하고 웹 애플리케이션 및 웹 애플리케이션 성능에 대한 사용자 기대치가 높아짐에 따라 경계가 모호해졌다.


    - 대부분의 웹 서버는 웹 서버가 서버 측 논리를 기반으로 동적 콘텐츠를 생성할 수 있도록 하는 스크립트 언어(예: ASP, JSP, PHP, Perl)용 플러그인을 지원합니다. 그리고 점점 더 많은 수의 애플리케이션 서버가 웹 서버 기능을 통합할 뿐만 아니라 HTTP를 기본 프로토콜로 사용하고 웹 서버와의 인터페이스를 위한 다른 프로토콜(예: CGI 및 CGI 변형)을 지원합니다.
    
    - 웹 애플리케이션이 역방향 프록시, 클러스터링, 중복성 및 로드 밸런싱 과 같은 서비스를 활용할 수 있도록 성능과 안정성을 개선하고 개발자가 인프라에 덜 집중하고 코딩에 더 집중할 수 있도록 한다.


<br />
<hr />
<br />

## 요약

<img src="https://images.velog.io/images/osk3856/post/f3a481b3-04b5-4931-8493-c787ba239808/web-service-architecture.png" width=800> 

<br />

    1. Web Server 
    - HTTP 프로토콜을 기반으로 클라이언트의 요청을 서비스, 즉 정적 컨텐츠를 제공한다.
    (유의! 웹 서버가 정적 컨텐츠만 제공하는 것이 아니라 동적 컨텐츠 요청받으면 WAS에게 요청을 넘겨주고 WAS에서 처리한 결과를 클라이언트에게 전달하는 역할을 한다.)

    2. WAS 
    - Web Server + Web Container가 합쳐진 형태, 웹 서버 단독으로 처리할 수 없는 DB조회나 다양한 로직 처리가 필요한 동적 컨테츠를 제공한다. Ex) Tomcat, Jeus
    (사용자의 다양한 요구에 대해 웹 서비스를 제공할 수 있으며, WAS는 JSP, Servlet 구동환경을 제공해주기 때문에 웹 컨테이너 또는 서블릿 컨테이너라고도 부른다)

    => 웹 서버를 WAS 앞에 두고 필요한 WAS들을 Web Server에 플러그인 형태로 설정하여 사용하면 더욱 효율적인 분산처리가 가능하다
    IF WAS가 정적 컨텐츠 요청까지 처리하게 된다면,
        부하가 커지게 되며 동적 컨테츠의 처리속도가 느려진다.
            이로 인해 페이지 노출 시간이 늘어나는 문제가 발생하여 효율성이 크게 떨어진다...



<br />
<hr />
<br />

## 참조
 1. [위키백과 - Web Server](https://ko.wikipedia.org/wiki/%EC%9B%B9_%EC%84%9C%EB%B2%84)
 2. [mozilla](https://developer.mozilla.org/ko/docs/Learn/Common_questions/What_is_a_web_server)
 3. [Web Server와 WAS](https://coding-factory.tistory.com/741)