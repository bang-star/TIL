# MySQL 한글깨짐 에러

 - MySQL의 기본설정은 latin1, latin_swedish_ci 상태이다.

 - 한글을 사용하기 위해서 utf8로 변경해주어야 한다.

 - 해결방법

     1. MySQL이 설치된 디렉토리에 있는 .ini파일을 복사하여 my.ini 파일을 생성한다.

     2. ini파일에 아래 내용을 추가한다.

     ```
     [mysql]
     default-character-set=utf8

     [mysqld]
     character-set-client-handshake=FALSE
     init_connect = "SET collation_connection = utf_general_ci"
     init_connect = "SET NAMES utf8"
     character-set-server= utf8
     collation-server = utf8_general_ci

     [client]
     default-character-set = utf8

     [mysqldump]
     default-character-set = utf8
     ```

     3. 파일 수정 후 서비스 - MySQL을 재가동 시키면 된다.

## 참고 

 1. ![MySQL 한글 에러](https://togll.tistory.com/58)
 2. ![MySQL 워크스테이션 한글에러](https://sowon-dev.github.io/2020/07/01/200702jspi2/)