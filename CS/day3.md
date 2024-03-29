# CS(3일차) - 1일 1로그 100일 IT 지식

## 1-9. 0과 1의 세계

  ```
    세상에는 오직 10가지 사람들이 존재한다. 이진수를 이해하는 사람들과 그렇지 앟은 사람들"
  ```

  - 디지털 시스템은 모든 유형의 정보를 숫자 값으로 표현한다.

<br />  

### 비트 

  - 디지털 정보를 표현하는 가장 기본적인 방식

  - 이진 숫자라는 뜻의 binary digit를 축약한 것으로, 1940년대 중반에 통계학자 존 루키가 만들어 냈다.

    - 수소 폭탄의 아버지로 아주 잘 알려진 에드워드 텔러는 '버짓'을 선호했지만, 다행이 이단어는 인기를 얻지 못했다고 한다.

  - '이진'이라는 단어는 두 개의 값을 가졌음을 암시하고 이는 비트에도 그대로 적용된다. 비트는 0 또는 1 중 하나의 값을 사용하고 다른 값은 사용하지 않는 숫자다. 

<br />  

### 2의 거듭제곱과 10의 거듭제곱

  - 컴퓨터 내부에서는 모든 것이 이진수로 처리되므로 크기와 용량 같은 속성이 2의 거듭제곱으로 표현되는 경향이 있다.

    비트가 N개 있다면 2^N개의 값이 가능하므로 2의 거듭제곱을 일정한 값, 가령 2^10 정도까지 알아 두면 편리하다. 

<br />  
<hr />
<br />

## 1-10 비트 모아 데이터
  
### 이진수
    
  - 각 자리의 숫자들을 10대신 2를 기수로 하는 자리값으로 해석하면 어떤 수를 나타낼 수 있다.

<br />

### 바이트

  - 컴퓨터에서 데이터 처리와 메모리 구성의 기본 단위는 8비트로, 이는 하나의 단위로 취급된다. 비트 여덟 개의 모음은 바이트(byte)라고 한다.

  - IBM에 근무하던 컴퓨터 설계자인 베르니 부르홀츠가 1956년에 만든 단어다.

  - 단일 바이트로는 256개의 구별되는 값은 인코딩할 수 있다.

    인코딩된 값은 0과 255 사이의 정수이거나, 7비트 아스키코드 문자 집합(1비트는 다른 용도로 남겨 둔다) 중 하나의 문자이거나, 뭔가 다른 것일 수 있다.

    어떤 바이트는 더 크거나 복잡한 것을 나타내는 큰 그룹의 일부일 때가 많다.

    바이트 두 개는 총 16비트이며, 0에서 2^16 - 1까지, 즉 65,535까지의 값을 나타낼 수 있다.

    바이트 네 개는 32비트로, 아스키코드 문자 네개, 유니코드 문자 두개 또는 2^32 - 1, 즉 43억 개 정도까지의 수를 나타낼 수 있다.

    일련의 바이트로 표현할 수 있는 정보의 종류에는 제한이 없다. 하지만 프로세서 자체에는 정보의 종류별로 몇 개의 특정 그룹들이 정의돼 있고, 각각의 그룹을 처리하기 위한 명령어가 따로 있다.

    이진수는 십진수 형태보다 세 배 이상 길어서 너무 많은 공간을 차지마므로 16진수라는 대안 표기법을 일반적으로 사용한다. 예시) RGB

    십육진수는 네트워크 주제에서 다룰 이더넷 주소에서도 볼 수 있고, 웹에 쓰이는 URL에 특수 문자를 표현하는 데도 사용된다.

    컴퓨터 광고에서 '64'비트라는 문구는 컴퓨터 내부적으로 데이터를 다양한 크기의 덩어리 단위로 조작하는데, 이런 덩어리는 수와 주소를 포함하며, 수로는 32비트와 64비트가 편리하게 사용되고 주소는 메모리상에 있는 정보의 위치다.
    
    여기서 관련된 것은 후자인 주소 속성이다. 30년 전에 16비트 주소 체계에서 32비트 주소 체계로 이행되었고, 32비트면 최대 4GB메모리에 접근하기에 충분한 크기다. 지금은 범용 컴퓨터에서 32bit에서 64bit로 이행이 완료되었다.

  - 비트와 바이트에 대한 논의에서 기억해야 할 가장 중요한 사실은 비트 모음의 의미가 상황에 따라 결정된다는 것이다.

    보이는 것만 가지고 비트가 무엇을 의미하는지 식별할 수는 없다. 바이트 한 개는 참 또는 거짓을 나타내는 비트 한개와 사용되지 않는 비트 일곱 개로 이루어져 있을 수도 있고, 작은 정수 또는 #같은 아스키코드 문자를 저장한 것일 수도 있다.

  - 다른 표기 체계에서 문자 한 개의 일부이거나, 2바이트, 4바이트, 또는 8바이트로 표현되는 큰 수의 일부이거나, 사진이나 음악 작품의 일부분이거나, 프로세서가 실행할 명령어의 일부일 수 있고, 이외에도 다양한 가능성이 있다.

  - 어떤 프로그램의 데이터는 다른 프로그램의 명령어가 되기도 한다. 프로그램이나 앱을 다운로드할 떄 그것은 단지 데이터로서, 무작정 복사되는 비트들이다. 하지만 프로그램을 실행할 때는 그 비트들이 CPU에 의해 처리되면서 명령어로 취급된다.

<br />
<hr />
<br />

## 1-11 요약
  
  - 컴퓨터는 왜 십자수 대신 이진수를 사용할까?

    - 물리적인 장치를 만들 떄 켜짐과 꺼짐이라는 두 가지 상태만 갖도록 하는 것이 두 가지 상태만 갖도록 하는 것이 열 가지 상태로 갖도록 하는 것보다 훨씬 쉽기 때문이다.

    - 상대적인 단순성은 많은 기술에서 활용되고 있다.

      전류(흐름 또는 흐르지 않음), 전압(높음 또는 낮음), 전하(있음 또는 없음), 자성(N극 또는 S극), 빛(밝음 또는 어두움) 등이 있다.

      폰 노이만은 이점을 명확히 인식했고, 1946년 논문에서 다음과 같이 이야기 했다.

      "우리가 설계한 시스템에서 기억의 기본 단위는 2자연스럽게 이진 체계로 맞춰져 있다. 우리가 전햐량의 연속적인 변화를 측정하려고 하지 않기 때문이다"

  - 이진수를 이해하고 관심 가져야 할까?

    - 익숙하지 않은 기수로 이루어진 수를 사용해 보는 것이 친숙한 십진수의 작동 원리를 더 잘 이해하는 데 도움을 주기 때문이다.
      
      이는 일종의 수리 추론에 해당하고 더 나아가 비트의 개수는 필요한 공간, 시간, 또는 복잡도와 일정하게 연관되어 있으므로, 이진수는 또한 중요하다.

    - 컴퓨터는 이해할 가치가 있고, 이진수와 이진 연산은 컴퓨터의 작동에서 핵심 개념이다.

<br />
<hr />
<br />

## 1-12. 프로세서와 계산기의 다른 점

  ```
  "기계에 전달된 명령이 숫자형 코드로 변환되고 기계가 일정한 방식으로 수와 명령을 구분할 수 있다면, 기억 기관은 수와 명령 둘다 저장하는데 사용될 수 있다."
  - 아서 벅스, 허먼 골드스타인, 존 폰 노이만 1946
  ```

  - 프로세서

    - 프로세서 또는 CPU가 컴퓨터의 '두뇌' 역할을 한다.

    - 프로세서에서는 수행할 수 있는 기본 연산들의 레퍼토리가 있다.

      - 산술 연산을 할 수 있어서 계산기처럼 수를 더하고 빼고 곱하고 나눌 수 있다.

      <br />

    - 메모리에서는 연산을 수행할 데이터를 가져오거나 연산 결과를 메모리에 저장할 수 있는데, 계산기에 있는 메모리 기능과 비슷하다.
    
    - 프로세서는 컴퓨터의 나머지 부분을 제어한다. 
    
      즉, 버스로 전송되는 신호를 마우스, 키보드, 디스플레이, 기타 전기적으로 연결된 모든 장치에 대한 입력과 출력을 조직화하고 조정한다.

    - 프로세서가 비록 단순하긴 해도 결정을 내릴 수 있다는 것이다.

      수나 다른 종류의 데이터에 대해 '이 수가 저 수보다 큰지', '이 정보가 저 정보와 동일한지'등 비교를 수행할 수 있고, 그 결과에 기초하여 다음에 무슨 일을 할지 결정할 수 있다.
      
      프로세서가 계산기보다 훨씬 다양한 작업을 수행하지는 못하지만, 계산기와 달리 사람의 개입 없이도 작동할 수 있음을 뜻하기 때문이다.

    - 프로세서는 현재 처리 중인 데이터리를 기반으로 다음에 무슨 일을 할지 결정할 수 있으므로 스스로 전체 시스템을 운영할 수 있다.
      
      기본 연산은 가짓수가 많거나 복잡하지는 않지만, 프로세서는 초당 수십억 번의 연산을 수행할 수 있어서 고도로 정교한 계산이 가능하다.


## Comment

  - bigit가 유행하지 못한것에 왜 글쓴이는 다행이라고 했을까? 

  - IPV4- IPV6로 전환되면 그때는 128bit로 전환되지 않을까라는 생각을 해봤다.

  - 삼성 3진법 반도체라는 글을 본적이 있었다. 2진법에서 3진법으로 변화하면서 얻는 것이 많다고 하는데, 컴퓨터 또한 2진법에서 3진법으로 변화하는 날이 오지 않을까 싶었다.

## Refer

  - [3진 반도체, 삼성의 큰그림 제대로 이해하자](https://insight-up.tistory.com/65)