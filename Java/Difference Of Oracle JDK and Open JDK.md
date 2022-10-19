# Oracle JDK 와 Open JDK의 차이점 비교

  - JDK (Java Development Kit)는 Java 플랫폼 프로그래밍에 사용되는 소프트웨어 개발 환경입니다. 여기에는 개별 런타임이라고하는 완전한 Java Runtime Environment가 포함되어 있습니다.

<br />

## [Oracle JDK](https://www.oracle.com/java/)

JDK (Java Development Kit)는 Java 플랫폼 프로그래밍에 사용되는 소프트웨어 개발 환경입니다.
여기에는 개별 런타임이라고하는 완전한 Java Runtime Environment 가 포함되어 있습니다.
독립형 JRE보다 더 많은 도구와 Java 애플리케이션 개발에 필요한 다른 구성 요소가 포함시켜 JDK를 만들었습니다.
Oracle은 JDK를 사용하여 Java SE (Standard Edition) 개발 키트 (Enterprise Edition 및 Micro Edition 플랫폼도 있음)를 사용할 것을 권장합니다.


<br />

## [Open JDK](http://openjdk.java.net/)

OpenJDK는 Java SE Platform Edition의 무료 오픈 소스 구현입니다.
Sun Microsystems가 2006 년에 시작된 개발의 결과로 2007 년에 처음 출시되었습니다.
중요한 것은 OpenJDK는 7 버전 이후 Java Standard Edition의 공식 레퍼런스 구현이라는 점입니다.
또한 Oracle JDK와 마찬가지로 Open JDK 프로젝트도 6 개월마다 새로운 기능 릴리스를 제공합니다.

<br />

## Oracle JDK VS Open JDK (차이점 비교)

1. 배포 일정 (Release)
    
    - Oracle은 3 년마다 릴리스하고 릴리스에 대한 장기적인 지원을 제공합니다

    - OpenJDK는 6 개월마다 릴리스하고 OpenJDK는 다음 버전이 릴리스 될 때까지만 릴리스에 대한 변경 사항을 지원합니다. 
        
        즉, Open JDK는 계속해서 신규버전이 나옵니다.

2. 라이센스 ( License )
    
    - Oracle JDK는 Oracle Binary Code License Agreement에 따라 라이센스이며, Oracle이 발표 한대로 2019 년 1 월 이후에 출시 된 Oracle Java SE 8의 공개 업데이트 부터 상용 라이선스 없이는 비즈니스, 상업용 또는 생산 용도로 사용할 수 없습니다.

    - OpenJDK에는 GNU GPL(General Public License) 버전 2 이므로 완전히 오픈 소스이며 자유롭게 사용할 수 있습니다.

3. 성능 (Performance)
    
   - 동일한 기반을 사용하므로 실질적인 기술차이는 없습니다. 그러나, 성능에 관해서는 응답성 및 JVM 성능면에서 Oracle JDK가 훨씬 좋습니다. Oracle JDK는 기업 고객에게주는 중요성 때문에 안정성에 더 중점을 둡니다. 반대로 OpenJDK는 릴리스를 더 자주 제공합니다. 이것은 불안정한 요소가 될 수 있습니다.

4. 기능 (Features)
    
   - Oracle 제품에는 Flight Recorder, Java Mission Control 및 Application Class-Data Sharing 기능이 있다. 또한 Oracle에는 더 많은 가비지 수집 옵션과 더 나은 렌더러가 있습니다.
   
   - OpenJDK에는 Font Renderer 기능이 있으며 기능도 빠르고 지속적으로 개선되고 있습니다.

5. 개발 및 인기도
    
    Oracle JDK는 Oracle Corporation에서 완전히 개발 한 반면 OpenJDK는 Oracle, OpenJDK 및 Java Community에서 개발했습니다. 그러나 Red Hat, Azul Systems, IBM, Apple Inc., SAP AG와 같은 일류 기업들도 개발에 적극적으로 참여하고 있습니다.

    이전에는 Oracle JDK가 더 선호되었지만, 최근 Android Studio 또는 IntelliJ IDEA와 같은 도구에서 Java Development Kit를 사용하는 상위 회사들이 OpenJDK 기반 JetBrains 빌드로 전환했습니다. 그리고, 주요 Linux 배포판 (Fedora, Ubuntu, Red Hat Enterprise Linux)은 OpenJDK를 기본 Java SE 구현으로 제공합니다.