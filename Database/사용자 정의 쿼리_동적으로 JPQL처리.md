# 사용자 정의 쿼리 - 동적으로 JPQL 처리

  - 원하는 시점에 원하는 JPQL 등을 생성해서 처리할 때 사용자가 직접 Repository를 조절하는 방식을 이용할 수 있다.

  - 방법
    
    1. 원하는 기능을 별도의 사용자 정의 인터페이스로 설계

        ```Java
        public interface CustomWebBoard {

            public Page<Object[]> getCustomPage(String type, String keyword, Pageable page);  
        }
        ```

    2. 엔티티의 Repository 인터페이스를 설계할 때 사용자 정의 인터페이스 같이 상속하도록 설계

        ```Java
        public interface CustomCrudRepository 
        extends CrudRepository<WebBoard, Long>, CustomWebBoard {
        }
        ```

    3. 엔티티 Repository를 구현하는 클래스 생성한다. 이때에는 반드시 'Repository 이름'+'Impl'로 클래스 이름을 지정한다. 클래스 생성 시에 부모 클래스를 QuerydslRepositorySupport로 지정한다.

    4. Repository 인터페이스 Impl 클래스에 JPQLQuery객체를 이용해서 내용을 작성

        ```Java
        @Log
        public class CustomCrudRepositoryImpl extends QuerydslRepositorySupport implements CustomWebBoard {

            public CustomCrudRepositoryImpl() {
                super(WebBoard.class);
            }

            @Override
            public Page<Object[]> getCustomPage(String type, String keyword, Pageable page) {
                log.info("====================================");
                log.info("TYPE: " + type);
                log.info("KEYWORD: " + keyword);
                log.info("PAGE: " + page);
                log.info("====================================");

                QWebBoard b = QWebBoard.webBoard;
                QWebReply r = QWebReply.webReply;
                
                JPQLQuery<WebBoard> query = from(b);
                
                JPQLQuery<Tuple> tuple = query.select(b.bno, b.title, r.count(), b.writer, b.regdate);
                tuple.leftJoin(r);
                tuple.on( b.bno.eq(r.board.bno) );
                tuple.where(b.bno.gt(0L));
                
                if(type != null){
                    
                    switch (type.toLowerCase()) {
                    case "t":
                        tuple.where(b.title.like("%" + keyword +"%"));
                        break;
                    case "c":
                        tuple.where(b.content.like("%" + keyword +"%"));
                        break;
                    case "w":
                        tuple.where(b.writer.like("%" + keyword +"%"));
                        break;				
                    }
                }
                

                tuple.groupBy(b.bno);
                tuple.orderBy( b.bno.desc());

                tuple.offset(page.getOffset());
                tuple.limit(page.getPageSize());

                List<Tuple> list = tuple.fetch();

                List<Object[]> resultList = new ArrayList<>();

                list.forEach(t -> {
                    resultList.add(t.toArray());
                });

                long total = tuple.fetchCount();

                return new PageImpl<>(resultList, page, total);

            }
        }
        ```

 