### 리파지터리 (Repository)

[JPARepository](https://velog.io/@minju0426/JPARepository%EC%97%90-%EB%8C%80%ED%95%B4-%EC%95%8C%EC%95%84%EB%B3%B4%EC%9E%90%EC%82%AC%EC%9A%A9%EB%B2%95-Method)는 pring Data JPA에서 제공하는 인터페이스 중 하나로, JPA를 사용하여 데이터베이스를 조작하기 위한 메서드들을 제공한다.

JPARepository 인터페이스를 상속받는 인터페이스를 정의하면, 해당 인터페이스를 구현하는 클래스는 JPA에서 제공하는 메서드들을 사용할 수 있다.

데이터베이스의 추가, 조회, 수정, 삭제의 findAll(), findById(), save() 등의 메서드들을 사용할 수 있다. 제공되는 메서드들 이용하여 쉽고 간편하게 CRUD 조작을 할 수 있다.
즉, JpaRepository를 사용하면, 복잡한 JDBC(Java DataBase Connectivity) 코드를 작성하지 않아도 간단하게 DB와의 데이터 접근 작업을 처리할 수 있다.

### Application Layer와 UI Layer

[애플리케이션 계층](https://ademcatamak.medium.com/layers-in-ddd-projects-bd492aa2b8aa)은 비즈니스 프로세스 흐름을 처리하는 계층이다. <br/>
이 계층에서 애플리케이션의 기능을 관찰할 수 있다. 도메인 엔터티는 여기에서 생성되고 업데이트될 수 있다. 사용 시나리오에 따라 트랜잭션 관리와 같은 주제도 여기에서 해결된다. 이 계층에서는 작업 명령 실행과 도메인 이벤트에 대한 반응이 코딩된다.

✨ Reference

https://wikibook.co.kr/article/layered-architecture/