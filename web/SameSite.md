# SameSite

## 쿠키란

- 쿠키는 브라우저에 데이터를 저장하기 위한 수단 중 하나이다.
- 브라우저에서 서버로 요청을 전송할 때 그 요청에 대한 응답에 Set-Cookie 헤더가 포함되어있는 경우, 브라우저는 Set-Cookie에 있는 데이터를 저장하고, 이 저장된 데이터를 쿠기라고 부른다.

<img src="https://seob.dev/static/97337a4841fcf5fa74cb24976247cb0d/d68e4/set-cookie-header.png">

> 위와 같이 서버의 응답에 Set-Cookie 헤더가 포함된 경우, normal이라는 이름의 쿠키에 yes라는 값이 저장된다.

- 저장된 쿠키는 브라우저에서 서버로 요청을 보낼 때, Cookie라는 헤더에 같이 전송됩니다. 서버에서는 헤더를 읽어서 유저를 식별하는 등 필요한 구현을 할 수 있다.

<img src="https://seob.dev/static/68ff614820ca22386dbfee5239c760ea/8f77f/cookie-header.png">

> 브라우저에서 보내는 요청에 포함된 "Cookie"헤더

- 쿠키는 이렇게 동작하기 때문에 주로 서버에서 사용자를 식별하기 위한 수단으로 사용되어 왔습니다.
- 쿠키가 만들어진 목적 자체가 이런 일을 하는 것이기 하다.
- Set-cookie 헤더로 세션ID를 넣어둔 뒤에, 이 후 요청부터 전송될 Cookie 헤더의 세션 ID를 읽어 어떤 사용자가 보낸 요청인지 판단하는 식으로 사용된다.

<br />
<hr />
<br />

## 쿠키에 대한 Domain 설정

<img src="https://seob.dev/static/11828a4ba17f8324156b25c26a4a0599/3cb0f/set-cookie-with-domain.png">

- 쿠키가 유효한 사이트를 명시하기 위해 쿠키에 도메인을 설정할 수 있습니다.
- 도메인이 설정된 쿠키는 해당 도메인에서만 유효한 쿠키가 된다.
- normal 쿠키는 localhost를 대상으로 쿠기가 설정되었기 때문에, localhost를 대상으로 한 요청에만 normal 쿠키가 전송됩니다.
- 쿠키에 별도로 명시된 도메인이 없다면 기본값으로 쿠키를 보낸 서버의 도메인으로 설정됩니다.

<br />
<hr />
<br />

## 퍼스트 파티 쿠키와 서드 파티 쿠키

- 설정된 도메인을 기준으로 퍼스트 파티 쿠키(First-party cookies)와 서드 파티 쿠키(Third-party cookies)가 나뉘어 진다.

```
aaa.co.kr에 접속한 상태에서 example.com이 제공하는 이미지인 example.com/image.png를 사용하고 있다고 했을 때
이 경우 사용자는 aaa.co.kr에 접속해 있지만, 브라우저에서는 example.com/image.png로 요청을 보낼 것 입니다. 

이때 사용자가 example.com에 대한 쿠키를 가지고 있다면, 해당 쿠키가 example.com을 운영하는 서버로 같이 전송됩니다. 
이때 전송되는 쿠키를 서드 파티 쿠키라고 부른다.

즉, 서드 파티 쿠키는 사용자가 접속한 페이지와 다른 도메인으로 전송하는 쿠키를 말한다.

퍼스트 파티 쿠키는 사용자가 접속한 페이지와 같은 도메인으로 전송되는 쿠키를 의미한다.
같은 쿠키라도 사용자가 접속한 페이지에 따라 퍼스트 파티 쿠키로도 부를 수 있고, 서드 파티 쿠키로도 부를 수 있다.
```

<br />
<hr />
<br />

## 쿠키와 CSRF 문제

- 쿠키에 별도로 설정을 가하지 않는다면, 크롬을 제외한 브라우저들은 모든 HTTP 요청에 대해서 쿠키를 전송한다.
- 요청에는 HTML 문서 요청, HTML 문서에 포함된 이미지 요청, XHR 혹은 Form을 이용한 HTTP 요청등 모든 요청이 포함됩니다.

- CSRF(Cross Site Request Forgery)는 이 문제를 노린 공격입니다. 
    
    1. 공격대상 사이트는 쿠키로 사용자 인증을 수행
    2. 피해자는 공격 대상 사이트에 이미 로그인 되어있어서 브라우저에 쿠키가 있는 상태.
    3. 공격자는 피해자에게 그럴듯한 사이트 링크를 전송하고 누르게 함. (공격대상 사이트와 다른 도메인)
    4. 링크를 누르면 HTML 문서가 열리는데, 이 문서는 공격 대상 사이트에 HTTP 요청을 보냄.
    5. 이 요청에는 쿠키가 포함(서드 파티 쿠키)되어 있으므로 공격자가 유도한 동작을 실행할 수 있음.
    

> (스포 주의!) SameSite는 이 문제를 해결하기 위해 탄생한 기술입니다.

<br />
<hr />
<br />

## SameSite 쿠키

- SameSite 쿠키는 서드 파티 쿠키의 보안적 문제를 해결하기 위해 만들어진 기술이다.
- 크로스 사이트(Cross-site)로 전송하는 요청의 경우 쿠키의 전송에 제한을 두도록 한다.
- SameSite 쿠키의 정책으로 None, Lax, Strict 세 가지 종류를 선택할 수 있고, 각각 동작하는 방식이 다릅니다.
    
        1. None
        - SameSite 가 탄생하기 전 쿠키와 동작하는 방식이 같습니다. None으로 설정된 쿠키의 경우 크로스 사이트 요청의 경우에도 항상 전송됩니다. 
        즉, 서드 파티 쿠키도 전송됩니다. 따라서, 보안적으로도 SameSite 적용을 하지 않은 쿠키와 마찬가지로 문제가 있는 방식입니다.
        
        2. Strict
        - 가장 보수적인 정책입니다. Strict로 설정된 쿠키는 크로스 사이트 요청에는 항상 전송되지 않습니다. 
        즉, 서드 파티 쿠키는 전송되지 않고, 퍼스트 파티 쿠키만 전송됩니다.
    
        3. Lax
        - Strict에 비해 상대적으로 느슨한 정책입니다. Lax로 설정된 경우, 대체로 서드 파티 쿠키는 전송되지 않지만, 몇 가지 예외적인 요청에는 전송됩니다.

<br />
<hr />
<br />

## Lax 쿠키가 전송되는 경우

- The Chromium Projects 의 SameSite 속성을 소개한 게시물을 보면 다음과 같이 Lax 정책을 설명합니다.

> A cookie with "SameSite=Lax" will be sent with a same-site request, or a cross-site top-level navigation with a "safe" HTTP method.

- 같은 웹 사이트일 때는 (당연히) 전송된다는 것이고, 이 외에는 Top Level Navigation(웹 페이지 이동)과, "안전한" HTTP 메서드 요청의 경우 전송된다는 것입니다.

- Top Level Navigation에는 
    1. 유저가 링크(a태그)를 클릭
    2. window.location.replace 등으로 인해 자동으로 이뤄지는 이동
    3. 302 리다이렉트를 이용한 이동이 포함됩니다. 

- 하지만 iframe이나 img를 문서에 삽입함으로서 발생하는 HTTP 요청은 "Navigation"이라고 할 수 없으니 Lax 쿠키가 전송되지 않고, iframe 안에서 페이지를 이동하는 경우는 "Top Level"이라고 할 수 없으므로 Lax 쿠키는 전송되지 않습니다.

- "안전하지 않은" POST나 DELETE 같은 요청의 경우, Lax 쿠키는 전송되지 않습니다. 
- GET처럼 서버의 서버의 상태를 바꾸지 않을 거라고 기대되는 요청에는 Lax 쿠키가 전송됩니다.
- 이 모든 내용은 서드 파티 쿠키에 한하는 것이고, 퍼스트 파티 쿠키는 Lax나 Strict여도 전송됩니다.

<br />
<hr />
<br />

## 브라우저의 SameSite 구현

### Lax by default
- 크롬은 SameSite를 가장 적극적으로 적용하고 있는 브라우저입니다. 원래 SameSite를 명시하지 않은 쿠키는 SameSite가 None으로 동작했지만, 2020년 2월 4일 크롬 80 버전이 배포되면서 SameSite의 기본값이 Lax로 변경되었고, 이 변경사항은 운영되고 있는 웹 서비스들에게 많은 영향을 미쳤다.

<br />

### Secure 필수 정책
- SameSite 속성으로 None을 사용하려면 반드시 해당 쿠키는 Secure 쿠키여야 합니다. 
- Secure 쿠키는 HTTPS가 적용된 요청에만 전송되는 쿠키입니다. 

<br />
<hr />
<br />

## 참조
1. [SameSite cookies - HTTP | MDN](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Set-Cookie/SameSite)