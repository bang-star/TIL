# [SpringBoot] - Intellj + Maven + Querydsl 오류

  - 현상 : target에 q 클래스 생성 오류
    
    ```
    com.mysema.codegen.model.Type
    ```

## 문제 발생 지점

  - Querydsl과 Qdomain을 사용하기 위해서 의존성+플러그인을 주입한다.

    ```xml
    <!-- https://mvnrepository.com/artifact/com.querydsl/querydsl-apt -->
    <dependency>
        <groupId>com.querydsl</groupId>
        <artifactId>querydsl-apt</artifactId>
        <version>5.0.0</version>
        <scope>provided</scope>
    </dependency>
    <dependency>
        <groupId>com.querydsl</groupId>
        <artifactId>querydsl-jpa</artifactId>
        <version>5.0.0</version>
    </dependency>
    ```

  - Qdomain 플러그인 추가

    ```XML
    <!-- ADDED FOR Querydsl -->
    <plugin>
        <groupId>com.mysema.maven</groupId>
        <artifactId>apt-maven-plugin</artifactId>
        <version>1.1.3</version>
        <executions>
            <execution>
                <goals>
                    <goal>process</goal>
                </goals>
                <configuration>
                    <outputDirectory>target/generated-sources/java</outputDirectory>
                    <processor>com.querydsl.apt.jpa.JPAAnnotationProcessor</processor>
                </configuration>
            </execution>
        </executions>
    </plugin>
    ```

 - Qdomain 플러그인을 넣어줬기 때문에 Q클래스들이 만들어져야 하지만, 만들어지지 않는다.

## 해결 방법

  1. file - project structure - modules에서 sources 설정하기 (실패)

  2. maven - clean - Run Maven Build - compile (실패)

  3. 의존성, 플러그인 수정(실패)

  4. 버전 주석 처리(성공)
    
        ```XML
        <dependency>
            <groupId>com.querydsl</groupId>
            <artifactId>querydsl-jpa</artifactId>
        </dependency>
        <dependency>
            <groupId>com.querydsl</groupId>
            <artifactId>querydsl-apt</artifactId>
        </dependency>
        ```

## 참고 
  
  - [ueryDSL Q Class 생성 안될 때](https://velog.io/@yulhee741/JPA-QueryDSL-Q-Class-%EC%83%9D%EC%84%B1-%EC%95%88%EB%90%A0-%EB%95%8C)

  - [Querydsl을 통한 동적 SQL 처리법](https://djunnni.gitbook.io/springboot/appendix/querydsl)

  - [compileQuerydsl 오류](https://www.inflearn.com/questions/355723)