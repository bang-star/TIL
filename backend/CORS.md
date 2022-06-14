# CORS

## CORS의 배경

    - 기존 브라우저 정책은 서로 다른 도메인으로부터 리소스가 필요한 경우, 보안상의 이유로 다른 도메인의 리소스를 가져오는 것이 불가능했다(SOP: Single-Origin Policy)
    - 어플리케이션을 개선하고 쉽게 개발하기 위해서 다른 도메인에 요청을 보내는 일은 필연적인데, 이를 해결하고자 등장한 표준 기술이 CORS이다.

<br />
<hr />
<br />


## CORS의 정의

    1. 위키백과
    - CORS(Cross-origin resource sharing)은 교차 출처 자원 공유라고도 한다.
    - CORS는 웹 페이지 상의 제한된 리소스를 최초 자원이 서비스된 도메인 밖의 다른 도메인으로부터 요청할 수 있게 허용하는 구조이다. 
    - 웹페이지는 image, CSS, JS, iframe, 동영상을 자유롭게 내장할 수 있다. 특정한 도메인 간(cross-domain) 요청, 특히 Ajax 요청은 동일-출처 보안 정책에 의해 기본적으로 금지된다.
    - CORS는 교차 출처 요청을 허용하는 것이 안전한지 아닌지를 판별하기 위해 브라우저와 서버가 상호 통신하는 하나의 방법을 정의한다.
    - 순수하게 동일한 출처 요청보다 더 많은 자유와 기능을 허용하지만 단순히 모든 교차 출처 요청을 허용하는 것보다 더 안전하다.
    - CORS의 사양은 원래 W3C 권고안으로 출판되었으나 해당 문서는 obsolete인 상태이다. 
    - 현재 CORS를 정의하면서 활발히 유지보수된 사양한 WHATWG의 Fetch Living Standard이다.


    2. Moziila
    - CORS는 추가 HTTP 헤더를 사용하여, 한 출처에서 실행 중인 웹 애플리케이션이 다른 출처의 선택한 자원에 접근할 수 있는 권한을 부여하도록 브라우저에 알려주는 체제입니다.
    - 웹 애플리케이션은 리소스가 자신의 출처(도메인, 프로토콜, 포트)와 다를 때 교차 출처 HTTP 요청을 실행합니다.


    > 정리하면 CORS란 도메인이 다른 자원에 리소스를 요청할 때 접근 권한을 부여한는 메커니즘이다.
    즉 친구의 물건을 쓰려면 친구가 제한하는 규약안에서 사용해야 하듯, 다른 도메인의 자원을 쓰려면 자원의 주인이 허락한 규약을 지켜야 하는 것이다.(도메인이 의미하는 것은 Resource : 프로토콜(http), 호스트(localhost), 포트(8080))
<br />
<hr />
<br />

## CORS의 동작원리

<br />

<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/c/ca/Flowchart_showing_Simple_and_Preflight_XHR.svg/512px-Flowchart_showing_Simple_and_Preflight_XHR.svg.png">

<br />

    (교차출처 요청 예시)  
    https://domain-a.com 의 프론트 엔드 Javascript 코드가 XMLHttpRequest를 사용하여 https://domain-b.com/data.json을 요청하는 경우, 보안상의 이유로 브라우저는 스크립트에서 시작한 교차 출처 HTTP 요청을 제한합니다. 
    예를 들어, XMLHttpRequest와 Fetch API는 동일 출처 정책을 따릅니다. 
    즉, API를 사용하는 웹 애플리케이션은 자신의 출처와 동일한 리소스만 불러올 수 있으며, 다른 출처의 리소스를 불러오려면 그 출처에서 올바른 CORS 헤더를 포함한 응답을 반환해야 합니다.

<img src="https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS/cors_principle.png">

    CORS 체제는 브라우저와 서버 간의 안전한 교차 출처 요청 및 데이터 전송을 지원합니다.
    최신 브라우저는 XMLHttpRequest 또는 Fecth와 같은 API에서 CORS를 사용하여 교차 출처 HTTP 요청의 위험을 완화합니다.


<br />
<hr />
<br />

## CORS가 발생하는 예시
- Client와 Server라는 SpringBoot 프로제그에서 Fetch 요청을 쓰는 예제이다.

- Server
```Java
@RestController
public class ServerSideController{
    @GetMapping("/server")
    public String message(){
        return "server";
    }
}
```

- Client
```HTML
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>Client - Server</title>
  </head>
  <body>
    <script>
      fetch('http://localhost:8080/server').then(response => {
        alert(response);
      });
    </script>
  </body>
</html>
```

       
    클라이언트 쪽에서는 단순히 index.html에서 서버로 요청을 하도록 설정하였다. 주의할 점은 CORS는 클라이언트가 다른 도메인으로 보내야 하기 때문에, 서로 다른 포트로 설정하였다.(서버는 8080, 클라이언트는 7070)
    
    위와 같이 설정하고 http://localhost:7070으로 접속하면? 아래와 같은 CORS 예외가 발생한다. 
    그러면 하.. 왜 안돼!! 하고 소리치고 있을 사람들이 보인다..

    이는 클라이언트는 [http://localhost:7070] 도메인을 사용하고, 서버는 [http://localhost:8080]을 사용하고 있기 때문에
    다른 도메인에 접근하지 못하도록 예외를 발생시키는 것이다.
    
<img src="https://user-images.githubusercontent.com/49060374/87845166-02a87980-c900-11ea-8737-2b6485e71031.png">

<br />

### 해결책은 무엇일까??

<br />
<hr />
<br />

### 1. @CorssOrigin

- CrossOrgin을 사용하면 다른 도메인의 클라이언트가 나의 서버에 요청 보낸것을 허용하는 것이다.
- CrossOrigin은 허용할 origins이나 methods를 지정할 수 있다.    

```Java
@RestController
public class ServerSideController {

    @CrossOrigin("http://localhost:7070")
    @GetMapping("/server")
    public String message() {
        return "server";
    }
}
```

```Java
@RequestMapping("/somePath")
@CrossOrigin(origins = "*", allowedHeaders = "*")
public class SomeController {
}
```

```Java
@RestController
@RequestMapping("/somePath")
public class SomeController {

    @CrossOrigin(origins="*")
    @RequestMapping(value = "/{something}",method = RequestMethod.DELETE)
    public ResponseEntity<String> delete(@PathVariable Long reservationNo) throws Exception{
    }

}
```
<br />
<hr />
<br />

### 2. Configuration

- 세부적으로 자신의 서버에서 CrossOrigin을 설정하고 싶다면 아래와 같이 Configuration을 추가하는 방법이 있다.
- 이 방법은 Global하게 적용하는 방법입니다.

```Java
@Configuration
public class WebConfig implements WebMvcConfigurer {

    @Override
    public void addCorsMappings(CorsRegistry registry) {
        registry.addMapping("/**")
                .allowedOrigins("*");
    }
}
```

    1. addMapping
    - registry.addMapping을 이용해서 CORS를 적용할 URL 패턴을 정의할 수 있다.
    - 위처럼 "/**" 와일드 카드를 사용할 수 있다.
    - Ant-Style도 지원하면 "/somePath/""/ 와 같이 적용할 수 있다.

    2. allowedOrigins
    - allowdOrigins 메소드를 이요해서 자원 공유를 허락할 Orgin을 지정할 수 있다.
    - 위처럼 '*'로 모든 Origin을 허락할 수 있습니다.
    - 아래와 같이 한번에 여러 Origin을 설정할 수 있습니다.

```Java
@Configuration
public class WebConfig implements WebMvcConfigurer {
    @Override
    public void addCorsMappings(CorsRegistry registry) {
        registry.addMapping("/**")
                .allowedOrigins("http://localhost:8080", "http://localhost:8081");
    }
}
```

    3. allowedMethods
    - allowedMethods를 이용해서 허용할 HTTP method를 지정할 수 있습니다.
    - 아래 처럼 여러개를 지정할 수 있고 마찬가지로 "*"를 이용하여 모든 method를 허용할 수 있습니다.

```Java
@Configuration
public class WebConfig implements WebMvcConfigurer {
    @Override
    public void addCorsMappings(CorsRegistry registry) {
        registry.addMapping("/**")
                .allowedOrigins("*")
                .allowedMethods("GET", "POST");
}
```


    4. maxAge
    - maxAge 메소드를 이용해서 원하는 시간만큼 pre-flight 요청를 캐싱 해둘 수 있습니다.

```Java
@Configuration
public class WebConfig implements WebMvcConfigurer {
    @Override
    public void addCorsMappings(CorsRegistry registry) {
        registry.addMapping("/**")
                .allowedOrigins("*")
                .allowedMethods("GET", "POST")
                .maxAge(3000);
}
```

<br />
<hr />
<br />

## 출처

 1. [위키백과](https://ko.wikipedia.org/wiki/%EA%B5%90%EC%B0%A8_%EC%B6%9C%EC%B2%98_%EB%A6%AC%EC%86%8C%EC%8A%A4_%EA%B3%B5%EC%9C%A0)