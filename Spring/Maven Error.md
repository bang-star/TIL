# Maven Error

 - Maven 에러가 발생하여 문제 해결을 위한 다양한 수단이 있었다.

     1. JDK가 아닌 JRE로 설정된 경우

     2. 프로젝트의 JDK 설정 문제

     3. Maven 업데이트가 필요한 경우

     4. Maven으로 빌드를 하는 경우

     - 나의 해결방법은 4번이이었다.

 - Maven View에서 Lifecycle - package을 통해 패키지를 설치한 후에 Build하면 된다.

 - setting - Build, Excution, Deployment - BUild Tools - Maven에서 Use Maven wrapper로 되어 Maven home path를 Bundled(Maven 3)로 변경하여 apply