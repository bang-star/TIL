# JPA

> 다시 JPA에 대해 작성하는 이유는 복습차원이다.

## 강의 시작전
- 내가 알고 있는 JPA는?
    
    1. 내가 알고 있는 JPA는 Java에서 ORM 기술 표준으로 사용하는 인터페이스 모음이다.
    2. Java에서 ORM을 사용하는 가장 대표적인 방법이다.
    3. JPA 하면 생각나는 것은 Hibernate, Spring Data JPA가 있다. 

<br />
<hr />
<br />

## 강의

### 1. ORM(Object-Relational Mapping)
- Object : "객체"지향 언어 (자바, 파이썬)
- Relation : "관계형" 데이터베이스(H2, MySQL)

<br />

- 백엔드 개발자(Backend Developer): 웹 서버를 개발하는 개발자
- DBA (Database Administration): 데이터베이스 관리자. 데이터베이스를 설치, 구성, 관리 등의 일을 맡은 사람

```
질문

1. ORM이 없이 웹 서버 개발은 못 하나요?
> ORM 없이도 충분히 웹 서버 개발 가능   예) AllInOneController 에서 Repository 역할 분리

2. ORM을 만든 이유는 무엇일까?
> ORM 이 없는 환경에서는 백엔드 개발자가 비즈니스 로직 개발보다 SQL 작성에 더 많은 노력을 들여야하기 때문
> SQL 작성은 단순하고 반복적이며, 실수하기 쉽기 때문에 이 문제를 쉽게 해결하기 위한 방법

3. 백엔드 개발자는 DB에 대해 몰라도 될까?
> 아니다. 백엔드 개발자는 DB에 대해 자세히 알고 있어야한다.
  이유는 백엔드 개발자는 DB 테이블 설계, SQL Query 성능 확보 등을 위해 잘 알고 있어야한다.
  한마디로 개발 시 서비스에 집중하지만, 설계 및 최적화를 위해서는 알고 있어야한다.
```

### 2. JPA
- JPA : Java Persistence API 자바 ORM 기술에 대한 표준 명세

<br />

<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FONuAj%2FbtrD8NufYwr%2FO2pkhZKx9fuA7MMrKI7OZ0%2Fimg.png" width=800>

<br />

```
질문

1. JPA 가 없으면? 
(나) 
- JPA가 없다고 개발할 수 없는 것은 아니다. 개발 시 서비스 로직에만 집중할 수 없고, DB 처리를 위한 SQL 처리에 많은 시간을 소요할 뿐이다.
(강의) 
- 직접 SQL문을 작성해서 구현 가능( AllInOneController )
- 실제로 과거엔 JPA없이 웹 서버를 개발한 기업이 많았고, 현재도 유효

2. JPA 사용 트렌드?
- 과거 SQL 매퍼(MyBatis, JdbcTemplate) 위주로 개발  (사실 공공기관에서는 아직도.. 나의바티스)
- 전 세계적으로 JPA 사용 빈도가 급격히 높아졌고 현재는 JPA가 대세

3. Hibernate는 무엇인가요?
- JPA는 표준 명세이고, 이를 실제 구현한 프레임워크 중 사실상 표준에 해당
- 스프링 부트에서 기본적으로 "하이버네이트" 사용 중
```

<br />
<hr />
<br />

## 참고

1. [Spring 심화 4주차 - JPA](https://to-be-a-artist.tistory.com/124)