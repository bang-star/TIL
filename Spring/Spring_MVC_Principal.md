# Spring MVC

## 1. Spring MVC 동작원리

- @Controller 는 스프링 서버 개발자 입장에서는 시작점과 끝점으로 보이지만, 사실 스프링이 뒤에서 많은 부분을 보이지 않게 처리해 주고 있습니다.

![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FCItDV%2FbtrDuwG6Bb3%2FQeeNDL3oVkfs8PsKDjzMm0%2Fimg.png)

1. Client → DispatcherServlet
- 가장 앞 단에서 요청을 받아 FrontController 라고도 불림

2. DispatcherServlet → Controller
- API 를 처리해 줄 Controller 를 찾아 요청을 전달
- Handler mapping 에는 API path 와 Controller 함수가 매칭되어 있음
- Handler mapping에서 어느 Controller 함수로 보내야되는지 찾고, 전달해주는 과정

```
💡 [Sample]
GET /hello/html/dynamic → HomeController 의 helloHtmlFile() 함수
GET /user/login → UserController 의 login() 함수
GET /user/signup → UserController 의 signup() 함수
POST /user/signup → UserController 의 registerUser() 함수
```

- 위 Sample을 통해 함수 이름을 내 마음대로 설정 가능했던 이유를 알 수 있다.
- Controller 에서 요청하는 Request 의 정보 ('Model') 전달(DispatcherServlet 에서 Controller로)
- 클라이언트로 부터 받은 정보를 해당 메소드 Controller로 전달해주는 것도 DispatcherServlet이 담당한다.

```Java
@Controller public class ItemSearchController {
     @GetMapping("/api/search")
     @ResponseBody
     public List<ItemDto> getItems(@RequestParam String query) { // ... }
}
```

- Controller → DispathcerServlet
    - Controller 가 Client 으로 받은 API 요청을 처리
    - 'Model' 정보와 'View' 정보를 DispatcherServlet 으로 전달
    - Model과 View를 거치지 않는 경우도 있는데, @responsebody를 하는 경우는 전달이 되지 않는다.

- DispatcherServlet → Client
    - ViewResolver 통해 View 에 Model 을 적용(View에 Model를 적용시켜 보낸다 - 템플릿 엔진이 하는 역할)
    - View 를 Client 에게 응답으로 전달

## 2. Controller 와 HTTP Request 메시지
![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbFHdpG%2FbtrDpO3qblq%2FKSSX5b4NFklWYwmDtbmI6K%2Fimg.png)

1. GET과 POST
GET은 URL 요청 안에 값을 넣어 전송한다면,
POST는 URL에 있는 것을 감추어 Body를 통해 전송한다.

2. Pathvariable과 RequestParam
Pathvariable은 생략하면 안되지만, RequestParam은 생략해도 매칭된다.
명시적으로 작성하는 것을 추천

3. RequestParam과 ModelAttribute
- 입력 값으로 2-3개를 받는다면 그냥 작성해도 되지만 만약 데이터 10개 이상 등 많은 데이터를 가져온다면 파라미터에 다 작성해야하지만, Model을 통해서 객체로 받게 되면 객체에 자동으로 값을 넣어준다.
- 주의할 점은 Setter는 필수적으로 들어가야한다

4. ModelAttribute 와 RequestBody
- ModelAttribute는 String 형식으로 데이터가 들어왔다면,
RequestBody는 JSON형식으로 들어온 데이터를 세팅할때 사용한다.