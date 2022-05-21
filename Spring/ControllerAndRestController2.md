# @Controller and @RestController 비교

## 1. 개요
- Spring MVC의 @RestController은 @Controller와 @ResponseBody의 조합입니다.
- Spring 프레임 워크에서 RESTful 웹 서비스를 보다 쉽게 개발할 수 있도록 Spring 4.0에서 추가되었습니다.

- 근본적인 차이점
    - @Controller의 역할은 Model 객체를 만들어 데이터를 담고 View를 찾는 것d이다.

    - @RestController는 단순히 객체만을 반환하고 객체 데이터는 JSON 또는 XML 형식으로 HTTP 응답에 담아서 전송합니다

    - @Controller와 @ResponseBody를 사용하여 만들 수 있지만 이러한 방식은 RESTful 웹서비스의 기본 동작이기 때문에 Spring은 @Controller와 @ResponseBody의 동작을 조합한 @RestController을 도입했습니다.

    - 대부분의 개발자들은 두개의 어노테이션이 아닌 하나의 어노테이션만 선언하고 싶어할 것입니다. 또한, @RestController는 이전 두개보다 의미에 대해서 명확히 나타내고 있습니다.

<br />

``` Java
  @Controller
  @ResponseBody
  public class MVCController{
    logic...
  }

  @RestController
  public class ReftFulController{
    logic...
  }
```

<br />
<hr />
<br />

## 2. Spring에서 @Controller와 @RestController은 무엇인가?

<br />

 - @Controller은 뷰에 표시될 데이터가 있는 Model 객체를 만들고 올바른 뷰를 선택하는 일을 담당합니다. 또한, @ResponseBody를 사용하여 HTTP Response Body에 데이터를 담아 요청을 완료할 수 있습니다.

 - HTTP Response Body에 데이터를 담는 것은 RESTful 웹 서비스에 대한 응답에 매우 유용합니다. 왜냐하면 뷰를 반환하는 대신 데이터를 반환하기 때문입니다.

<br />
<hr />
<br />

## 3. Spring에서 @Controller와 @RestController은 차이점

<br />

  1. @Controller는 클래스를 Spring MVC 컨트롤러로 표시하는데 사용되며, @RestController는 RESTful 웹 서비스에서 사용되는 특수 컨트롤러이며 @Controller + @ResponseBody와 동일합니다.

  2. @RestController는 Spring4.0에서 추가되었지만, @Controller는 Spring이 주석을 지원하기 시작한 이후에 존재하며 공식적으로 Spring 2.5버전에서 추가되었습니다.

  3. @Controller는 @Component 주석이 달려있고, @RestController는 아래와 같이 @Controller와 @ResponseBody 주석이 달린 편의 컨트롤러입니다.

  4. @Controller와 @RestController의 주요 차이점 중 하나는 @RestController을 표시하면 모든 메소드가 뷰 대신 객체로 작성됩니다.

  5. 제가 생각하는 가장큰 차이점은 @RestController을 클래스에 달면 모든 핸들러 메소드에서 @ResponseBody를 사용할 필요가 없다는 것입니다.

<br />

### ※ 일반적인 Spring MVC 처리과정
<br />

![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbXvA4D%2FbtqW4gE9bMH%2FTzOqxMdEnRXTAVqaLre5TK%2Fimg.png)


<br />
<hr />
<br />

## 참고

- [@Controller와 @RestController 차이](https://dncjf64.tistory.com/288)