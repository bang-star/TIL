# JPA Core Features

- JPA의 핵심 3요소는 동일성 보장, 쓰기 지연, 변경 감지이다.

## 1. 동일성 보장
> 동일성 보장은 EntityManager 에서 한 객체에 대해 여러 번 꺼내도 꺼낸 객체들은 모두 같다.

- 어떻게 이것이 가능할까?
   
    - 영속성 컨텍스 안에 1차 캐시에서 Transaction Isolation level을 level2(REPEATTABLE_READ) 수준을 사용하기 때문에 데이터베이스가 아닌 애플리케이션 차원에서 보장해줄 수 있는 것이다.
    
    <br />

    ``` Java
    public static void main(String[] args) {
        EntityManagerFactory emf = Persistence.createEntityManagerFactory("hello");
        EntityManager em = emf.createEntityManager();
        EntityTransaction tx = em.getTransaction();

        tx.begin();

        // 동일성 보장 확인
        Member findMember1 = em.find(Member.class, 100L);
        Member findMember2 = em.find(Member.class, 100L);
        System.out.println("result = " + (findMember1 == findMember2)); // "result = true"

        tx.commit();
        em.close();
        emf.close();
    }
    ```

<br />
<hr />
<br />

## 2. 쓰기 지연
> 쓰기 지연은 Entity 를 저장(.persist()) 한다고 해서 데이터베이스에 쿼리가 바로 전송 되는 게 아니라 트랜잭션이 종료되는 시점(commit, 내부적으로는 .flush()) 에 쿼리가 전송되는 것

- 어떻게 이것이 가능할까?
   
    - 영속성 컨텍스트 안에는 '쓰기 지연 SQL 저장소' 와 1차 캐시(Entity 저장소) 가 나뉘어져 있어서 .persist() 시점에는 쿼리를 쓰기 지연 SQL 저장소에 저장해두었다가, 트랜잭션이 종료되는 시점에 쓰기 지연 SQL 저장소에 있는 쿼리들을 데이터베이스로 보내는 구조이기 때문에 가능한 것이다.
    
    <br />


    ```Java
    public static void main(String[] args) {
        EntityManagerFactory emf = Persistence.createEntityManagerFactory("hello");
        EntityManager em = emf.createEntityManager();
        EntityTransaction tx = em.getTransaction();

        tx.begin();

        // 쓰기 지연 확인
        Member member1 = new Member(100L, "지구");
        Member member2 = new Member(200L, "hajs");
        em.persist(member1);
        em.persist(member2);
        System.out.println("==== where is insert query ====");

        tx.commit();
        em.close();
        emf.close();
    }
    ```

<br />
<hr />
<br />

## 3. 변경 감지(dirty checking)
> 변경 감지는 한 트랜잭션 안에서 발생하는 Entity 의 변경사항을 감지하고 update 해주는 것

- 어떻게 이것이 가능할까?
   
    - 영속성 컨텍스트 안에 있는 1차 캐시에는 Entity 가 적재되는 순간을 기록하는 '스냅샷' 공간이 있습니다.이 공간에 저장된 스냅샷과 <> 트랜잭션이 종료 되었을 때의 해당 Entity 스냅샷을 비교하고두 스냅샷에 차이가 있으면 변경된 정보를 update 쿼리로 만들어서 쓰기 지연 SQL 저장소에 적재하는 구조를 가졌기 때문입니다.

    <br />


    ```Java
    public static void main(String[] args) {
        EntityManagerFactory emf = Persistence.createEntityManagerFactory("hello");
        EntityManager em = emf.createEntityManager();
        EntityTransaction tx = em.getTransaction();

        tx.begin();

        // 변경 감지 확인 (dirty checking)
        Member findMember = em.find(Member.class, 100L);
        findMember.setName("지수"); // 지구 -> 지수
        System.out.println("==== where is update query ====");

        tx.commit();
        em.close();
        emf.close();
    }
    ```


<br />
<hr />
<br />

## 생각해보기
1. RDBMS에서 삭제는 보통 auto commit이 되는데, JPA는 어떻게 동작하고 있을까?
> 트랜잭션이 종료되는 시점에 query가 보내진다.

2. 한 트랜잭션 안에서 객체를 생성하고 제거하면, 1차 캐시 내에서만 핸들링이 되는걸까?
> 한 트랜잭션 안에서 객체를 생성하고 제거하는 작업이라도, 각 작업이 이뤄질 때마다 1차 캐시와 쓰기 지연 SQL 저장소에 객체를 저장한다는 것을 알 수 있다. 즉, 영속성 컨텍스트가 '엔티티를 영구 저장하는 환경'이라고 말할 수 있다.
