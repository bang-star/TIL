# Javascript JSON 다루기

## 1. JSON API
  
    JSON은 본래 자바스크립트에서 사용할 목적으로 만들어진 포맷입니다.
    그런데 라이브러리를 사용하면 자바스크립트가 아닌 언어에서도 JSON을 충분히 다룰 수 있어서, JSON을 데이터 교환 목적으로 사용하는 경우가 많습니다.

* 자바스크립트가 제공하는 JSON 관련 메소드
  1. JSON.stringify : 객체 -> JSON
  2. JSON.parse : JSON -> 객체
  
``` Javascript
let student = {
  name: 'John',
  age: 30,
  isAdmin: false,
  courses: ['html', 'css', 'js'],
  wife: null
};
 
let json = JSON.stringify(student);
 
alert(typeof json);         // 문자열이네요!
 
alert(json);                // JSON 타입
```


  - JSON.stringify(student)를 호출하자 Student가 문자열로 바뀌었습니다.
  - 이렇게 변경된 문자열은 JSON으로 인코딩된(JSON-encoded), 직렬화 처리된(serialized), 문자열로 변환된(Stringified), 결집된(marshalled) 객체라고 부릅니다.
  - 객체는 이렇게 문자열로 변환된 후에야 비로소 네트워크를 통해 전송하거나 저장소에 저장할 수 있습니다.

<br />
<hr />
<br />

### Tip
    ! JSON으로 인코딩된 객체는 일반 객체와 다른 특징을 보입니다.
    - 문자열은 큰따옴표로 감싸야 합니다. JSON에선 작은따옴표나 백틱을 사용할 수 없습니다.
    - 객체 프로퍼티 이름은 큰따옴표로 감싸야 합니다.(age:30 -> "age":30으로 변한 것을 통해 확인할 수 있다.)

  * JSON.stringify는 객체뿐만 아니라 원시값에도 적용할 수 있습니다.
    
    - 객체[...], 배열[...], 문자형, 숫자형, 불린형, null
    - JSON은 데이터 교환을 목적으로 만들어진 언어로, 자바스크립트 특유의 객체 프로퍼티는 JSON.stringify가 처리할 수 없습니다.

  * JSON.stringify 호출 시 무시되는 프로퍼티는 아래와 같습니다.

    1. 함수 프로퍼티(메소드)
    2. 심볼형 프로퍼티(키가 심볼인 프로퍼티)
    3. 값이 undefined인 프로퍼티
    ``` Javascript
    let user = {
        sayHi() {               // 함수 무시
            alert("Hello");
        },
        [Symbol("id")]: 123,    // 심볼 무시
        something: undefined    // undefined 무시
    };
        
    alert( JSON.stringify(user) ); // {} (빈 객체가 출력됨)
    ```

  * 중첩 객체도 알아서 문자열로 바꿔줍니다.

    ```Javascript
    let meetup = {
    title: "Conference",
    room: {
        number: 23,
        participants: ["john", "ann"]
    }
    };
    
    alert( JSON.stringify(meetup) );
    /* 객체 전체가 문자열로 변환되었습니다.
    {
        "title":"Conference",
        "room":{"number":23,"participants":["john","ann"]},
    }
    */
    ```

## JSON.stringify

    ```Javascript
        let json = JSON.stringify(value[, replacer, space])
    ```

  * value : 인코딩 하려는 값
  * replacer : JSON으로 인코딩 하길 원하는 프로퍼티가 담긴 배열, 또는 매핑 함수 function(key, value)
  * space : 서식 변경 목적으로 사용할 공백 문자 수

  ```Javascript
        let rabbit = {
        name : 'tori',
        color : 'white',
        size : null,
        participants: [{name: "John"}, {name: "Alice"}],
        birthDate : new Date(), 
        jump : () => { // 함수는 스트링화 안됨.
            return 100;
        }
        }
 
 
        let json = JSON.stringify(rabbit);
        //{"name":"tori","color":"white","size":null,"participants":[{"name":"John"},{"name":"Alice"}],"birthDate":"2021-08-03T02:29:57.992Z"}
  ```

### Replacer 
    - replacer 인자에 배열을 주면, 배열값이 허용할 프로퍼티로 해석되어 추가합니다. 즉, 이것만 반환하라는 의미
    - 만약 replacer 값이 없거나 null이면, 모든 값이 반환됩니다.
    
``` Javascript
    // 두번 째 인자로 콜백함수를 넣어주면, 객체를 순회하며 리턴값을 반환한다.
    json = JSON.stringify(rabbit, (key, value) => {
        console.log(`key : ${key}, value = ${value}`);
        return value;
    })

    /*
        key : , value : [object Object]
        key : name, value : tori
        key : color, value : white
        key : size, value : null
        key : participants, value : [object Object],[object Object]
        key : 0, value : [object Object] >> 내장객체까지 순회한다.
        key : name, value : John
        key : 1, value : [object Object]
        key : name, value : Alice
        key : birthDate, value : 2021-08-03T02:29:57.992Z
        key : jump, value : () => { // 함수는 스트링화 안됨.
                return 100;
            }
    */
```

  * 🔥 replacer라는 함수명에 유래하듯이, 조건을 걸어 커스텀 값을 리턴하면, 데이터를 말대로 replace 할수 있습니다.
    
    ```Javascript
        json = JSON.stringify(rabbit, (key, value) => {
            return key === 'name' ? 'fuck you' : value; 
        })
        //{"name":"fuck you","color":"white","size":null,"participants":[{"name":"fuck you"},{"name":"fuck you"}],"birthDate":"2021-08-03T03:25:26.373Z"}
    ```

### Space
  - 가독성을 높이기 위해 중간에 삽입해 줄 공백 문자 수를 나타내는 인자입니다.
  - space는 가독성을 높이기 위한 용도로 만들어졌기 때문에 단순 전달 목적이라면 space 없이 직렬화하는 편입니다.
  - 예시처럼 space에 2를 넘겨주면 자바스크립트는 중첩 객체를 별도의 줄에 출력해주고 공백 문자 두 개를 써 들여쓰기해 줍니다.
  ```Javascript
  // 세번 째 인자로 \t를 넣어주면 가독성 좋게 출력된다.
    json = JSON.stringify(rabbit, null, 2); // 3번째 인자를 쓰기위해서, replacer를 null로 처리한다.
    /*
    {
    "name": "tori",
    "color": "white",
    "size": null,
    "participants": [
        {
        "name": "John"
        },
        {
        "name": "Alice"
        }
    ],
    "birthDate": "2021-08-03T03:25:26.373Z"
    }
    */
  ```

### toJSON
  - toString을 사용해 객체를 문자형으로 변환시키는 것처럼,
  - 객체에 toJSON이라는 메서드가 구현되어 있으면 객체를 JSON으로 바꿀 수 있습니다.
  - JSON.stringify는 이런 경우를 감지하고 toJSON을 자동으로 호출해줍니다.

  ```Javascript
    var date = new Date();
    date; // Tue Aug 03 2021 12:43:15 GMT+0900 (한국 표준시)
    date.toJSON(); // "2021-08-03T03:43:15.472Z"
  ```

  ```Javascript
  json = JSON.stringify(rabbit, ['birthDate']);
  // birthDate는 객체이지만, 내장된 toJSON()이 자동으로 호출되서 스트링화됨
  //{"birthDate":"2021-08-03T03:25:26.373Z"}
  ```

  * 직접 toJSON메소드를 만들어서 조작 할 수도 있습니다.

  ```Javascript
    let room = {
    number: 23,
    name: "hotel",
    toJSON() {
        return 9999;
    }
    };
    
    let meetup = {
    title: "Conference",
    room
    };
    
    console.log( JSON.stringify(room) ); // 9999
    console.log( JSON.stringify(meetup) ); // {"title":"Conference","room":9999}
  ```

  * JSON.stringify는 객체에 toJSON 메서드가 있으면 이를 자동으로 호출해줍니다.

<br />
<hr />
<br />

### JSON.parse
```Javascript
    let value = JSON.parse(str,[reviver]);
```
  * str : JSON형식의 문자열
  * reviver : 모든 (key, value)쌍을 대상으로 호출되는 function(key, value) 형태의 함수로 값을 변경시킬 수 있습니다.

```Javascript
    let rabbit = {
        name : 'tori',
        color : 'white',
        size : null,
        participants: [{name: "John"}, {name: "Alice"}],
        birthDate : new Date(), 
        jump : () => { // 함수는 스트링화 안됨.
            return 100;
        }
    }
    
    let json = JSON.stringify(rabbit);
    
    let obj = JSON.parse(json);
    // {name: "tori", color: "white", size: null, participants: Array(2), birthDate: "2021-08-03T04:00:06.965Z"}
```

  * 꼭 JSON타입이 아니더라도, 문자열 타입의 데이터가 있다면 이 역시 변환이 가능합니다.

  ```Javascript
    // 문자열로 변환된 배열
    let numbers = "[0, 1, 2, 3]";
    numbers = JSON.parse(numbers);
    numbers[1]; // 1
    
    let userData = '{ "name": "John", "age": 35, "isAdmin": false, "friends": [0,1,2,3] }';
    let user = JSON.parse(userData);
    alert( user.friends[1] ); // 1
  ```

  * 다만, JSON포맷에 반드시 따라야합니다. Ex) 문자열은 '가 아닌"로 감싸야 합니다.
  ```Javascript
    let json = `{
      name: "John",                     // 실수 1: 프로퍼티 이름을 큰따옴표로 감싸지 않았습니다.
      "surname": 'Smith',               // 실수 2: 프로퍼티 값은 큰따옴표로 감싸야 하는데, 작은따옴표로 감쌌습니다.
      'isAdmin': false                  // 실수 3: 프로퍼티 키는 큰따옴표로 감싸야 하는데, 작은따옴표로 감쌌습니다.
      "birthday": new Date(2000, 2, 3), // 실수 4: "new"를 사용할 수 없습니다. 순수한 값(bare value)만 사용할 수 있습니다.
      "friends": [0,1,2,3]              // 이 프로퍼티는 괜찮습니다.
    }`;
  ```

### Reviver
  * 함수명에서 유추할 수 있듯이, 객체로 변환하면 자체 내장함수나 심볼 등을 사용 할 수 있으니, 이를 복구, 소생 시킨다는 기능을 가지고 있습니다.
  * 당연한 말이지만 rabbit객체에서 JSON으로 변환하고 이를 다시 obj 객체로 변환할때 함수 jump는 이미 걸러진지 오래입니다. new Date()도 마찬가지입니다.
  * JSON변환 과정에서 객체가 이미 문자열로 변환됬으니, getDate메서드가 존재 할리가 없습니다.

<br />

  ```Javascript
    let obj = JSON.parse(json); 
    rabbit.jump(); // 100
    obj.jump(); // Error! 
    rabbit.birthDate.getDate(); //3
    obj.birthDate.getDate(); // Error!
  ```

<br />

  * 이럴때 reviver를 사용해서 이 key값은 객체로 복구한다라고 조건을 명시해 리턴 하면 됩니다.
  * 참고로 이 방식은 중첩 객체에도 적용할 수 있습니다.

  ```Javascript
    let json = JSON.stringify(rabbit);
    let obj = JSON.parse(json, (key, value) => {
        return key === 'birthDate' ? new Date(value) : value;
    });
    
    obj.birthDate.getDate(); // 3
  ```

<br />
<hr />
<br />

## 참조

  1. [JSON과 메소드](https://ko.javascript.info/json)