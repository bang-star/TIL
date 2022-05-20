# h2 Version Error

> org.h2.jdbc.JdbcSQLSyntaxErrorException: Syntax error in SQL statement


- 다음과 같이 에러가 발생했었다. 강의를 수강하면서 에러가 발생하여 계속해서 찾아보았다. 이유는 버전 차이였다. 

    1. 버전으로 인해서 변경된 것들이 있어서 그렇다.
    2. 에러 요인들이 다양하다고 한다. 그러므로 추가해줄 것이 있다.
    3. application.properties 파일에 spring.datasource.hikari.jdbc-url=~~;에서 MODE=MYSQL을 추가해주면 해결된다.
    
