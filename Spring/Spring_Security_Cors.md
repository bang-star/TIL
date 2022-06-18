# Spring Security Cors

- CORS에 대한 자세히 이야기는 하지 않을 것이다. 이미 이전에 포스팅하였기 때문에 간단히 설명하고 넘어갈 것이다.
- CORS는 다른 출처의 자원을 공유할 수 있도록 설정하는 권한 체제를 의미한다.

- 참고 : [CORS](https://github.com/bang-star/TIL/blob/main/backend/CORS.md)

## Spring Security CORS

<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FmgjtP%2Fbtq0VofncN3%2Fml0OckGYYZvdSF76zROsv0%2Fimg.png">


- configure 메소드를 통해 HttpSecurity에서 cors를 활성화시키고, cors 설정 클래스를 빈으로 등록해주면 api 서버는 브라우저의 preflight 요청에 적절한 헤더를 추가한 response를 응답할 것이다.

<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fb7aeC1%2Fbtq6LPLVoRZ%2F3UDLkVjPRrJbQvyEJGqRK1%2Fimg.png">

- 위 코드는 Security filters에 추가한 CorsFilter를 확인할 수 있다.
- 설정한 processor를 이용해 요청의 유효성을 검증하고 지금 요청이 preflight라면 요청을 끝내는처리를 해준다. 
