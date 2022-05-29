# Compare Servlet with Controller

## 1. Servlet
> “자바 서블릿(Java Servlet)은 자바를 사용하여 웹페이지를 동적으로 생성하는 서버측 프로그램 혹은 그 사양을 말하며, 흔히 “서블릿”이라 불린다.”
- 자바를 사용하여 웹페이지를 동적으로 생성하는 서버 측 프로그램 혹은 그 사양을 말함


## 2. Controller
- 스프링 서버 개발자 입장에서는 시작점과 끝점으로 보이지만, 사실 스프링이 사용자의 요청 (Request)과 응답 (Response)을 처리해 주고 있습니다.

![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FpqRyX%2FbtrafL6ATqP%2FA6F8ebKrjMOKkKDtzPmzxk%2Fimg.png)

```
나의 생각은 Controller는 Servlet을 업그레이드 시킨 것이라고 보면된다. 
Servlet에서 String to JSON으로 전환하는 작업을 직접 다해줘야했다면, SPring은 다 알아서 해주고, 매칭도 알아서 해준다. Controller의 기능을 뺀 것이 Servlet인 것 같다. 둘다 사용해보면서 Controller를 사용하는 것이 좋은 것 같다.
```