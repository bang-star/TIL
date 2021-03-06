# CS 24일차

- 범위 : CH47, 51

## 47. 자바스크립트는 어떻게 작동할까?

    - 자바스크립트 프로그램은 다른 프로그래밍 언어와 유사한 과정을 거쳐 실행 가능한 형태로 변환되지만, 세부사항은 크게 다르다.

        1. 브라우저가 웹페이지에서 자바스크립트를 발견하면 프로그램의 텍스트를 자바스크립트 컴파일러로 전달한다.
        2. 컴파일러는 프로그램에 에러가 있는지 검사하고, 프로그램을 모형 컴퓨터처럼 만들어 낸 컴퓨터의 어셈블리 언어 명령어로 컴파일한다.
        3. 모형 컴퓨터 같은 시뮬레이터를 실행하여 자바스크립트 프로그램이 수행하기로 되어 있는 모든 기능을 수행한다.
        4. 시뮬레이터와 브라우저는 밀접하게 상호작용한다.


    자바스크립트를 실행하기 위해서는 자바스크립트 엔진이 필요합니다. 자바스크립트는 엔진은 V8, Rhino, SpiderMonkey 등 다양하게 있지만 이 중에서도 가장 대표적인 예는 Google에서 만든 V8 엔진이 있다.

    엔진은 두 가지 구성요소로 구성됩니다. 하나는 Memory Heap이고, 다른 하나는 Call Stack이죠. Memory Heap(메모리 힙)은 메모리 할당이 발생하고, Call Stack(호출 스택)은 코드 실행에 따라 스택이 하나씩 쌓이는 곳입니다.

    자바스크립트를 사용하다 보면 setTimeOut() 같은 수많은 API를 사용하고는 합니다. 이런 API들은 Web API라고 해서 웹 브라우저 혹은 node js 같은 자바스크립트 런타임에서 지원해주는 API입니다. 그래서 어떤 브라우저에서는 지원을 해줄 수도 있고, 안 해 줄 수도 있다.

    그런데 자바스크립트는 아까 위에서 나온 setTimeOut()과 같은 비동기 코드 작성이 가능함에도 불구하고, 자바스크립트 자체에는 비동기 코드를 처리하기 위한 개념을 갖고 있지 않았습니다. 그런데 어떻게 비동기 코드를 처리할 수 있었냐면 바로 Event loop & Callback Queue의 환상의 콜라보레이션으로 가능하게 된 것입니다.

    설명한 Web API와 더불어 웹 브라우저나 런타임에서는 Event loop와 Callback Queue라는 것도 지원해줍니다. 

    V8 엔진의 구조를 간단하게 봤을 때 하나의 Call Stack(호출 스택)과 하나의 Memory Heap(메모리 힙)으로 이루어진 것을 확인할 수 있었습니다. Call Stack은 기본적으로 자바스크립트를 한 줄씩 읽어가며 우리의 코드가 순서대로 돌 수 있도록 보장해주는 데이터 구조입니다. 스택을 사용하기 때문에 후입 선출(LIFO, Last-In-First-Out)의 구조를 갖습니다.

    Call Stack에 쌓이는 하나의 사각형을 스택 프레임(Stack Frame)이라고 하는데, 만약 함수가 실행이 된다면은 스택의 맨 위에 있던 스택 프레임을 가리키는 중이며, 함수의 실행이 끝날 때 해당 스택 프레임을 Call Stack에서 제거하게 됩니다.

## 51. 파이썬은 어떻게 작동할까? 
- 파이썬 프로그램은 다른 프로그래밍 언어와 유사한 방법을 거쳐 실행 가능한 형태로 변환되지만, 세부 사항은 크게 다르다.

        
        명령줄 환경에서 python 명령어를 통해서 직접 실행하든 웹페이지에서 제공하는 서비스를 통해 간접적으로 실행하든, 파이썬을 실행할 때는 프로그램의 텍스트가 파이썬 컴파일러로 전달한다. 
        컴파일러는 프로그램에 에러가 있는지 검사하고, 프로그램을 모형 컴퓨터처럼 만들어 낸 컴퓨터의 어셈블리 언어 명령어로 컴파일한다.
        import문이 있으면 그 라이브러리의 코드도 포함한다. 
        컴파일러는 파이썬 프로그램이 하기로 되어 있는 모든 동작은 수행하고자 가상 머신을 실행한다.
        가상 머신은 키보드나 인터넷에서 데이터를 읽거나화면에 출력을 표시하는 것 같은 작업을 하기 위해 컴퓨터 환경과 상호작용한다.

### 파이썬 동작 원리(Python의 구현체 Cpython)

    python이 C로 구현되어 있다고 알려져있는데 그 구현체가 CPython이다. 가장 처음 만들어진 python의 구현체이고 Python.org 에서 다운 받으면 CPython을 받는 것이다. 다른 구현체들과 비교해서 언급할 때 주로 CPython이라고 표기하는데 Python을 C언어로 구현한 구현체를 의미한다.

    CPython은 인터프리터 이면서 컴파일러 이다. 우리가 작성하는 Python 코드를 bytecode로 컴파일 하고 실행한다. 다시 말해, python 코드를 C언어로 바꾸는 것이 아니라 컴파일하여 bytecode로 바꾸고 그 다음에 interpreter(virtual machine)가 실행한다.

    .py 파일을 실행하면 .pyc 라는 파일이 생성되는데 이것이 CPython이 컴파일한 bytecode가 들어있는 것이다. 그 다음 .pyc를 interpret 하는 것도 CPyton이다.

    dis 라는 패키지를 사용하면 python 코드가 어떻게 bytecode로 변환되는지를 볼 수 있다.

    CPython 인터프리터 실행 중에 단점이 있는데 GIL(global interpreter lock)을 사용한다는 것이다. bytecode를 실행할 때에 여러 thread를 사용할 경우, 전체에 lock 을 걸어서 한번에 단 하나의 thread 만이 python object에 접근하도록 제한한 것이다. 하지만 single thread일 때는 문제가 없고 GIL의 단점을 보안하기 위한 방법들이 존재하고 있어서 GIL로 인한 불편함을 느낄 가능성은 거의 없다고 한다.