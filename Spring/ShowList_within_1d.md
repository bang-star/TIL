# 조회 시간으로부터 24시간 이내 출력하는 방법

## Hint
  1. Spring JPA localtime between
  2. 지금은 LocalDateTime.now(), 전날은 LocalDateTime.now().minusDays(1)

```Java
    LocalDateTime startDatetime = LocalDateTime.of(LocalDate.now().minusDays(1), LocalTime.of(0,0,0));//어제
    LocalDateTime endDatetime = LocalDateTime.of(LocalDate.now(), LocalTime.of(23,59,59));
    List<Memo> memos = memoRepository.findAllByModifiedAtBetweenOrderByModifiedAtDesc(startDatetime,endDatetime);
```

<br />
<hr />
<br />

## findAllByModifiedAtBetweenOrderByModifiedAtDesc(start, end)

   * 해당 메소드를 해석할 필요가 있다.
   * 순서대로 읽어보면 findAll + ByModifiedAtBetween + OrderByModifiedAt + Desc
   * findAll : 전체 다 불러줘라!
   * ByModifiedAtBetween : 수정시간을 사이를 출력해줘!
   * OrderByModifiedAt : 수정시간을 기준으로!
   * Desc : 내림차순(최신 순으로)


<br />
<hr />
<br />


## 참조 

  - [Spring Data JAP](https://docs.spring.io/spring-data/jpa/docs/current/reference/html/#jpa.query-methods)