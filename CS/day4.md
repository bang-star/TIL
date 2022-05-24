# CS(4일차) - 1일 1로그 100일 IT 지식

### 범위 : p.33 ~ 45

<br />

### 1.7 연속과 불연속 
  ```
    "어떤 단위의 기수가 2라면 그 다누이는 이진 숫자, 더불여서 비트(Bit)라고 할 수 있는데, 이는 존 루키가 제안한 단어다" -클로도 섀넌, 1948 
  ```

  1. 연속과 불연속
  - 컴퓨터가 정보를 표현한 방식에 관한 기본 아이디어
    
    1. 컴픂터는 디지털 처리 장치다. 즉, 컴퓨터는 불연속적인 덩어리로 입력받고, 불연속적인 값을 갖는 정보를 저장하고 처리한다. 아날로그 정보는 연속적으로 변한는 값을 뜻한다.

    2. 컴퓨터는 정보를 비트로 표현한다.
    3. 비트는 모여서 더 큰 정보를 표현한다. 숫자, 문자, 단어, 이름 소리, 사진, 영화부터 이러한 정보를 처리하는 프로그램을 구성하는 명령어에 이르기까지 모두 비트가 모여 표현된다.



  2. 아날로그와 디지털
    
    1. 아날로그 
    - 아날로그는 '유사하다'라는 뜻의 analogous와 어원이 같고, 다른 어떤 것이 변함에 따라 연속적으로 변하는 값이라는 개념을 전달한다.

    2. 디지털 시스템은 불연속적인 값을 다루므로 가능한 값의 수가 정해져있다.

    3. 디지털 방식을 사용하는 이유

      첫번째, 컴퓨터 입장에서는 디지털 데이터가 다루기 쉽기 때문이다.
      디지털 데이터는 기존 출처와는 무관하게 다양한 방식으로 저장되고, 전송되고, 처리될수 있다. 
      두번째, 디지털 정보는 불필요하거나 중요하지 아낳은 정보를 버리는 방식으로 압축될 수 있어 네트워크를 통해 전송할 때 효과적이다.
      세번째, 보안과 개인정보 보호를 위해 암호화되고, 다른 데이터와 병합되고, 그대로 복사되고, 인터넷을 통해 어디로든 옮겨지고, 한없이 다양한 장치에 저장될 수 있다.

<br />  
<hr />
<br />

### 1.8 아날로그 정보를 디지털로 바꾸기
  
  1. 이미지 디지털하기
  - 이미지는 아날로그를 디지털 형태로 변화하는 과정을 보여주는 가장 간단한 예다.

    1. 아날로그 카메라
    - 아날로그 카메라는 화학 물질을 입힌 플라스틱 필름에 있는 감광 영역을 피사체에서 오는 빛에 노출하여 영상을 만들어 낸다.
    - 영역마다 서로 다른 색의 빛을 각기 다른 양으로 받아들이고, 받아들인 빛은 필름 내 염료에 영향을 미친다. 
    - 필름은 복잡한 화학 처리 단계를 거쳐 종이 위에 현상되고 인하된다. 이때 색상은 착색 염료의 양에 따라 표시된다.

    2. 디지털카메라
    - 디지털 카메라는 렌즈가 적색, 녹색, 청색 필터 뒤에 놓인 미세한 광검출 소자의 직사각형 배열에 영상의 초점을 맞춘다.
    각 검출 소자는 소자에 들어오는 빛의 양에 비례하는 양으로 전하를 저장한다. 저장된 전하는 수치로 변환된다. 
    - 사진의 디지털 표현은 이렇게 계산되어 빛의 강도를 나타내는 수를 배열한 것이다.
    - 검출 소자가 더 많고 전하가 더 정밀하게 측정될수록 디지털화된 영상은 피사체 원형을 더 정확하게 담아낸다.
    - 센서 배열의 각 요소는 적책, 녹색, 청색 빛의 양을 측정하는 세 개의 검출 소자로 구성된다.
    - 각 요소는 화소라는 뜻에서 픽셀 이라고한다.
    - 예를 들어 영상이 4000x3000 픽셀이라면 1천 2백만 화소 또는 12메가 픽셀이다.
    
  2. 음향 디지털화하기
  - 디지털 정보의 특성이 사회적, 경제적, 법적으로 중대한 영향을 미치기 시작한 첫 번째 분야이다.
  - 바이닐 레코드나 카세트테이프와 달리 디지털 음악은 무제한적으로 복제 가능하다. 
  - 또한 인터넷을 통해 무료로 어디로든 복제 가능하다.
  
  - 소리의 근원인 음원에서 발생한 진동이 공기에 압력 변화를 일으켜 파동의 형태로 전파되어 고막을 진동시키면 신경 활동으로 변화되는데, 뇌에서 이것을 소리로 받아들인다.
  - 1870년대에 토머스 에디슨은 '측음기'를 만들었다. 이 장치는 기압 변동을 왁스 실린더에 있는 가느다란 홈의 패턴으로 변환했고, 나중에 이 패턴을 이용해서 기압 변동을 재현할 수 있었다. 소리를 홈의 패턴으로 변화하는 과정을 '녹음'이라 하고, 패턴의 기압변동을 변환하는 과정을 '재생'이라고 한다.

  - 정식 제도된 CD는 수십년을 버티겠지만, 복제된 CD는 그렇지 않을 수 있다고 한다. 왜냐하면 복제된 CD에서는 시간에 따라 특성이 변할 가능성이 있는 감광 염료가 화학적 변화를 일으키면서 영향을 줄 수 있기 때문이다. 

  - 소리와 영상은사람이 인지할 수 있는 것보다 많은 세부 정보를 담고 있기 떄문에 압축할 수 있다.

  3. 영화 디지털화하기
  - 오늘날 영화는 초당 24프레임의 비율, TV는 초당 25프레임 도는 340프레임의 비율로 이미지를 보여주며, 이는 인간의 눈이 일련의 장면을 연속적인 움직으로 인지할 정도로 충분히 빠른 속도다. 비디오 게임은 일반적으로 초당 60프레임을 사용한다.
  - 영화의 디털 표현은 음향과 영상 요소를 결합하고 동기화한다.
  - 동여상 표현 기술인 MPEG 같은 압축 기술을 사용하면, 저장에 필요한 용량을 줄일 수 있다.

  4. 텍스트 디지털화하기
  - 아스키 코드와 유니코드에 대한 설명을 하고 있다.

<br />
<hr />

### Comment
  1. 어릴 때 게임을 설치하는데 필요한 시간은 30분 가량이 걸렸다. 그리고 필요한 용량도 지금과 비교하면 엄청 작았다. 그런데 지금은 GB용량을 가진 게임들을 설치하는데 몇분이 걸리지 않는다.. 이 것을 되돌아보면 기술의 발전이 엄청난 것 같다.
  2. 삼성이 1억 2천만 화소를 개발했을 때 우연히 사람의 눈을 디지털 카메라의 화소 수로 측정한 것을 보았다. 이때 사람의 눈은 5억 7천 6백만 화소까지 볼수 있다고 하는데 어쩌면 내가 죽기 전에 카메라가 그 성능을 뛰엄넘지 않을까 싶다.
  3. 게임을 하면서 프레임이 떨어지면 못하겠다.. 라는 생각을 하는 경우가 많은데 현재의 게임이 돌아갈 수 있도록 성능이 발전한 것이 더 놀라운 것 같다.
  
