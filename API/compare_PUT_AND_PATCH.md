# REST란 무엇인가?

## REST 
- Representational State Transfer의 약자이며, 다음과 같이 구성되어 있다.

- 자원(Resource) : URL
- 행위(Verb) : HTTP Method
- 표현(Representations)
    
    즉, REST는 URI에 자원을 표시하고, HTTP Method를 이용하여 해당 자원의 행위를 규정하여 그 결과를 받는 것을 의미한다.
    
- 보통 CRUD에서 조회 GET, 등록 POST, 수정 PUT, 삭제는 DELETE를 이용한다.

<br />
<hr />
<br />

### PUT과 PATCH의 차이

  1.  **PUT**, which is used to apply partial modifications to a resource
 > 즉,자원의 전체 교체, 자원 교체 시 모든 필드 필요 (사용 예 : 좋아요 버튼 )**


  2. **PATCH,** method requests that the state of the target resource be created or replaced with the state defined by the representation enclosed in the request message payload
    
> 즉,  자원의 부분 교체, 자원 교체 시 일부 필드 필요 (사용 예 : 비밀번호 수정)**
    
<br />

<br />

(예시) User { “name”:”Kim”, “age”:20”}
          PUT → /api/user { “name” : “Lee”, “age” : 21}

          PATCH → /api/user { “age” : 21 }

### 유의점

- PATCH는 우리가 사용하는 대부분의 웹 서버 및 브라우저에서 지원하지 않는다고 한다.
- PUT 요청 시 요청을 일부분만 보낸 경우 나머지는 default 값으로 수정되는 게 원칙이므로, 바뀌지 않는 속성도 다 보내야 한다.
- IE8, PHP, Tomcat, Django 등 많은 곳에서 지원하지 않기 때문에 확인 후 사용해야 한다.


<br />
<hr />
<br />

<참고> 

- [[****[REST API] HTTP Method PUT vs PATCH]****](https://velog.io/@insutance/REST-API-HTTP-Method-PUT-vs-PATCH)
- [[튜나 개발일기]](https://devuna.tistory.com/77)