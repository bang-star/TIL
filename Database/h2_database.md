# H2_Database

## 1. H2 Database란?
 - H2DB는 자바 기반의 오픈소스 관계형 데이터 베이스 관리 시스템(RDBMS )입니다.
 - 서버(Server) 모드와 임베디드(Embedded) 모드의 인메모리 DB 기능을 지원합니다.
 - 디스크 기반 테이블을 또한 생성할 수 있습니다.
 - 브라우저 기반의 콘솔모드를 이용할 수 있으며, 별도의 설치과정이 없고 용량도 2MB(압축버전) 이하로 매우 저용량 입니다. DB자체가 매우 가볍기 때문에 매우 가볍고 빠르며, JDBC API 또한 지원하고 있습니다.
 - SQL 문법은 다른 DBMS들과 마찬가지로 표준 SQL의 대부분이 지원됩니다.


## 2. H2 Database 적용방법
1. src > main > resources > application.properties에 다음과 같이 붙여줍니다.

```JAVA
    spring.h2.console.enabled=true
    spring.datasource.url=jdbc:h2:mem:springcoredb;MODE=MYSQL
```
- MODE를 붙여주지 않으면, user라는 키워드에 테이블 등을 생성하지 못한다. 이유는 h2에서 이미 사용하고 있기 떄문이다.


## 3. H2 형식
1) 기본 URL 형식

        1. 임베디드 로컬 연결 - jdbc:h2:[file:][]
        (예시) jdbc:h2:~/test, jdbc:h2:file:/data/sample, jdbc:h2:C:/data/sampe(이 경우 Windows일 경우에만 한정)
        
        2. 인메모리(비공개) - jdbc:h2:mem

        3. 인메모리(데이터베이스 이름 지정) - jdbc:h2:mem:
        (예시) jdbc:h2:mem:test
        
        4. 원격연결(TCP/IP 사용) - jdbc:h2:tcp://[:]/[]
        (예시) jdbc:h2:tcp://localhsot//test, jdbc:h2:tcp://localhsot:8084//test, jdbc:h2:tcp://localhsot/mem:test
        
        5. 원격(TLS 사용) - jdbc:h2:ssl://:[:]/[]
        (에시) jdbc:h2:ssl://localhost/~/test;

2) 키워드

        - 암호된 파일 사용을 사용할 경우
        Keyword : CIPHER(jdbc:h2:;CIPHER=AES)
        (예시) jdbc:h2:ssl//localhost/
        /test;CIPHER=AES , jdbc:h2:file: (X)
        /test;CIPHER=AES
        
        - 데이터베이스가 이미 존재하는 경우에 데이터베이스를 사용하고 싶을 경우
        keyword : IFEXISTS (jdbc:h2:;IFEXISTS=TRUE)
        (예시) jdbc:h2:file:~/test;IFEXISTS=TRUE
        
        - log 파일 레벨을 설정하고 싶을 경우
        keyword : TRACE_LEVEL_FILE
        (jdbc:h2:;TRACE_LEVEL_FILE=<level 0..3>)
        → 0 : OFF
        → 1 : ERROR
        → 2 : INFO
        → 3 : DEBUG
        (예시) jdbc:h2:file:~/test;TRACE_LEVEL_FILE=3
        
        - 연결할 때 바로 SQL 실행하고 싶은 경우
        keyword: INIT=RUNSCRIPT FROM (jdbc:h2:;INIT=RUNSCRIPT FROM '<sql파일 위치>' )
        (예시) jdbc:h2:file:
        /test;INIT=RUNSCRIPT FROM '
        /create.sql'\;RUNSCRIPT FROM '~/dummy.sql'
        
        - 호환모드 사용하고 싶은 경우
        keywrod: MODE (jdbc:h2:;MODE=)
        (예시) jdbc:h2:~/test;MODE=MYSQL;DATABASE_TO_LOWER=TRUE
        
        - 연결이 끊겼을 시, 자동 재연결을 원하는 경우
        keyword : AUTO_RECONNECT (jdbc:h2:;AUTO_RECONNECT=TRUE)
        (예시) jdbc:h2:tcp://localhost/~/test;AUTO_RECONNECT=TRUE
        (유의사항) 자동 커밋이 활성화 된 경우에만 발생합니다. 만약 자동 커밋이 활성화 되어 있지 않다면, 예외가 발생