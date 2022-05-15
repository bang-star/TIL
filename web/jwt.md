# JWT

## JWT란 무엇인가
- JWT는 Json Web Token 약자로 모바일이나 웹의 사용자 인증을 위해 Json 포맷을 이용하여 사용자에 대한 속성을 저장하는 Claim 기반의 Web Token이다
- JWT 정보를 request에 담아 사용자의 정보 열람, 수정 등 개인적인 작업 등을 수행할 수 있게 한다.
- JWT는 토큰 자체를 정보로 사용하는 Self-Contained 방식으로 정보를 안전하게 전달한다.

## JWT는 어떤 정보를 담아서 전달할까
- JWT는 세파트로 나누어지고, 각 파트는 '.'으로 구분하여 aaa.bbb.ccc 와 같이 표현됩니다.
- JWT는 URL에서 파라미터로 사용할 수 있도록 URL_Safe 한 Base64URL 인코딩을 사용한다.

```Java
  # 코드 조각
  curl http://127.0.0.1:8000/toktokhan/ -H 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c

  header = eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9
  payload = eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ
  signature = SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c
```

### header
- 토큰의 타입과 해시 암호화 알고리즘으로 구성되어 있습니다.
  * typ: 토큰의 타입을 지정 ex) JWT
  * alg: 알고리즘 방식을 지정하며, 서명(Signature) 및 토큰 검증에 사용 ex) HS256(SHA256) 또는 RSA

```JSON
{
  "typ": "JWT",
  "alg": "HS256"
}
```


### payload
- 토큰에 담을 정보가 들어있습니다. 여기에 담은 정보의 한’조각’을 클레임(claim)이라고 부르고, 이는 Json(Key/Value)의 한쌍으로 이뤄져있습니다. 클레임의 종류는 등록된(registered)클레임, 공개(public)클레임, 비공개(private)클레임 이 존재합니다.

  ```JSON
  {
    "sub": "1234567890", // 등록된 플레임
    "name": "John Doe", // 비공개 플레임
    "iat": 1516239022  // 등록된 플레임
  }
  ```

  1. 등록된 클레임(Registered Claim)
  - 등록된 클레임은 토큰 정보를 표현하기 위해 이미 정해진 종류의 데이터들로, 모두 선택적으로 작성이 가능하며 사용할 것을 권장한다. 
  또한 JWT를 간결하게 하기 위해 key는 모두 길이 3의 String이다. 여기서 subject로는 unique한 값을 사용하는데, 사용자 이메일을 주로 사용한다

    * iss: 토큰 발급자(issuer)
    * sub: 토큰 제목(subject)
    * aud: 토큰 대상자(audience)
    * exp: 토큰 만료 시간(expiration), NumericDate 형식으로 되어 있어야 함 ex) 1480849147370
    * nbf: 토큰 활성 날짜(not before), 이 날이 지나기 전의 토큰은 활성화되지 않음
    * iat: 토큰 발급 시간(issued at), 토큰 발급 이후의 경과 시간을 알 수 있음
    * jti: JWT 토큰 식별자(JWT ID), 중복 방지를 위해 사용하며, 일회용 토큰(Access Token) 등에 사용

  2. 공개 클레임
  - 공개 클레임은 사용자 정의 클레임으로, 공개용 정보를 위해 사용된다. 충돌 방지를 위해 URI 포맷을 이용하며, 예시는 아래와 같다.
  ```JSON
  {
    "https://mangkyu.tistory.com": true

  }
  ```

  3. 비공개 클레임(Private Claim)
  - 비공개 클레임은 사용자 정의 클레임으로, 서버와 클라이언트 사이에 임의로 지정한 정보를 저장한다. 아래의 예시와 같다.
  ```JSON
  {
    "token_type": access 
  }
  ```

### signature
  * 서명(Signature)은 토큰을 인코딩하거나 유효성 검증을 할 때 사용하는 고유한 암호화 코드이다. 
  * 서명(Signature)은 위에서 만든 헤더(Header)와 페이로드(Payload)의 값을 각각 BASE64Url로 인코딩하고, 
  * 인코딩한 값을 비밀 키를 이용해 헤더(Header)에서 정의한 알고리즘으로 해싱을 하고, 이 값을 다시 BASE64Url로 인코딩하여 생성한다.
  * 각 요청시 서명이 확인됩니다. 헤더 또는 페이로드의 정보가 클라이언트에 의해 변경된 경우 서명이 무효화됩니다.
  * 서버 기반 인증 기존의 인증 시스템에서는 서버측에서 유저들의 정보를 세션에 기억하고 있어야 합니다. 
  * 세션을 유지하기 위해서는 여러가지 방법이 사용되는데 메모리/디스크/데이터베이스 시스템에 이를 담곤 합니다. 

  * 토큰 기반 시스템은 stateless하고 유저의 인정 정보를 서버나 세션에 담아두지 않기 때문에 인정정보를 서버에 담아둠으로써 발생하는 많은 문제점들이 해소됩니다.


### jwt의 장점
  1. 무상태(stateless), 확장성이 있다. 기존 서버에 세션을 저장하는 방식에서 서버 여러대를 사용하여 요청을 분산하였다면 어떤 유저가 로그인했을 때 그 유저는 처음 로그인한 서버에만 요청을 내보내도록 설정해야합니다. 하지만 토큰을 사용하면 토큰 값만 알고 있다면 어떤 서버로 요청이 들어가던 상관이 없습니다. 즉, 세션스토리지가 필요없다!
  2. 보안성 쿠키를 전달하지 않아도 되므로 쿠키를 사용함으로써 발생하는 취약점이 사라집니다.
  3. 여러 플랫폼 및 도메인 어플리케이션 규모가 커지면 여러 디바이스를 호환 시키고 더 많은 종류의 서비스를 제공합니다. 토큰을 사용한다면 그 어떤 디바이스에서도 그 어떤 도메인에서도 토큰만 유효하다면 요청이 정상적으로 처리 됩니다.

### jwt의 단점
  1. 길이 claim에 넣는 데이터가 많아질 수록 JWT토큰이 길어집니다. API호출 시 매 호출마다 토큰 데이터를 서버에 전달해야 하는데 길이가 길다는 것은 그만큼 네트워크 대역폭 낭비가 심할 수 있습니다.
  2. 보안 JWT는 기본적으로 Payload에 대한 정보를 암호화 하지 않습니다. 단순히 BASE64로 인코딩만 하기 때문에 중간에 패킷을 가로채거나 기타 방법으로 토큰을 취득했으면 디코딩을 통해 데이터를 볼 수 있습니다. 그래서 JWE(JSON Web Encryption)를 통해 암호화 하거나 중요데이터를 Payload에 넣지 말아야 합니다.
  3. Self-contained: 토큰 자체에 정보를 담고 있으므로 양날의 검이 될 수 있다. 
  4. 토큰 길이: 토큰의 페이로드(Payload)에 3종류의 클레임을 저장하기 때문에, 정보가 많아질수록 토큰의 길이가 늘어나 네트워크에 부하를 줄 수 있다. 
  5. Payload 인코딩: 페이로드(Payload) 자체는 암호화 된 것이 아니라, BASE64Url로 인코딩 된 것이다. 중간에 Payload를 탈취하여 디코딩하면 데이터를 볼 수 있으므로, JWE로 암호화하거나 Payload에 중요 데이터를 넣지 않아야 한다.
  6. Stateless: JWT는 상태를 저장하지 않기 때문에 한번 만들어지면 제어가 불가능하다. 즉, 토큰을 임의로 삭제하는 것이 불가능하므로 토큰 만료 시간을 꼭 넣어주어야 한다. 
  7. Store Token: 토큰은 클라이언트 측에서 관리해야 하기 때문에, 토큰을 저장해야 한다.


### 참조
  [JWT란 무엇인가] : https://tech.toktokhan.dev/2021/04/30/JWT/
  
  [MangKyu's Diary] : https://mangkyu.tistory.com/56 