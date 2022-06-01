# Load Balancer

## 1. 왜 Load Balancer가 필요한가?
<br />
 
 - Client가 한 두명인 경우에는 어떨까요?

<img src="https://nesoy.github.io/assets/posts/20180602/1.png" >

<br />

 - Server는 여유롭게 사용자가 원하는 결과를 응답 해줄 수 있습니다.
 
 <br />
 <hr />
 <br />

## 2. 하지만 Client가 한 두명이 아닌 수천만명이라면 어떨까요?

<br />

<img src="https://nesoy.github.io/assets/posts/20180602/2.png" width=750 >

<br />

- Server는 모든 사람들의 응답을 해주려고 노력하지만 결국엔 지치게 되어 동작을 멈추게 됩니다.

<br />
<hr />
<br />

## 3. 문제를 해결하기 위해서는 어떻게 해야할까요?

- Scale-up : Server가 더 빠르게 동작하기 위해 하드웨어 성능을 올리는 방법.
- Scale-out : 하나의 Server 보다는 여러 대의 Server가 나눠서 일을 하는 방법.

1. Scale-out의 장점은 무엇이 있을까요?

    - 하드웨어 향상하는 비용보다 서버 한대 추가 비용이 더 적습니다.
    - 여러 대의 Server 덕분에 무중단 서비스를 제공할 수 있습니다.

<br />

> 여러 대의 Server에게 균등하게 Traffic을 분산시켜주는 역할을 하는 것이 Load Balancer입니다.

<br />
<hr />
<br />

## 4. 주요 기능은 어떤게 있을까요??

1. NAT(Network Address Translation)
- 사설 IP 주소를 공인 IP 주소로 바꾸는 데 사용하는 통신망의 주소 변조기입니다.

2. Tunneling
- 인터넷상에서 눈에 보이지 않는 통로를 만들어 통신할 수 있게 하는 개념
- 데이터를 캡슐화해서 연결된 상호 간에만 캡슐화된 패킷을 구별해 캡슐화를 해제할 수 있습니다.

3. DSR(Dynamic Source Routing protocol)
- 로드 밸런서 사용 시 서버에서 클라이언트로 되돌아가는 경우 목적지 주소를 스위치의 IP 주소가 아닌 클라이언트의 IP 주소로 전달해서 네트워크 스위치를 거치지 않고 바로 클라이언트를 찾아가는 개념입니다.

<br />

<img src="https://nesoy.github.io/assets/posts/img/2019-07-10-16-39-38.png" width=750 >

<br />

### Architecture

<img src="https://nesoy.github.io/assets/posts/20180602/3.png" width=750 >