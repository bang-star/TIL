# 안전한 패스워드 저장

> "보안 시스템은 가장 약한 연결 고리만큼만 강하다."

  - 보안 시스템의 안전성은 '강한 부분이 얼마나 강한가'보다는 '약한 부분이 얼마나 약한가'에 따라 좌우된다.

    - 2012년 6월 세계 최대 비즈니스 전문 소셜 네트워크 서비스(SNS) LinkedIn은 사용자 데이터 해킹 사고로 650만 명의 아이디와 패스워드 정보가 유출된 후 집단 소송을 당했다. 취약한 암호화 알고리즘인 SHA-1을 사용했다는 것이 그 이유였다. 보안 시스템의 한 부분인 암호화 알고리즘으로 어떤 알고리즘을 선택했는지도 보안의 책임을 다했는지 판단할 때 중요한 요소이다.

<br />
<hr />
<br />

## 단방향 해시 함수

  - 보통 프로그래머는 아래의 두 가지 중 한가지로 사용자의 패스워드를 저장한다.

    - 단순한 텍스트(plain text)

        단순 텍스트로 패스워드를 저장하는 것은 범죄를 저지르는 것이나 다름없다.

    - 단방향 해시 함수(one-way hash function)의 다이제스트(digest)

         단방향 해시 함수는 수학적인 연산을 통해 원본 메시지를 변환하여 암호화된 메시지인 다이제스트를 생성한다. 원본 메시지를 알면 암호화된 메시지를 구하기는 쉽지만 암호화된 메시지로는 원본 메시지를 구할 수 없어야 하며 이를 '단방향성'이라고 한다. 
        
         예를 들어 사용자의 패스워드 "hunter2"라면 문자열을 흔히 사용하는 해시 알고리즘인 SHA-256으로 인코딩하여 아래와 같은 값을 얻을 수 있다.

            f52fbd32b2b3b86ff88ef6c490628285f482af15ddcb29541f94bcf526a3f6c7

         위의 값을 저장하면 사용자의 패스워드를 직접 저장하는 위험을 피할 수 있다. 그리고 사용자가 로그인할 때 패스워드를 입력하면, 이를 해시한 값을 저장된 값과 비교하여 일치 여부를 확인할 수 있다.

         이러한 특징을 avalanche 효과라고 하며, 사용자의 원본 패스워드를 추론하기 어렵게 만드는 중요한 요소이다. 그러나 이것만으로는 패스워드 보안이 충분히 안전하다고 말할 수 없다.

<br />
<hr />
<br />

## 단방향 해시 함수의 문제점

  - 대부분의 웹 사이트에서 SHA-256과 같은 해시 함수를 사용해 패스워드를 암호화해 저장하고 값을 비교하는 것만으로 충분한 암호화 메커니즘을 적용했다고 생각하지만, 실제로는 다음과 같은 두 가지 문제점이 있다.

### 1. 인식 가능성(recognizability)

  - 동일한 메시지가 언제나 동일한 다이제스트를 갖는다면, 공격자가 전처리(pre-computing)된 다이제스트를 가능한 한 많이 확보한 다음 이를 탈취한 다이제스트와 비교해 원본 메시지를 찾아내거나 동일한 효과의 메시지를 찾을 수 있다. 이와 같은 다이제스트 목록을 레인보우 테이블(rainbow table)이라 하고, 이와 같은 공격 방식은 레인보우 공격(rainbow attack)이라 한다. 게다가 다른 사용자의 패스워드가 같으면 다이제스트도 같으므로 한꺼번에 모든 정보가 탈취될 수 있다.

### 2. 속도(speed)

  - 해시 함수는 암호학에서 널리 사용되지만 원래 패스워드를 저장하기 위해서 설계된 것이 아니라 짧은 시간에 데이터를 검색하기 위해 설계된다는 문제가 발생한다. 해시 함수의 빠른 처리 속도로 인해 공격자는 매우 빠른 속도로 임의의 문자열의 다이제스트와 해킹할 대상의 다이제스트를 비교할 수 있다.(MD5를  사용한 경우 일반적인 장비를 이용하여 1초당 56억 개의 다이제스트를 대입할 수 있다.)

  - 이런 방식으로 패스워드를 추측하면 패스워드가 충분히 길거나 복잡하지 않은 경우에는 그리 긴 시간이 걸리지 않는다. 그리고 대부분 사용자의 패스워드는 길거나 복잡하지 않을 뿐 아니라, 동일한 패스워드를 사용하는 경우도 많다.

  - 반면 사용자는 웹 사이트에서 패스워드를 인증하는 데 걸리는 시간에는 민감하지 않다. 사용자가 로그인하기 위해 아이디와 패스워드를 입력하고 확인 버튼을 누르는 과정에 10초가 걸린다고 가정했을 때, 다이제스트를 생성하는 데 0.1초 대신 1초가 소요된다고 해서 크게 신경 쓰는 사람은 많지 않다. 즉, 해시 함수의 빠른 처리 속도는 사용자들보다 공격자들에게 더 큰 편의성을 제공하게 된다.

<br />
<hr />
<br />

## 단방향 해시 함수 보완하기

### 솔팅(salting)

  - 솔트(salt)는 단방향 해시 함수에서 다이제스트를 생성할 떄 추가되는 바이트 단위의 임의의 문자열이다. 원본 메시지에 문자열을 추가하여 다이제스트를 생성하는 것을 솔팅(salting)이라 한다.

    예를 들어 "redfl0wer'에 솔트인 "8zff4fgflgfd93fgdl4fgdgf4mlf45p1"를 추가해 다이제스트를 생성할 수 있다.

    <img src="https://d2.naver.com/content/images/2015/06/helloworld-318732-1.png">

    <br />

    이 방법을 사용하면, 공격자가 "redfl0wer"의 다이제스트를 알아내더라도 솔팅된 다이제스트를 대상으로 패스워드 일치 여부를 확인하기 어렵다. 또한 사용자별로 다른 솔트를 사용한다면 동일한 패스워드를 사용하는 사용자의 다이제스트가 다르게 생성되어 인식 가능성 문제가 크게 개선된다.

    솔트와 패스워드의 다이제스트를 데이터베이스에 저장하고, 사용자가 로그인 할 때 입력한 패스워드를 해시하여 일치 여부를 확인할 수 있다. 이 방법을 사용할 때에는 모든 패스워드가 고유의 솔트를 갖고 솔트의 길이는 32바이트 이상이어야 솔트와 다이제스트를 추측하기 어렵다.

<br />

### 키 스트레칭(key stretching)

  - 입력한 패스워드의 다이제스트를 생성하고, 생성된 다이제스트를 입력 값으로 하여 다이제스트를 생성하고, 또 이를 반복하는 방법으로 다이제스트를 생성할 수도 있다. 이렇게 하면 입력한 패스워드를 동일한 횟수만큼 해시해야만 입력한 패스워드의 일치 여부를 확인할 수있다. 이것이 기본적인 키 스트레칭 과정이다.

  - 잘 설계된 패스워드 저장 시스템에서는 하나의 다이제스트를 생성할 때 어느정도(일반적인 장비에서 0.2초 이상)의 시간이 소요되게 설정한다. 이는 억지 기법 공격(brute-force attack)으로 패스워드를 추측하는 데 많은 시간이 소요되도록 하기 위한 것이다.

  - 최근에는 일반적인 장비로 1초에 50억 개 이상의 다이제스트를 비교할 수 있지만, 키 스트레칭을 적용하여 동일한 장비에서 1초에 5번 정도만 비교할 있게 한다. GPU를 사용하더라도 수백에서 수천 번 정도만 비교할 수 있다. 50억 번과는 비교할 수 없을 정도로 적은 횟수다. 컴퓨터 성능이 더 향상되면 몇 번의 반복을 추가하여 보완할 수 있다.

  - 솔트를 추가한 패스워드에 여러 단계의 해시 함수를 적용하여 다제스트를 생성하는 과정

    <img src="https://d2.naver.com/content/images/2015/06/helloworld-318732-2.png">

    <br />

    솔팅과 키 스트레칭으로 구성된 암호화 시스템을 구현하려고 한다면 이미 검증된 암호화 시스템을 사용할 것을 권장한다. 널리 알려진 검증된 시스템을 사용하면, 암호화 시스템을 잘못 구현해서 발생하는 위험을 피할 수 있다.

    이에 비해 자신만의 암호화 시스템을 구현하는 것은 매우 위험하다. 이 경우 취약점을 확인하기 어렵고, 대부분의 경우 구현된 암호화 시스템을 점검하고 확인하는 사람은 암호화 시스템을 구현한 당사자 한 명이다. 만약 구현한 암호화 시스템에 취약점이 있다면, 많은 사람들이 사용할수록 그만큼 많은 사람들이 피해를 입게 된다. 이런 취약점이 내포된 시스템은 여러 차례 발견되었고, 이와 같은 시스템을 사용한 프로그램들이 여러 해 동안 BSD나 Linux에서 사용되어 왔다.

<br />
<hr />
<br />

## Adaptive Key Derivation Functions

  - adaptive key derivation function은 다이제스트를 생성할 때 솔팅과 키 스트레칭을 반복하며 솔트와 패스워드 외에도 입력 값을 추가하여 공격자가 쉽게 다이제스트를 유추할 수 없도록 하고 보안의 강도를 선택할 수 있다.

    이 함수들은 GPU와 같은 장비를 이용한 병렬화를 어렵게 하는 기능을 제공한다. 이와 같은 기능은 프로그래밍 언어에서 제공하는 라이브러리만으로는 구현하기 어렵다.

<br />

### PBKDF2

  - 가장 많이 사용되는 key drivation function은 PBKDF2(Password-Based Key Derivation Function)이다. 해시 함수의 컨테이너인 PBKDF2는 솔트를 적용한 후 해시 함수의 반복 횟수를 임의로 선택할 수 있다. PBKDF2는 아주 가볍고 구현하기 쉬우며, SHA와 같이 검증된 해시 함수만을 사용한다.

    PBKDF2의 기본 파라미터는 다음과 같은 5개 파라미터다.

        DIGEST = PBKDF2(PRF, Password, Salt, c, DLen)


    - PRF : 난수(예: HMAC)

    - Password : 패스워드

    - Salt : 암호화 솔트

    - c : 원하는 iteration 반복 수

    - Dlen : 원하는 다이제스트 길이

  - PBKDF2는 NIST(National Institute of Standards and Technology, 미국표준기술연구소)에 의해서 승인된 알고리즘이고, 미국 정부 시스템에서도 사용자의 패스워드의 암호화된 다이제스트를 생성할 때 사용한다.

<br />

### bcrypt

  - bcrypt는 애초부터 패스워드 저장을 목적으로 설계되었다. Niels Provos와 David Mzeieres가 1999년 발표했고 현재까지 사용되는 가장 강력한 해시 메커니즘 중 하나이다. bcrypt는 보안에 집착하기로 유명한 OpenBSD에서 기본 암호 인증 메커니즘으로 사용되고 있고 미래에 PBKDF2보다 더 경쟁력이 있다고 여겨진다.

    bcrypt에서 "work factor"인자는 하나의 해시 다이제스트를 생성하는 데 얼마만큼의 처리 과정을 수행할지 결정한다. "work factor"를 조정하는 것만으로 간단하게 시스템의 보안성을 높일 수 있다.

    다만 PBKDF2나 scrypt와는 달리 bcrypt는 입력 값으로 72 bytes character를 사용해야 하는 제약이 있다.

    ```Java
    // Sample code for jBCrypt is a Java
    // gensalt is work factor and the default is 10
    String hashed = BCrypt.hashpw(password, BCrypt.gensalt(11));

    // Check that an unencrypted password matches one that has
    // previously been hashed
    if (BCrypt.checkpw(candidate, hashed))  
        System.out.println("It matches");
    else  
        System.out.println("It does not match");
    ```

<br />

### scrypt

  - scrypt는 PBKDF2와 유사한 adaptive key derivation function이며 Colin Percival이 2012년 9월 17일 설계했다. scrypt는 다이제스트를 생성할 때 메모리 오버헤드를 갖도록 설계되어, 억지 기법 공격(brute-force attack)을 시도할 때 병렬화 처리가 매우 어렵다. 따라서 PBKDF2보다 안전하다고 평가되며 미래에 bcrypt에 비해 더 경쟁력이 있다고 여겨진다. scrypt는 보안에 아주 민감한 사용자들을 위한 백업 솔루션을 제공하는 Tarsnap에서도 사용하고 있다. 또한 scrypt는 여러 프로그래밍 언어의 라이브러리로 제공받을 수 있다.

    scrypt의 파라미터는 다음과 같은 6개 파라미터다.

        DIGEST = scrypt(Password, Salt, N, r, p, DLen)  

     - Password : 패스워드

     - Salt : 암호학 솔트

     - N : CPU 비용

     - r : 메모리 비용

     - p : 병렬화(parallelization)

     - DLen : 원하는 다이제스트 길이

<br />
<hr />
<br />

## More Info

  - MD5, SHA-1, SHA-256, SHA-512 등의 해시 함수는 메시지 인증과 무결성 체크를 위한 것이다. 이것을 패스워드 인증을 위해 사용하면 앞에서 말한 인식 가능성과 빠른 처리 속도에 기인하는 취약점이 존재한다.

    이를 해결하기 위해서  key derivation function을 사용하는 것을 권장한다.

    ISO-27001의 보안 규정을 준수하고, 서드파티의 라이브러리에 의존하지 않으면서 사용자 패스워드의 다이제스트를 생성하려면 PBKDF2-HMAC-SHA-256/SHA-512을 사용하면 된다.

매우 강력한 패스워드 다이제스트를 생성하는 시스템을 쉽게 구현하고 싶다면 bcrypt를 사용하는 것이 좋다. 대부분의 프로그래밍 언어에서 라이브러리를 사용할 수 있고, 검색 엔진에서 "bcrypt <프로그래밍 언어>"로 검색하면 쉽게 예제를 구할 수 있다.

구현하려는 시스템이 매우 민감한 정보를 다루고, 보안 시스템을 구현하는 데 많은 비용을 투자할 수 있다면 scrypt를 사용하면 된다.

이와 함께 패스워드 보안을 위해 더 쉽게 취할 수 있는 조치가 있다.

패스워드 다이제스트의 강도는 결국 패스워드 자체의 길이와 유일성 같은 엔트로피에 의해서 결정된다. 따라서 사용자가 안전한 패스워드를 설정하도록 패스워드 정책을 설정하는 것이 매우 중요하다. 사용자가 모두 다른 패스워드를 사용하도록 강제하는 것이 최상이겠지만 현실적으로는 어렵기 때문에 최대한 긴 패스워드를 사용하도록 권장해야 한다.

<br />
<hr />
<br />

## 참조

  - [안전한 패스워드 저장](https://d2.naver.com/helloworld/318732)