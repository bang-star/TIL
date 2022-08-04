# MySQL Archive Setup

  - 공부하고 있는 서적과 최대한 유사하게 진행하기 위해 MySQL 구버전을 설치해야했다. 현재 MySQL은 알집 형식으로 파일을 제공해주고 있었다.

  - zip 아카이브 설치 장점

     - MySQL 삭제 시 레지스트 파일 등의 추가 삭제를 하지 않아도 된다.

  - 설치 방법

     1. 다운받은 zip파일을 압축 해제

     2. 원하는 경로로 파일을 이동

     3. CMD(명령프롬프트)를 관리자 권한으로 실행

     4. CMD에서 파일 경로로 이동

     5. 파일에 bin 폴더로 이동

     6. mysqld --initialize 명령어를 통해 설치

     7. 파일 설치 후 data  폴더가 자동 생성된다.

     8. mysqld --install 명령어를 통해 서비스 설치

     9. net start mysql 명령어를 통해 서비스 시작

        - 명령어를 통해 시작되지 않을 경우 제어판 - 서비스 - MySQL 서비스 시작을 통해 제어 가능

     10. archive으로 설치 시 비밀번호는 임시 난수로 설정되어 있기 때문에 변경해주어야 한다.

     11. 파일 경로/data/컴퓨터이름.err 파일에 root@localhost: 다음 문자열을 변경하여 비밀번호를 설정한다.

     12. bin 폴더에서만 접근이 가능하므로 전역전으로 mysql에 접근하기 위해서는 환경변수 설정이 필요함.

## 참고

  - ![MySQL Archive 설치](https://timeboxstory.tistory.com/68)