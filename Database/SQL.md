# SQL 

## SQL 이란?
 - Structured Query Language(구조적 질의 언어)의 줄임말로, 관계형 데이터베이스 시스템(RDBMS)에서 자료를 관리 및 처리하기 위해 설계된 언어이다.
 - 1970년대에 IBM에서 최초 개발되었으며 관계형 모델이라는 이론에서 파생된 특징을 가지고 있는데, 현재 SQL의 표준으로 ANSI SQL이 정립되었다.
 - 각 DBMS 프로그램에서 ANSI SQL을 기반으로 개발된 개별 SQL을 사용하여 서로 근소한 차이를 보인다.

<br />
<hr />
<br />

## SQL 문법의 종류
- DDL(Data Definition Language, 데이터 정의 언어)
  
  각 릴레이션을 정의하기 위해 사용하는 언어(CREATE, ALTER, DROP))

- DML(Data Manipulation Language, 데이터 조작 언어)

  데이터를 추가/수정/삭제하기 위한, 즉 데이터 관리 언어(SELECT, INSERT, UPDATE)

- DCL(Data Control Language, 데이터 제어 언어)

  사용자 관리 및 사용자별로 릴레이션 또는 데이터를 관리하고 접근하는 권한을 다루기 위한 언어(GRANT, REVOKE)


<br />
<hr />
<br />

## SQL의 언어적 특성

- 각 프로그래밍 언어가 가진 고유한 특성은 꼭 구별지어 알아두어야 사용할 때 줄일 수 있다.
  
1. SQL은 대소문자를 가리지 않는다.

    단, 서버 환경이나 DBMS 종류에 따라 데이터베이스 또는 필드명에 대해 대소문자를 구분하기도 한다.

2. SQL 명령은 반드시 세미콜론(;)으로 끝나야 한다.
3. 고유의 값은 따옴표('')로 감싸준다.

    ex) SELECT * FROM EMP WHERE NAME = 'James';

4. SQL에서 객체를 나타낼 때는 백틱(``)으로 감싸준다.

    ex) SELECT `COST`, `TYPE` FROM `INVOICE`;

5. 주석은 일종의 도움말로, 주석 처리된 문장은 프로그램에서 동작하지 않는다. 주석은 --를 붙여서 사용

    ex) -- SELECT * FROM EMP;

