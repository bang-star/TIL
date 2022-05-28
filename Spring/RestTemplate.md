# RestTemplate

## 1. RestTemplate 이란
- Spring에서 지원하는 객체로 간편하게 Rest 방식 API를 호출할 수 있는 Spring 내장 클래스입니다.
- Spring 3.0부터 지원되었고, json, xml 응답을 모두 받을 수 있습니다.
- Rest API 서비스를 요청 후 응답 받을 수 있도록 설계되어있다.
- HTTP 프로토콜의 메소드(ex. GET, POST, DELETE, PUT)들에 적합한 여러 메소드들을 제공합니다.

※ Spring Framework 5부터는 WebFlux 스택과 함께 Spring은 WebClient 라는 새로운 HTTP 클라이언트를 도입하여 기존의 동기식 API를 제공할 뿐 만 아니라 효율적인 비차단 및 비동기 접근 방식을 지원하여, Spring 5.0 이후 부터는 RestTemplate는 deprecated 되었습니다. (WebClient 사용 지향)

<br />
<hr />
<br />

## 2. RestTemplate의 특징
- Spring 3.0 부터 지원하는 Spring의 HTTP 통신 템플릿
- HTTP 요청 후 JSON, XML, String 과 같은 응답을 받을 수 있는 템플릿
- Blocking I/O 기반의 동기방식을 사용하는 템플릿
- RESTful 형식에 맞추어진 템플릿
- Header, Content-Tpye등을 설정하여 외부 API 호출
- Server to Server 통신에 사용

<br />
<hr />
<br />

## 3. RestTemplate 동작 원리

1. 애플리케이션 내부에서 REST API에 요청하기 위해 RestTemplate의 메서드를 호출한다.
2. RestTemplate은 MessageConverter를 이용해 java object를 request body에 담을 message(JSON etc.)로 변환한다. 메시지 형태는 상황에 따라 다름
3. ClientHttpRequestFactory에서 ClientHttpRequest을 받아와 요청을 전달한다.
4. 실질적으로 ClientHttpRequest가 HTTP 통신으로 요청을 수행한다.
5. RestTemplate이 에러핸들링을 한다.
6. ClientHttpResponse에서 응답 데이터를 가져와 오류가 있으면 처리한다.
7. MessageConverter를 이용해 response body의 message를 java object로 변환한다.
8. 결과를 애플리케이션에 돌려준다.

※ RestTemplate은 통신 과정을 ClientHttpRequestFactory(ClientHttpRequest, ClientHttpResponse)에 위임합니다. ClientHttpRequestFactory의 실체는 HttpURLConnection, Apache HttpComponents, HttpClient와 같은 HTTP Client

