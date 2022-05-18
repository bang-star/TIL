# Java Locale Class

## 궁금하게 된 이유
 > 문자열을 대문자 또는 소문자로 전환할 때, 입력값으로 Locale.ROOT이라는 값이 항상 들어있었다. 한번은 지우고 작성을 해보았는데, 값이 동일하였다. 그래서 Locale.ROOT가 무슨의미 일까 고민하였다.

<br />

 ## Locale 클래스

  1. 지역의 [언어][나라] 등의 정보를 담고 있는 클래스이다. 
  2. 사용방법은 지역의 [언어][나라] 등의 정보를 담고 있는 클래스이다.

  (1) 인스턴스 생성
      - Locale 클래스는 3가지 생성자를 제공합니다.
      
      1) Public Contructors
      - Locale(String language)
      - Locale(String language, String country)
      - Locale(String language, String country, String variant)

      2) Parameters
      - language 
      : String: An ISO 639 alpha-2 or alpha-3 language code, or a language subtag up to 8 characters in length. See the Locale class description about valid language values.
      
      - country 
      : String: An ISO 3166 alpha-2 country code or a UN M.49 numeric-3 area code. See the Locale class description about valid country values.

      - variant
      : String: Any arbitrary value used to indicate a variation of a Locale. See the Locale class description for the details.

      (요약)
      언어코드는 ISO 639 alpha-2, 나라코드는 ISO 3166-1 alpha-2를 주로 사용한다.

  (2) Locale 클래스 예제
  ``` Java
    Locale locale = new Locale("ko","KR");
    System.out.println("getDisplayLanguage:"+locale.getDisplayLanguage());
    System.out.println("getLanguage:"+locale.getLanguage());
    System.out.println("getDisplayCountry:"+locale.getDisplayCountry());
  ```

  (3) Locale.ROOT은 무슨 의미일까?
  - 오라클 사이트에서는 static 으로 정의해져있다고 한다.
  - Useful constant for the root locale. The root locale is the locale whose language, country, and variant are empty ("") strings. This is regarded as the base locale of all locales, and is used as the language/country neutral locale for the locale sensitive operations.
  - 요약해보면 모든 Locale의 기본으로 간주하여 언어/국가 중립 Locale을 사용한다는 의미이다. 

<br />
<hr />
<br />

### 참조
 1. [Oracle doc](https://docs.oracle.com/javase/7/docs/api/java/util/Locale.html)
