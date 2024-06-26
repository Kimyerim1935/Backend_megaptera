## ✔️ 키워드 정리

### DTO (Data Transfer Object) 란

[DTO](https://martinfowler.com/eaaCatalog/dataTransferObject.html)란 메서드 호출 수를 줄이기 위해 프로세스 간에 데이터를 전달하는 객체이다.(계층간 데이터 교환을 위해 사용하는 객체라고도 한다)

`Remote Facade`와 같은 원격 인터페이스로 작업할 때 각 호출비용이 많이 든다. 결과적으로는 통신 횟수를 줄여야하며, 통신할 때마다 더 많은 데이터를 전송해야한다는 것을 의미한다.

많은 매개 변수를 사용하는 방법도 있지만, 단일 값만 반환하는 Java와 같은 언어에서는 불가능하다.

이를 해결하기 위해 호출에 대한 모든 데이터를 보유할 수 있는 데이터 전송 객체가 만들어졌다.

### 프로세스 간 통신(IPC, Inter-Process Communication)

[IPC](https://ko.wikipedia.org/wiki/%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4_%EA%B0%84_%ED%86%B5%EC%8B%A0)란 프로세스들 사이에 서로 데이터를 주고 받는 행위 또는 그에 대한 방법이나 경로를 뜻한다.

IPC는 마이크로커널과 나노커널의 디자인 프로세스에 매우 중요하다.
IPC에는 기본적으로 두 가지 모델이 있는데, 공유 메모리와 메시지 전달이 있다.

공유 메모리는 협력 프로세스 간 공유되는 메모리를 생성하는 것을 의미한다. 그 지역에 있는 데이터를 이해하고 정보를 교환할 수 있다.
데이터의 형식과 위치는 프로세스에 의해 결정되는 것이 아니다. 또한 프로세스는 같은 위치에 있는 사람에게 책임을 져야한다.

메시지 전달은 OS가 프레임 간 통신 방법을 제공한다. 메모리를 관리하기 위해 대리 전달을 제공하는 것을 의미한다.

IPC가 필요한 이유
- 공유 정보
    : 여러 사용자가 동일한 정보에 관심을 가질 수 있으므로 해당 정보에 동시에 접근 할 수 있는 환경 제공
- 계산 속도 증가
    : 특정 작업을 더 빠르게 실행하려면 해당 작업을 하위 작업으로 나누어야하며, 각 하위작업은 다른 작업과 병렬로 실행됨
- 모듈성
    : 시스템 기능을 별도의 프로세서나 스레드로 나누어 모듈 방식으로 시스템 구성
- 편리성
    : 개인 사용자라도 동시에 여러 작업 수행 가능

IPC 에서 쓸 수 있는 기술은 다음과 같다.

- File → 가장 기본적인 접근. 원격 환경에서 활용하기 어렵다.
- Socket → 파일과 유사하게 읽고 쓸 수 있지만, 원격 환경에서도 활용할 수 있다.
    - HTTP 같은 고수준 프로토콜을 활용하면 어느 정도 정해진 틀이 있기 때문에 상대적으로 쉬워진다.
    - REST를 활용하면 RPC(SOAP의 일반적인 활용)가 아닌 Resource에 대한 CRUD로 정리해야 함.
- Java에선 RPC를 위해 RMI(Remote Method Invocation)란 기술을 제공한다.
    - RPC
    - RMI

REST에선 표현을 다뤄야 하고, 이를 위해 데이터를 담는 것 외엔 사실상 아무 것도 하지 않아서 제대로 된 객체라고 볼 수 없는 (하지만 Java에선 어쩔 수 없이 class를 활용해서 쓸 수 밖에 없는) 특별한 객체를 사용하게 된다.

### “무기력한 도메인 모델” 이란 그리고 안티 패턴인 이유

데이터와 프로세스를 함께 결합하기 때문에 객체지향 디자인의 기본 개념에 너무 어긋난다는 치명적인 단점이 있다.

[무기력한 도메인 모델](https://martinfowler.com/bliki/AnemicDomainModel.html)의 문제점은 어떤 이점도 얻지 못한 채 도메인 모델의 모든 비용을 발생시킨다는 것이다.

Domain Driven Design에는 이런 내용이 들어있다.


> 응용 프로그램 계층(서비스 계층의 이름): 소프트웨어가 수행해야 하는 작업을 정의하고 표현 도메인 개체가 문제를 해결하도록 지시합니다. 이 계층이 담당하는 작업은 비즈니스에 의미가 있거나 다른 시스템의 애플리케이션 계층과 상호 작용하는 데 필요합니다. 이 층은 얇게 유지됩니다. 여기에는 비즈니스 규칙이나 지식이 포함되어 있지 않으며 작업을 조정하고 작업을 다음 계층의 도메인 개체 공동 작업에 위임합니다. 비즈니스 상황을 반영한 상태는 없지만, 사용자나 프로그램의 작업 진행 상황을 반영한 상태는 가질 수 있습니다.

> 도메인 레이어(또는 모델 레이어): 비즈니스의 개념, 비즈니스 상황에 대한 정보, 비즈니스 규칙을 표현하는 역할을 담당합니다. 이를 저장하는 기술적 세부사항은 인프라에 위임하더라도 비즈니스 상황을 반영하는 상태가 여기에서 제어되고 사용됩니다. 이 계층은 비즈니스 소프트웨어의 핵심입니다.

### 자바빈즈(JavaBeans)

빌더 형식의 개발도구에서 가시적으로 조작이 가능하고 또한 재사용이 가능한 소프트웨어 컴포넌트이다.

[자바빈즈](https://ko.wikipedia.org/wiki/%EC%9E%90%EB%B0%94%EB%B9%88%EC%A6%88)가 지켜야할 관례는 다음과 같다.
- 클래스의 상태를 지속적으로 저장ㆍ복원시키기위해 직렬화되어야한다.
- 클래스는 기본 생성자를 가지고 있어야 한다.
- 클래스의 속성들은 get,set 혹은 표준 명명법을 따르는 메서드들을 사용해 접근할 수 있어야 한다.
- 클래스는 필요한 이벤트 처리 메서드들을 포함하고 있어야한다.


### EJB(Enterprise JavaBeans)

EJB는 Java API 및 Java EE 스펙의 서브세트이다. 

EJB는 3가지 종류의 컴포넌트를 포함한다.

1. 세션 빈(Session Beans): 클라이언트의 요청을 처리하기 위한 서버 측 컴포넌트이다. 세션 빈은 상태를 가질 수도 있고 없을 수도 있다. 세션 빈은 비즈니스 로직을 구현하는 데 사용된다.

2. 엔티티 빈(Entity Beans): 데이터베이스와 상호 작용하기 위한 서버 측 컴포넌트이다. 엔티티 빈은 데이터베이스의 테이블에 대응되며, 데이터베이스에 저장된 데이터를 객체로 표현한다.

3. 메시지 빈(Message-Driven Beans): 비동기 메시지를 처리하기 위한 서버 측 컴포넌트이다. 메시지 빈은 JMS(Java Message Service)를 사용하여 메시지를 소비하고 처리한다.

### Java의 record

Java 14부터 도입된 [Record](https://s7won.tistory.com/2) 클래스는 불변 데이터를 객체 간에 전달하는 작업을 간단하게 만들어준다. Record 클래스를 사용하면 불필요한 코드를 제거할 수 있고, 적은 코드로도 명확한 의도를 표현할 수 있다.

Record는 이런 특징을 갖고 있다.

- 멤버 변수는 private final로 선언된다.
- 필드 별 getter가 자동으로 생성된다.
- 모든 멤버변수를 인자로 하는 public 생성자를 자동으로 생성한다.
    (@allaargsconstructor와 유사하지만, record는 불변 데이터를 다루므로 생성자가 실행될 때 인스턴트 필드 수정 불가능)
- equals, hashcode, toString을 자동으로 생성한다.
- 기본 생성자는 제공하지 않으므로 필요한 경우 직접 생성해야 한다.

최신 Java에서는 record를 사용할 수 있지만, 오래된 Bean 관련 라이브러리에서는 지원하지 않는다.

### DAO

[DAO(Data Access Object)](https://iri-kang.tistory.com/5)는 데이터베이스의 데이터에 접근하기 위해 생성하는 객체이다. 데이터베이스에 접근하기 위한 로직과 비즈니스 로직을 분리하기 위해 사용한다.

DB에 접속하여, 데이터의 CRUD 작업을 시행하는 클래스이다.

JSP 및 Servlet 페이지 내에 로직을 기술하여 사용할 수 있지만, 코드의 간결화 및 모듈화, 유지보수 등의 목적을 위해 별도의 DAO 클래스를 생성하여 사용하는 것이 좋다.

### ORM

[ORM(Object Relational Mapping)](https://jalynne-kim.medium.com/%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4-%EB%B0%B1%EC%97%94%EB%93%9C-orm-object-relational-mapping-%EC%9D%98-%EA%B0%9C%EB%85%90%EA%B3%BC-%EC%A2%85%EB%A5%98-%ED%99%9C%EC%9A%A9%EB%B0%A9%EC%95%88-c43b69028957)은 객체로 연결을 해준다는 의미로 어플리케이션과 데이터베이스 연결 시 SQL언어가 아닌 어플리케이션 개발언어로 데이터베이스를 접근할 수 있게 해주는 툴이다.

ORM은 SQL 문법 대신 어플리케이션의 개발 언어를 그대로 사용할 수 있게 함으로써, 개발 언어의 일관성과 가독성을 높여준다는 장점을 갖고 있다. 

ORM은 개발 언어의 일관성과 가독성에 대한 장점이 있지만, ORM만으로는 SQL의 모든 부분을 다루기가 어렵기 때문에 쿼리에 대한 지식도 갖춰야한다.

✨ Reference

https://velog.io/@chanyoung1998/Inter-Process-CommunicationIPC-%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4-%EA%B0%84-%ED%86%B5%EC%8B%A0<br/>
