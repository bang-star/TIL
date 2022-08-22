# Spring DevTools

 - Spring Boot를 개발하면서 매번 재실행 하는 것을 번거롭다. 이를 해결하기 위해 save시 자동으로 재실행해주는 도구가 있는데 그것이 Spring DevTools이다.

 - 설정 과정(기준 IntelliJ)

    1. 의존성 추가
    
        - Gradle
        
            ```Java
            implementation 'org.springframework.boot:spring-boot-devtools:2.6.2'
            ```

        - Maven

            ```Java
            <dependencies>
                <dependency>
                    <groupId>org.springframework.boot</groupId>
                    <artifactId>spring-boot-devtools</artifactId>
                    <optional>true</optional>
                </dependency>
            </dependencies>
            ```

    2. application.properties 설정

        ```Java
        // 각자 사용하는 템플릿엔진에 맞게 바꿔줍니다 (ex. thymeleaf, mustache, handlebars, ...)
        spring.thymeleaf.cache=false
        ```

    3. Intellij 설정

       1. "Preferences - Build, Execution, Deployment - Compiler"에서 "Build project automatically" 체크

       2. "Preferences - Advanced Settings"에서 Compiler - "Allow auto-make to start even if deployed application is currently running" 체크

    4. 브라우저에서 새로고침할 때 캐시 지우고 새로 고치기 (크롬이면 cmd + shift + R)