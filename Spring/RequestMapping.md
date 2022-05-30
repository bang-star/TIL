# RequestMapping

- 우리는 특정 URI로 요청을 보내면 Controller에서 어떠한 방식으로 처리할지 정의를 하는데, 이때 들어온 요청을 특정 메서드와 매핑하기 위해 사용하는 것이 @RequestMapping이다.

- @RequestMapping에서 가장 많이사용하는 부분은 value와 method이다. 
    
    - value는 요청받을 url을 설정하게 된다.
    - method는 어떤 요청으로 받을지 정의하게 된다.(GET, POST, PUT, DELETE 등)
    - 공통적인 url은 class에 @RequestMapping으로 설정을 해주었다.
    - @GetMapping, @PostMapping, @PutMapping, @DeleteMapping으로 간단하게 생략이 가능해졌다.
    - 뒤에 추가적으로 url을 붙이고 싶다면 @GetMapping, @PostMapping, @PutMapping, @DeleteMapping 에 추가적인 url을 작성하면 된다.

[RequestMapping 사용 전]
```Java
@RestController
public class HelloController {

    @RequestMapping(value = "/hello", method = RequestMethod.GET)
    public String helloGet(...) {
        ...
    }

    @RequestMapping(value = "/hello", method = RequestMethod.POST)
    public String helloPost(...) {
        ...
    }

    @RequestMapping(value = "/hello", method = RequestMethod.PUT)
    public String helloPut(...) {
        ...
    }

    @RequestMapping(value = "/hello", method = RequestMethod.DELETE)
    public String helloDelete(...) {
        ...
    }
}
```

[RequestMapping 사용]
```Java
@RestController
@RequestMapping(value = "/hello")
public class HelloController {

    @GetMapping()
    public String helloGet(...) {
        ...
    }

    @PostMapping()
    public String helloPost(...) {
        ...
    }

    @PutMapping()
    public String helloPut(...) {
        ...
    }

    @DeleteMapping()
    public String helloDelete(...) {
        ...
    }
}
```
