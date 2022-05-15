# JWT

## JWT란 무엇인가
- JWT는 Json Web Token 약자로 모바일이나 웹의 사용자 인증을 위해 사용하는 암호화된 토큰을 의미한다.
- JWT 정보를 request에 담아 사용자의 정보 열람, 수정 등 개인적인 작업 등을 수행할 수 있게 한다.

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

## reset 
- commit 했던 작업내역을 말 그대로 리셋시키는 것

## stash
- 프로젝트의 변경사항을 임시적으로 보관해둘 때 사용(commit전)