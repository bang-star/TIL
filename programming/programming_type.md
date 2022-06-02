# 프로그래밍 종류

> 프로그래밍이란 특정 목적을 달성하기 위해 설계된 알고리즘(algorithm)을 프로그래밍 언어를 사용하여 구체적인 프로그램으로 작성하는 과정

<br />

<img src="https://velog.velcdn.com/images%2Fgillog%2Fpost%2F3b288584-c96c-40ff-a41e-061e6732c31e%2F6_aop%EB%9E%80.jpg">

<br />

## 절차지향 프로그래밍 => 실행순서 중시

- 절차지향 프로그래밍은 물이 흐르듯 위에서 아래로 흐르는 것처럼 한줄씩 처리하는 프로그래밍을 의미한다.
- 대표적인 절차지향언어로는 C언어가 있다.
- 햄버거를 만드는데 빵, 패티, 소스, 양상추, 양파, 피클과 같이 순서가 필요한 경우 적합하다. 
- 사용 분야 : 임베디드 시스템

``` Java
int human1_position = 0;
int human2_position = 0;

human1_position = move(human1_position, 3);
human2_position = move(human2_position, 5);

public int move(int cur, int change){
    return cur + change;
}
```

<br />

<img src="https://velog.velcdn.com/images%2Fikerbm94%2Fpost%2F725afbc4-3918-4850-8f20-a43a5f7108f0%2Fimage.png">

<br />
<hr />
<br />

## 객체지향 프로그래밍 => 종류와 속성 중점

- 객체지향 프로그래밍은 객체라는 기본 단위로 나누고 이들을 상호작용하는 방식이다.
- 대표적인 객체지향 언어로는 Java, Python이 있다.
- 자동차를 만드는데 한 곳에서 부품을 다 만드는 것은 비효율적이므로, 각 부품을 따로따로 만드는 것과 유사하다.
- 사용분야 : 게임

``` Java
public class Human{
    private int pos = 0;

    public Human(){ this.position = 3; }
    public void move(int x) { this.position += x; }
}

Human human1 = new Human();
Human human2 = new Human();
human1.move(3);
human2.move(5);
```

> 객체지향은 절차지향과 반대되는 개념인가요??
- 절대 아니다. 객체지향은 절차지향처럼 '절차'를 따르지만, 객체를 강조하기 위해 붙여진 이름이다.

<br />

<img src="https://velog.velcdn.com/images%2Fikerbm94%2Fpost%2Fb6d0a4ce-3270-48c6-8837-c72b84e74c1d%2Fimage.png">

<br />
<hr />
<br />

## 관점지향 프로그래밍(AOP) => OOP의 보완형
- AOP은 OOP를 대신하는 새로운 개념이 아니라, 기존 OOP를 더욱 보완, 확장하여 OOP를 OOP답게 사용할 수 있도록 도와주는 개념이다.
- AOP은 공통 관심 기능을 분리하여 반복되는 부분을 추출하여 핵심 로직에 영양를 미치지 않고 소스의 중복을 줄이는 방법으로 기존 객체지향 프로그래밍에서 공통 관심 기능을 여러 모듈에서 적용하여 발생하는 중복된 코드 양산의 한계를 극복하기 위해 나오게 되었다.
- 기능의 코드 핵심부를 어수선하게 채우지 않고도 비즈니스 로직에 핵심적이지 않은 동작들을 프로그램에 추가할 수 있게 한다.

- AOP 도입 전까지는 객체의 재사용에도 불구하고 필수적으로 반복되는 코드를 없앨수는 없었다. 예) 트랜잭션, 로그, 권한 체크, 인증, 예외 처리 등

### 1. AOP 주요 Annotaion
<br />
<img src="https://velog.velcdn.com/images%2Fjybin96%2Fpost%2Fbeb395a5-55f6-4730-88fa-39408e03d4c4%2F%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-11-27%20%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB%2011.33.18.png">

<br />
<img src="https://velog.velcdn.com/images%2Fikerbm94%2Fpost%2Fef80903e-04b0-48e5-a7d9-02a8f9d57ca2%2Fimage.png">

<br />
<hr />
<br />

### 참조
 - [절차지향과 객체지향 비교](https://github.com/bang-star/TIL/blob/main/programming/procedural%20and%20object_oriented%20.md)
 - [관점지향 프로그래밍](https://velog.io/@ikerbm94/%EA%B4%80%EC%A0%90-%EC%A7%80%ED%96%A5-%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D-Aspect-Oriented-Programming-AOP)