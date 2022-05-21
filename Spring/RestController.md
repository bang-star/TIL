# RestController

## 1. @RestController란?
- 스프링프레임워크 4.x 버전 이상부터 사용가능한 어노테이션으로 @Controller에 @ResponseBody가 결합된 어노테이션입니다.
- 컨트롤러 클래스에 @RestController를 붙이면, 컨트롤러 클래스 하위 메서드에 @ResponseBody 어노테이션을 붙이지 않아도 문자열과 JSON 등을 전송할 수 있습니다.

<br />
<hr />
<br />

## 2. @Controller와 @RestController 차이점
 - @RestController는 Spring MVC Controller에 @ResponseBody가 추가된 것입니다.
 따라서 @Controller와 달리 @RestController는 컨트롤러 클래스의 각 메서드마다 @ResponseBody를 추가할 필요가 없어졌습니다.

<br />
<hr />
<br />

## 3. @RestController를 사용하여 문자열을 전송하는 방법

<br />

```Java
    @RestController
    @RequestMapping("/hello/*")
    public class RestController{
        @RequestMapping("/test")
        public String test(){
            return "test";
        }
    }
```

## 4. @RestController를 사용하여 map을 전송하는 방법

<br />

```Java

    @RestController
    @RequestMapping("/hello/*")
    public class RestController{

        @RequestMapping("/test")
        public HashMap<String, Object> test(){
            HashMap<String, Object> hashMap = new HashMap<String, Object>();

            hashMap.put("name", "john");
            hashMap.put("age", "32");
            hashMap.put("gender", "man");

            return hashMap;
        }
    }

```

<br />
<hr />
<br />

## 참고
- [스프링 @RestController란](https://doctorson0309.tistory.com/664)