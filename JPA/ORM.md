## ✔️ 키워드 정리

### ORM

[ORM](https://ko.wikipedia.org/wiki/%EA%B0%9D%EC%B2%B4_%EA%B4%80%EA%B3%84_%EB%A7%A4%ED%95%91)은 데이터베이스와 객체 지향 프로그래밍 언어 간의 호환되지 않는 데이터를 변환하는 프로그래밍 기법이다. 객체 지향 언어에서 사용할 수 있는 "가상" 객체 데이터베이스를 구축하는 방법이다.

애플리케이션과 데이터베이스 연결 시, SQL 언어가 아닌 애플리케이션 개발 언어로 데이터베이스를 접근하게 해준다. 

ORM은 개발 언어의 일관성과 가독성을 높여준다는 장점을 갖고 있다.

하지만 ORM만으로는 SQL의 모든 부분을 다루기 어렵기 떄문에 SQL 쿼리에 대한 학습도 필요하다.

### JPA(Jakarta Persistence API)

[JPA](https://ko.wikipedia.org/wiki/%EC%9E%90%EB%B0%94_%ED%8D%BC%EC%8B%9C%EC%8A%A4%ED%84%B4%EC%8A%A4)는 관계형 데이터 베이스의 관리를 표현하는 자바 API이다.

JPA는 다음과 같은 영역으로 구성되어 있다.
- The API itself, defined in the jakarta.persistence package (javax.persistence for Jakarta EE 8 and below)
- The Jakarta Persistence Query Language (JPQL; formerly Java Persistence Query Language)
- Object/relational metadata

### Jakarta EE

[Jakarta EE](https://en.wikipedia.org/wiki/Jakarta_EE)는 분산 컴퓨팅 및 웹서비스와 같은 엔터프라이즈 기능에 대한 사양으로 Java SE를 확장하는 사양 세트이다.

### Entity

[Entity](https://docs.oracle.com/javaee/6/tutorial/doc/bnbqa.html)는 경량 지속성 도메인 개체이다. 일반적으로 엔티티는 관계형 데이터베이스의 테이블을 나타내며 각 엔티티 인스턴스는 해당 테이블의 행에 해당한다.

엔티티 클래스는 이런 요구사항을 따라야한다.

- class에 `javax.persistence.Entity` 주석 추가
- 인수가 없는 공개 또는 보호 생성자가 있어야함
- class를 `final`로 선언하지 않을 것
- 세션 bean의 원격 비즈니스 인터페이스 등을 통해 엔티티 인스턴스가 분리된 개체로 값으로 전달되는 경우, class는 직렬화 가능 인터페이스를 구현해야 함
- 엔티티는 엔티티 class와 비엔티티 class 모두 확장할 수 있으며, 비엔티티 class는 엔티티 class 확장 가능
