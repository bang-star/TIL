# HTTP Message

![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbBwMxe%2FbtrDnq7AXak%2FvXUep3kEwTcNnasnOfgZm0%2Fimg.png)

- Client 와 Server 간 Request, Response 는 HTTP 메시지 규약을 따름
HTTP 메시지는 웹 서비스 개발자(백엔드, 프론트 개발자)에게 매우 중요한 내용!!
스프링 MVC 이해를 위한 필수 내용만 학습
 

## 1. HTTP 메시지

1. 메시지 구조
    - 시작줄 (start line)
    - Response 에선 '상태줄 (status line)' 이라고 부름
    - 헤더 (headers)
    - 본문 (body)
 
<br />

2. Request 메시지

    1. 시작줄: API 요청 내용
    => HTTP 메소드 + URL +  HTTP 버전

        GET naver.com HTTP/1.1

    2. 헤더 - meta 정보(추가적인 정보)
        - "Content type" 
        - 없음
        - HTML form 태그로 요청 시
        - Content type: application/x-www-form-urlencoded
        - AJAX 요청
        Content type: application/json
 

    3. 본문(Client 에서 보내는 정보)

        - GET 요청 시: (보통) 없음
        - POST 요청 시: (보통) 사용자가 입력한 폼 데이터
        - name=홍길동&age=20
 

3. Response 메시지

- 상태줄: API 요청 결과 (상태 코드, 상태 텍스트)
- HTTP/1.1 404 Not Found => HTTP버전 + 상태코드 + 상태 메시지
- 헤더
    - "Content type" : 내가 보내는 정보에 대한 타입
    - 없음
    - Response 본문 내용이 HTML 인 경우 
        
        - Content type: text/html

    - Response 본문 내용이 JSON 인 경우
        
        - Content type: application/json
    - "Location"
    - Redirect 할 페이지 URL
 
    - Location: <http://localhost:8080/hello.html>
    - 본문
    - HTML
    ```html
    <!DOCTYPE html> 
    <html> 
    <head>
        <title>By @ResponseBody</title>
    </head> 
    <body>
        Hello, Spring 정적 웹 페이지!!
    </body>
    </html>
    ```

    2. JSON
    ```json
    { 
        "name":"홍길동",
        "age": 20
    }
    ```


<HR >
4. Controller 와 HTTP Response 메시지

<br />

![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbbtkJy%2FbtrDj9Golrq%2FXf4U3JYD2u3DBTlz6cjl0K%2Fimg.png)

크게 ResponseBody가 있는 경우와 없는 경우로 나뉘어진다.
1. ResponseBody가 없는 경우 -> Return Type은 String
    1) String 으로 전달할 경우 Templates 엔진은 해당 String 값을 View로 전달하여 해당 String은 View name으로 읽는다. 없을 경우 에러를 발생시킨다.
    2) redirect가 있을 경우, view로 보내지 않고 해당 URL로 이동시켜준다.

2. Reponsebody가 있을 경우
    1) String을 반환해주는 경우 해당 텍스트는 text/html 타입으로 전달된다. 즉, 데이터가 아닌 텍스트로 전달된다.
    2) String외에 클래스 등을 반환해주는 경우, application/json타입으로 전달되는데 이는 Spring이 자동으로 변환해서 보내준다.

(+) 만약 데이터를 매칭시켜서 전달시켜주고 싶은 경우는 Model을 사용하여 전달 가능하다