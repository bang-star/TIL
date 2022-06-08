# JPA Keyword

## Flush
```
프로그래밍 언어에서 Flush는 버퍼에 있는 데이터를 모두 비워버리는 역할을 한다.
JPA에서는 어떤 역할을 할까??
```

- JPA Flush
> 영속성 컨텍스트의 변경 내용을 DB 에 반영하는 것을 의미한다.
```
1. Transaction commit 이 일어날 때 flush가 동작 
2. 쓰기 지연 저장소에 쌓아 놨던 INSERT, UPDATE, DELETE SQL들이 DB에 날라간다.
(주의! 영속성 컨텍스트를 비우는 것이 아니라 영속성 컨텍스트의 변경 사항들과 DB의 상태를 맞추는 작업이다.)
즉, 영속성 컨텍스트의 변경 내용을 DB에 동기화한다.
```

### Flush 동작 과정
1. 변경을 감지한다. (Dirty Checking)
2. 수정된 Entity를 쓰기 지연 SQL 저장소에 등록한다.
3. 쓰기 지연 SQL 저장소의 Query를 DB에 전송한다. (등록, 수정, 삭제 Query)
4. flush가 발생한다고 해서 commit이 이루어지는 것이 아니고 flush 다음에 실제 commit이 일어난다.
4. 플러시가 동작할 수 있는 이유는 데이터베이스 트랜잭션(작업 단위)이라는 개념이 있기 때문이다.
5. 트랜잭션이 시작되고 해당 트랜잭션이 commit 되는 시점 직전에만 동기화 (변경 내용을 날림) 해주면 되기 때문에, 그 사이에서 플러시 매커니즘의 동작이 가능한 것이다.

[참고] JPA는 기본적으로 데이터를 맞추거나 동시성에 관련된 것들은 데이터베이스 트랜잭션에 위임한다.


<br />
<hr />
<br />

## Commit
- 트랜잭션을 begin() 으로 수행한 뒤 commit() 하여 트랜잭션을 종료해야합니다. 커밋을 수행하게 되면 내부적으로 EntityManager 의 flush() 메서드를 호출한 후 트랜잭션을 닫습니다.

### Commit vs Flush 

- flush는 쿼리를 전송하는 역할
- commit은 내부적으로 flush를 수행한 뒤 트랜잭션을 끝내는 역할.
> 즉 flush로 전송된 쿼리는 rollback할 수 있지만 commit은 트랜잭션을 끝내므로 rollback 할 수 없습니다.

<br />
<hr />
<br />

## 참고
[JPA CORE FEATURE]()