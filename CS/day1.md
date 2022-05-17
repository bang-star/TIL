# CS(1일차)

- 항해 2주차에서는 CS 스터디를 팀으로 시작한다.
- 오늘은 1.1 ~ 1.2까지의 범위이다.



## 1부 - 하드웨어

  * 하드웨어는 직접 보고 조작할 수 있는 기기나 장비를 말한다.
  * 컴퓨터 장치는 초기에는 주로 천문 현상이나 행성 또는 별의 위치를 예측하는데 특화된 형태였다.
  * 기원전 100년경에 만들어진 안티키티라 기계도 정교한 천문 계산용 컴퓨터다.
  * 계산자는 존네이피어가 로그의 원리를 설명하고 얼마 지나지 않은 1600년 초에 발명되었다.


  * 오늘날의 컴퓨터와 가장 근접한 모습을 보인 장치는 1800년 경 프랑스에서 조제프 마리 자카르가 발명했다고 한다.
 작카르 직기는 여러 줄의 구멍이 있는 직사각형 모양의 카드를 이용해 직조 패턴을 지정했다.
  즉, 천공 카드에 입력된 명령에 따라 다양한 패턴을 짜도록 '프로그래밍'된 것이다.
  * 직물 생산에 필요한 노동력을 대체하는 기계가 등장하자, 방직ㄷ공들이 일자리를 잃게되면서 사회적 혼란이 발생했다고 한다. 대표적으로는 1811년 ~ 1816년 까지 영국에서 일어난 러다이트 운동은 기계화에 반대하는 폭력 시위였다고 한다.

  * 오늘날과 같은 의미의 컴퓨팅은 영국의 찰스 배비지라는 사람에게서 처음 이루어졌는데, 배비지는 항해술과 천문학에 관심이 많은 과학자였고, 두분야 모두 위치를 계산하는 데 숫자값으로 이루어진 표가 필요하여 그런 표를 만들고 인쇄까지 하려면 직접 산술 연산을 했는데, 지겹기도 하고 실수하기도 쉬었다. 배비지는 수작업을 멈추기 위해 기계적으로 처리하는 장치를 개발하는 데 일생의 많은 시간을 투자했다고 한다. 재정적 후원이 끊기는 등 여러 가지 이유로 그의 포부는 결국 실현되지 못했지만, 설계 방식은 타당했다고 한다.
  * 배비지가 살던 시대의 도구와 재료를 사용하여 그가 만들던 기계 중 하나인 차분 기관의 일부를 현대적으로 구현하기도 했다.

  * 오거스타 에이다 바이런은 세계 최초의 프로그래머로 내가 존경하는 하는 사람 중 한명이다. 배비지는 그녀가 수학을 본격적으로 배우고자신의 계산 장치를 연구할 수 있도록 돕고 격려해주었다. 그녀는 배지지의 해석을 과학적 계산에사용하는 방법을 상세하게 기록했으며, 이 기계가 작곡 같은 비수치적 계산도 할수 있을 것이라고 추측하기도 했다.

<br />
<hr />
<br />

### 1.1 컴퓨터의 논리와 구조
  * "완성된 장치가 범용 컴퓨터 기계가 되려면 산술 연산, 기억-저장,제어 운영자와의 연결을 담당하는 특정 주요 기관을 포함해야 한다"  (1946. 폰노이만, 아서벅스, 허먼 골드스타인)
  * 컴퓨터는 논리적 구조(기능), 물리적 구조로으로 살펴보고 있다. 
  * 이 책에서 컴퓨터의 다양한 OS를 자동차와 비교하고 있는데 인상적이었다. 자동차는 모습이 비슷하고 기본 기능이 동일하지만, 서로 다른 회사들이 비슷하지만 다르게 기능을 만들어서 사용자의 니즈를 충족시키기 위해 만든다는 점을 자동차와 비슷하다고 설명하고 있다.
  * 네트워크 효과를 PC에 OS에서 볼수있다는 점도 설명하였다.
    * 네트워크 효과는 사람들이 A를 더 많이 쓸수록 당신에게도 A의 효용이 더 커지며, 그 효과는 사용자의 수에 대략 비례한다.

<br />  
<hr />
<br />

### 1.2 프로세스 속도와 심작 박동수
  * 컴퓨터를 논리적 또는 기능적 아키텍처로 본다면 프로세서, 주 기억장치, 보조 기억 장치, 다른 다양한 구성 요소가 있으며, 그 중간에 정보를 전달하는 버스라는 여러 개의 전선이 서로 연결된다고 한다.
  * 휴대전화나 태블릿 PC라면 마우스, 키보드, 디스플레이가 화면이라는 하나의 구성요소로 합쳐지는 점과 물리적 위치를 알기 위한 나침반, 가속도계, GPS 수신기 같은 숨은 구성 요소가 추가된다.
  * 이처럼 프로세서, 명령어와 데이터를 담은 메모리의 저장 장치, 입력돠 출력 장치가 이쓴ㄴ 기본 구조는 폰 노이만 아키텍처를 따른다.

  * 프로세스(Processor) 는 컴퓨터의 두뇌에 해당한다. 
    * 프로세스는 산술 연산을 하고, 데이터를 여기저기로 옮기며, 다른 구성 요소의 작업을 제어한다.
    * 프로세서가 수행할 수 있는 기본적인 연산 레퍼토리는 한정되어 있지만, 눈부실 정도로 빠르게 연산을 수행한다.
    * 기존 계산 결과를 바탕으로 다음에 수행할 연산을 결정할 수 있어서, 사용자가 일일이 개입할 필요없이 상당히 독립적으로 작동한다.



  * 코어는 프로세서와 동의어가 된다.
    * 코어는 단독으로도 프로세서가 될 수 있지만, 더 빨리 계산하고자 함께 또는 독립적으로 작동하는 코어를 여러 개 포함해 프로세서로 쓸 수 있다.
    * 프로세서의 속도는 1초에 수행할 수 있는 연산이나 명령어의 개수를 어림잡아 측정한다.
    * 속도 측정 단위 중 하나는 초당 쨰갂 거리는 횟수이다. 초당 한번 뛰거나 째깍꺼리는 것을 1Hz라고 한다.


  * 주 기억 장치(Primary memory)
    * 주 기억 장치는 프로세서가 현재 작업 중인 데이터뿐만 아니라 프로세서가 그 데이터로 무엇을 해야 하는지 알려주는 명령어도 저장한다.
    메모리에 다른 명어를 로드하여 프로세서가 다른 계산을 수행할 수 있게 한다.
    * 주기억 장치를 RAM 즉, 임의 접근 메모리 라고 부르는 이유는 프로세서가 정보에 접근할 떄 메모리에 저장된 위치와 무관하게 같은 속도로 접근할 수 있기 떄문이다. 메모리의 어떤 위치에 무작위로접근하더라도 접근 속도는 거의 비슷하다.
    * 주기억 장치의 에로 비디오 테이트로 영화의 마지막 부분을 보려면 시작부터 전체를 '빨리 감기'해야만 했다. 이러한 방식은 순차적 접근이라고라고 한다. 대부분의 메모리는 휘발성 즉, 전원이 꺼지면 메모리의 내용이 사라지고 현재 활성화된 모든 정보가 없어진다. 

<br />
<hr />

### Comment
  1. 이 책을 읽으면서 1-2학년 때 전공을 맨 처음 배울때가 생각났었다. 그때는 이해보다 암기가 우선이였다. 매일 과제와 시험을  위해 외워야만 했기 때문에 주요 단어와 그에 대한 내용을 암기만 하였다. 지금은 그 내용을 이야기를 통해 읽고 있어 재미있게 느껴졌다.
  전공책에서는 많은 부분들이 딱딱한 부분이 많았는데, 이 책에서는 깊이 있게 말하고 있지는 않지만 예시를 통해 설명하려고 하는 것 같았다.
  2. 1세대 ~ 5세대 컴퓨터를 표로 외웠던 것이 생각나는데 기원전 100년전에도 컴퓨터가 있었다는 것은 처음 알게되었다.(내가 잊고 있던 것일 수 도 있다)
  3. 이 책을 보면서 두가지의 질문을 생각하였다.
  * 첫번 째는 현재의 스마트폰은 미래의 어떤 모습일까? 이전의 기술처럼 사라지고 지기한 유물이될 것인가라는 생각
  * 두번 째는 기술의 발전으로 인한 빅 브라더가 심화되어 사람들의 모든 것을 침해받고 유출되고 있는 현재와 교도소와 다른 것일까? 라는 생각

  
