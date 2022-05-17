# Check Overflow

[콜라츠 추측] https://programmers.co.kr/learn/courses/30/lessons/12943

<br />

  > 프로그래머스에 콜라츠 추측을 풀이하면서 오버플로우 문제를 겪었다. 하지만 문제에서 대부분의 테스트 값은 해결하였지만, 5번과 7번 케이스만 계속 실패하여 이유를 알지 못하여 구글링을 통해 문제풀이를 하였는데 어떤 이가 500 -> 450으로 조건을 변경하면 된다고 하여 그대로 문제로 풀이하였다. 그런데 이유는 무엇이었을까?? 

  * 문제의 원인은 Overflow였다. 테스트 케이스 문제를 해결하기 위해 값을 출력하여 확인해보니 int의 범위를 넘는 값이 출력되고 있었다. 그래서 이 문제를 해결하기 위한 방법은 여러가지가 있겠지만 쉽게 선택할 수 있는 방법은 입력 값을 long으로 형 변환하여 값의 범위를 늘리는 방법이다.  

  * 매개변수 입력 받은 int형 n값을 long으로 바꿔주지 않으면, 테스트 3에서 488이라는 결과가 나왔다.
    입력 받은 n값을 int형으로 그대로 사용하면 100번째 근처에서 오버플로우가 나와서, 음수로 한번 바뀌기 때문에 결과 값이 꼬이는 것을 알 게되었다.
   
<br /> 

```Java
public static int solution(int num) {
        int answer = 0;
        long n = Long.valueOf(num);
        while(n!=1) {
            if(n%2==0) {
                n /= 2;                       // int 범위 를 넘어가서
            } else {
                n = 3*n + 1;
            }

            answer++;
            if(answer==500) {
                answer=-1; break;
            }
        }
        return answer;
    }
```
  