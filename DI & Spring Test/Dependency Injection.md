## ✔️ 키워드 정리

### Spring AOP(Aspect Oriented Programming)

Spring AOP는 스프링 프레임워크에서 제공하는 기능 중 하나로 관점 지향 프로그래밍을 지원하는 기술이다. Spring AOP는 로깅, 보안, 트랜잭션 관리 등과 같은 공통적인 관심사를 모듈화하여 코드 중복을 줄이고 유지 보수성을 향상하는 데 도움을 준다.

Aspect-Oriented Programming이란

객체 지향 프로그래밍 패러다임을 보완하는 기술로 메서드나 객체의 기능을 핵심 관심사와 공통 관심사로 나누어 프로그래밍하는 것을 말한다.

핵심 관심사는 각 객체가 가져야 할 본래의 기능이며, 공통 관심사는 여러 객체에서 공통적으로 사용되는 코드를 말한다.

### Dependency Injection

Dependency Injection을 사용하면 일반 Java 클래스를 관리되는 객체로 전환하고 다른 관리되는 객체에 주입할 수 있다. 

### 싱글턴 패턴

Singleton pattern을 따르는 클래스는 생성자가 여러 차례 호출되더라도 실제로 생성되는 객체는 하나이고 최초 생성 이후에 호출된 생성자는 최초의 생성자가 생성한 객체를 리턴한다.

궁통된 객체를 여러 개 생성해서 사용하는 DBCP(DataBase Connection Pool)과 같은 상황에서 많이 사용된다.

### IoC(Inversion of Control)

IoC Container 는 DI의 핵심 개념이다. 컴퓨터 프로그램의 사용자 정의 작성 부분이 일반 프레임워크에서 제어 흐름을 수신하는 디자인 패턴이다.

이 설계를 사용하는 소프트웨어 아키텍처는 절차적 프로그래밍과 비교하여 제어를 반전시킨다. 제어 반전은 애플리케이션 프로그래머가 정의한 방법으로 프레임워크를 확장할 수 있게 해준다.

### Spring Bean

빈은 스프링 컨테이너에 의해 관리되는 재사용 가능한 소프트웨어 컴포넌트이다. 스프링 컨테이너가 관리하는 자바 객체를 뜻하며, 하나 이상의 빈을 관리한다.

빈은 인스턴스화 된 객체를 의미하며 스프링컨테이너에 등록된 객체를 스프링 빈이라고 한다.

스프링 간 객체가 의존 관계를 관리하도록 하는 것에 가장 큰 목적이 있다. 객체가 의존관계를 등록할 때 스프링 컨테이너에서 해당하는 빈을 찾고 그 빈과 의존성을 만든다.

### BeanFactory

Spring에서 빈 객체를 생성하고 관리하는 역할을 수행한다.
BeanFactory는 Application Context의 상위 인터페이스이며, Application Context는 Bean Factory를 상속하고 더 많은 기능을 제공한다.

BeanFactory의 역할은 다음과 같다.

- 빈 객체의 생성과 관리: BeanFactory는 XML 또는 Java 기반의 설정 메타 데이터를 읽어 빈 객체를 생성하고 빈의 생명주기를 관리한다.
- 빈 객체의 지연 로딩: BeanFactory는 요청시에 빈 객체를 생성하며, 지연 로딩을 지원한다. 필요한 시점에 빈 객체를 생성하여 메모리를 효율적으로 관리할 수 있다.
- 빈 객체의 설정과 프로퍼티 설정: BeanFactory는 빈 객체의 설정 정보와 프로퍼티 값을 관리한다. 설정 파일에서 빈의 정의와 프로퍼티 값을 읽어와 빈 객체를 생성하고 설정한다.

이렇게 사용하면 된다.
```java
DefaultListableBeanFactory beanFactory = new DefaultListableBeanFactory();
```

✨Reference

https://adjh54.tistory.com/133<br/>
https://docs.spring.io/spring-framework/reference/core/beans/dependencies/factory-collaborators.html<br/>
https://dev-wnstjd.tistory.com/440<br/>
