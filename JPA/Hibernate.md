## ✔️ 키워드 정리

### Hibernate

[Hibernate](https://en.wikipedia.org/wiki/Hibernate_(framework))은 Java 프로그래밍 언어를 위한 객체 관계형 매핑도구이다. 

객체 지향 도메인 모델을 관계형 데이터베이스에 매핑하기 위한 프레임워크를 제공한다.

Hibernate는 직접적이고 지속적인 데이터베이스 액세스를 높은 수준의 객체 처리 기능으로 대체하여 객체-관계형 임피던스 불일치 문제를 처리한다.

Hibernate의 주요 기능은 Java 클래스에서 데이터베이스 테이블로 매핑하고 Java 데이터 유형에서 SQL 데이터 유형으로 매핑하는 것이다.

Hibernate는 데이터 쿼리 및 검색 기능을 제공한다는 장점이 있다.

### 데이터 모델 / 객체 모델

[데이터 모델](https://ko.wikipedia.org/wiki/%EB%8D%B0%EC%9D%B4%ED%84%B0_%EB%AA%A8%EB%8D%B8)은 데이터의 관계, 접근과 그 흐름에 필요한 처리 과정에 추상화된 모형이다. 

데이터 모델은 데이터 구조를 결정한다.

[객체 모델](http://word.tta.or.kr/dictionary/dictionaryView.do?subject=%EA%B0%9D%EC%B2%B4+%EB%AA%A8%EB%8D%B8)은 객체 지향형 데이터베이스에 저장되는 객체가 구비해야하는 속성과 성질을 정의한 것으로, 관계형 데이터베이스의 관계 모델에 해당하며 OODB에 필요한 검색 키나 객체의 영속성 등이 추가되었다.

### entityManager

[EntityManager](https://www.ibm.com/docs/en/wasdtfe?topic=architecture-entity-manager)는 엔티티 인스턴스의 수명 주기를 관리하는 API이다. 

entity는 관계형 데이터베이스에서 그 자체를 지속할 수 없으며, 어노테이션은 POJO를 엔티티로 선언하거나 관계형 데이터베이스의 해당 테이블과의 매핑 및 관계를 정의하는 데에만 사용된다.

JPA에서는 애플리케이션이 관계형 데이터베이스에서 엔티티를 관리하고 검색할 수 있도록 하기 위해 EntityManager 인터페이스가 사용된다.

### 트랜잭션

데이터베이스 트랜잭션은 데이터베이스 관리 시스템 또는 유사한 시스템에서의 상호작용의 단위이다. 여기서 유사한 시스템이란 트랜잭션이 성공과 실패가 분명하고 상호 독립적이며, 일관되고 믿을 수 있는 시스템을 의미한다.

데이터베이스 기능 중, 트랜잭션을 조작하는 기능은 사용자가 데이터베이스 완전성 유지를 확신하게 한다.

단일 트랜잭션은 데이터베이스 내에 쓰거나 읽는 여러 개의 쿼리를 요구한다.

간단한 트랜잭션은 아래 양식의 SQL 언어로 데이터베이스 내에서 실행된다.

- Begin the transaction
- Execute several queries (DB내 갱신이 아직 적용되지 않음)
- Commit the transaction (트랜잭션이 성공적이며, 갱신이 실제 적용됨)

만약 쿼리 하나가 실패하면, 데이터베이스 시스템은 전체 트랜잭션 또는 실패한 쿼리를 롤백한다. 트랜잭션은 커밋전에 언제든지 수동으로 롤백될 수 있다.

### JPQL

[JPQL(Java Persistence Query Laguage)](https://www.ibm.com/docs/ko/radfws/9.6.1?topic=architecture-jpa-query-language)는 엔티티를 저장하는 데 사용되는 메커니즘에 독립적인 지속성 엔티티에 대한 검색을 정의하는 데 사용된다.

JPQL은 Enterprise JavaBeans 조회 언어인 EJB QL의 확장이며 SQL의 구문 및 단순 조회 시멘틱을 객체 지향 표현식 언어의 표현과 결합하도록 디자인되었다.

JPQL은 작업 중에 작성된 동적 조회 및 이름 지정된 조회와 같은 두 가지 유형의 조회를 정의한다.

이름 지정된 조회는 동일한 조회가 여러 번 호출되는 컨텍스트에 사용된다. 이러한 조회는 향상된 코드 재사용 가능성, 수월한 유지보수 및 잠재적으로 향상된 성능과 같은 주요 이점을 갖고 있다.

이름 지정된 조회는 `@NamedQuery` 어노테이션을 사용하여 정의된다.

하지만 가독성이 높고 확장 가능한 동적 쿼리를 작성하기 위해 Querydsl을 사용이 늘어나는 추세인 것 같다.

✨ Reference

https://yeongunheo.tistory.com/entry/%EC%8B%A4%EB%AC%B4%EC%97%90%EC%84%9C-JPQL-%EB%8C%80%EC%8B%A0-Querydsl%EC%9D%84-%EB%A7%8E%EC%9D%B4-%EC%82%AC%EC%9A%A9%ED%95%98%EB%8A%94-%EC%9D%B4%EC%9C%A0<br/>
