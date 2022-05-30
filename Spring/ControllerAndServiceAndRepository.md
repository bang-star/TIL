# Controller, Service, Repositry 역할

## 1. Controller

<br />

![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcJvh29%2FbtrDxoh8Fyr%2FswvPffZfuUF4t8kOzwNG9k%2Fimg.png)

- 클라이언트의 요청을 받음
- 요청에 대한 처리는 서비스에게 전담
- 클라이언트에게 응답

<br />
<hr />
<br />

## 2. Service

<br />

![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FJfzyL%2FbtrDrPH5dMX%2FdKRy66m6FiZCO9tYpDHKH1%2Fimg.png)

- 사용자의 요구사항을 처리 ('비즈니스 로직') 하는 실세 중에 실세!!!
- 현업에서는 서비스 코드가 계속 비대해짐
- DB 정보가 필요할 때는 Repository 에게 요청

<br />
<hr />
<br />

## 3. Repository

<br />

![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FrUwSP%2FbtrDwQzbg15%2F7AIkgpBOskA8pOhoz7AOh0%2Fimg.png)

- DB 관리 (연결, 해제, 자원 관리)
- DB CRUD 작업 처리


<br />
<hr />
<br />

## 4. MVC 구조

<br />

![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fp7DDV%2FbtrDzxkQtvw%2FB25Cp6SsZcWikWL1mDBEPk%2Fimg.png)

