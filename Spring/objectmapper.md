# ObjectMapper

## ObjectMapper란?
 - JSON 컨텐츠를 Java 객체로 deserialization 하거나 Java 객체를 JSON으로 serialization 할 때 사용하는 Jackson 라이브러리의 클래스
 > JSON 형식을 사용할 때, 응답들을 직렬화하고 요청들을 역직렬화할 떄 사용하는 기술이다.

## 직렬화란?
- Object to String
- 데이터를 전송하거나 저장할 때 바이트 문자열이어야 하기 때문에 객체들을 문자열로 바꾸어 주는 것

## 역직렬화란?
- String to Object
- 데이터가 모두 전송된 이후, 수신측에서 다시 문자열을 기존의 객체로 회복시켜주는 것
- Spring boot의 경우 Spring-boot-start-web에 기본적으로 Jackson 라이브러리가 있어서 Object <-> JSON 간 변환은 자동으로 처리된다.
- @RestController의 경우, 요청과 응답이 내부적으로 직렬화/역직렬화가 되는데 이는 Jackson 라이브러리가 있기 때문이다.

<br />
<hr />
<br />

## 직접 경험하기
### 1. 1단계 클래스 만들기
```Java
@Getter
@ToString
@AllArgsConstructor
@NoArgsConstructor
public class Person {

    private String name;
    private int age;
}
```

### 2. 2단계 - Object to JSON
1. Java 객체를 JSON으로 serialization 하기 위해서는 ObjectMapper의 writeValue() 메서드를 이용한다.

```Java
import java.io.File;
import java.io.IOException;

public class ObjectMapperTest {
    public static void main(String[] args) {
        ObjectMapper objectMapper = new ObjectMapper();

	    // Java Object ->  JSON
        Person person = new Person("test", 11);
        try {
            objectMapper.writeValue(new File("src/person.json"), person);
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

```
(유의사항) JSON으로 직렬화 시킬 클래스에 Getter가 존재해야 한다!
Jackson 라이브러리는 Getter와 Setter를 이용하여 prefix를 잘라내고 맨 앞을 소문자로 만드는 것으로 필드를 식별한다. 그렇기 때문에 만약 직렬화 시킬 클래스에 Getter가 존재하지 않으면 클래스에서 필드를 식별하고 못하고 결국 값을 가져오지 못하여 에러가 발생하게 된다.
```

### 3. 3단계 - JSON to Object
1. JSON 파일을 Java 객체로 deserialization 하기 위해서는 ObjectMapper의 readValue() 메서드를 이용한다.

```Java
    public class ObjectMapperEx {
        public static void main(String[] args) {
            ObjectMapper objectMapper = new ObjectMapper();

            // JSON -> Java Object
            String json = "{\"name\":\"zooneon\",\"age\":25,\"address\":\"seoul\"}";
            try {
                Person deserializedPerson = objectMapper.readValue(json, Person.class);
                System.out.println(deserializedPerson);
            } catch (JsonProcessingException e) {
                e.printStackTrace();
            }
        }
    }
```

```
(유의사항)역직렬화 시킬 클래스(여기서는 Person 클래스)에 JSON을 파싱한 결과를 전달할 생성자가 있어야 한다.

기본 생성자를 이용하였지만 생성자에 Jackson 라이브러리의 @JsonCreator 어노테이션을 쓰는 등 다양한 방법이 있다.
만약 클래스에 적절한 생성자가 없을 경우, InvalidDefinitionException가 발생한다.
```