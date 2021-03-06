# Programming Test

## 1. 화이트 박스 검사(White-box testing)

  - 소프트웨어 혹은 제품의 내부 구조, 동작을 세밀하게 검사하는 테스트 방식으로, 외부에서 요구사항에 따른 예상 결과 값을 테스트 하는 것과는 다르게 내부 소스 코드를 테스트하는 기법으로 사용자가 들여다 볼 수 없는 구간의 코드 단위를 테스트 한다.

 > 즉, 개발자가 소프트웨어 또는 컴포넌트 등의 로직에 대한 테스트를 수행하기 위해 설계 단계에서 요구된 사항을 확인하는 개발자 관점의 단위테스팅 기법이다.

  - 기법
  1. 문장 검증 - 프로그램의 코드가 전체가 수행되는 검증
  2. 분기 검증 - 프로그램의 로직에 있는 분기를 최소 한번은 실행하게 하는 테스트 방식
  3. 경로 검증 - 각각의 조건들이 개별적으로 참과 거짓이 한 번 실행될 수 있도록 하는 테스트 케이스
  4. 조건 검증 - 조건문의 모든 조건식을 만족하는 경우와 만족하지 않는 경우를 검사한다.

<br />
<hr />
<br />

## 2. 블랙 박스 검사(Black-box testing)
 - 소프트웨어의 내부 구조나 작동 원리를 모르는 상태에서 소프트웨어의 동작을 검사하는 방법.
 - 검사 진행에 있어 해당 소프트웨어의 코드나 내부 구조에 대한 정보는 필요하지 않으며, 특징, 요구 사항 검사를 위해 공개된 설계도 등의 대외적으로 공개된 사항들을 통해 검사를 진행하며, “이 소프트웨어는 무슨 역할이 수행되어야 하는가?”와 같이 소프트웨어의 특징이나 요구사항 등에 초점을 맞춰 검사가 이뤄진다.

 > 즉, 개발자입장이 아닌 사용자 입장에서 소프트웨어 혹은 제품에 대한 요구사항과 결과물이 일치하는지 확인하기 위한 테스트 기법이다

  - 기법

  1. 동등 분할 기법 (Equivalence Partitioning)
  - 입력 데이터에 따른 결과값을 테스트할 때 사용되는 기법으로 입출력 데이터에 따라 다르게 동작하는 기능을 테스트하는 경우에 사용된다.
  - 소프트웨어에서 요구하는 입력 데이터를 그룹화하여 해당 그룹에 속하는 값으로 결과값을 비교한다.
        
        Feature: 성적 관리 기능
        Scenario: 점수에 따른 학점을 계산한다. 
        When: 90점을 입력한다.
        then: A학점이 나온다.

<br />

  2. 경계값 분석 기법(Boundary Value Analy)
  - 경계가 뚜렷한 입력 데이터에 따른 동작을 검사할 때 사용되는 기법으로 입력 조건의 경계에 해당하는 값들에서 에러가 발생할 확률이 높다는 점을 이용하여 검사를 진행한다.

        Feature: 오전/오후 도출 기능
        Scenario: 시간에 따른 오전/오후를 구한다.
        When: 1시를 입력한다.
        then: 오후라는 결과가 나온다.

<br />

  3.  오류 예측 기법(Error Guessing)
  - 각 기능에 대한 제약조건을 위반함으로써 생길 오류들을 추측해 검사해보는 것.
<br />

        Feature: 오전/오후 도출 기능
        Scenario: 시간에 따른 오전/오후를 구한다.
        When: 1시를 입력한다.
        then: 오후라는 결과가 나온다.

<br />

  4. 원인 결과 그래프 기법(Cause Effect Graph)
- 원인-결과 그래프를 통해 요구사항 명세를 입력및 출력 조건 간의 논리적 관계로 표현하고 이를 기반으로 테스트 케이스를 만들어낸다.
- 여러 원인들을 논리적으로 IDENTITY, AND, OR, NOT연산으로 연관지어 결과를 도출할 수 있고, 뿐만아니라 E(exclusive), I(inclusive), O(one and only one), R(requires) 제약 심볼을 적용할 수 있다.

<br />

5. 의사결정 테이블 테스팅
- 논리적 조건이나 상황에서 입력 조건과 결과를 참,거짓으로 표현해 조합을 만들고 테스트를 작성한다. 가령 예를들어 광고 회사에서 화장품을 홍보하기위해 적절한 홍보 타겟을 결정하기 위해 의사 결정표를 만들고 중복되는 내용을 통합하여 해당 표를 가지고 테스트 케이스를 작성한다.

<br />

6. 상태전이 테스팅
- 시스템의 상태가 변화함에 따라 상태가 다른 결과물을 도출할 때 그 과정을 테스트 케이스로 작성한다.

        feature: 방안의 전등을 제어한다.
        case 1: 스위치를 키면 불이 켜져야 한다.
        case 2: 스위치를 끄면 불이 꺼져야 한다.
        case 3: 스위치를 켜지 못했다면, 불은 꺼져있어야 한다.