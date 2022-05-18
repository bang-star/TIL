# 자바의 대문자 소문자 전환 함수

  - Java에서는 문자열을 대문자 혹은 소문자로 반환하고 싶다면 String 클래스의 toUpperCase()와 toLowerCase()를 사용하면 됩니다. 또한 equalsIgnoreCase()를 사용하여 대소문자 구분없이 문자열을 비교할 수 있습니다.


## toUpperCase() : 소문자 → 대문자
  * 문자열에 대소문자, 숫자가 섞여 있어도 소문자를 대문자로 변경해 줍니다.
``` Java
    String word = "abCDfe"
    word = word.toUpperCase();
    System.out.println(word);       // ABCDFE
```


## toUpperCase() : 소문자 → 대문자
* 문자열에 대소문자, 숫자가 섞여 있어도 대문자를 소문자로 변경해 줍니다.
``` Java
    String word = "abCDfe"
    word = word.toUpperCase();
    System.out.println(word);       // abcdef
```

## equalsIgnoreCase() : 소문자 → 대문자
* 아래와 같이 equalsIgnoreCase를 사용해서 str1, str2가 같을 경우 true, 다를 경우 false를 리턴해서 대소문자 구분 없이 문자열을 비교할 수 있습니다.
``` Java
    String str1 = "ABCDEF"
    String str2 = "abcdef"
    if(str1.equalsIgnoreCase(str2))
        System.out.println("같다")
    else
        System.out.println("다르다."); 
```


<br />
<hr />
<br />

### 참고
* [대소문자, 소문자 변환 및 비교](https://pink-rabbit.tistory.com/9)