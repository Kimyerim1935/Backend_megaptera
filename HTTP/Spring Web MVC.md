## ✔️ 키워드 정리

### Spring Boot

Spring은 Java 기반 애플리케이션 개발을 지원하는 오픈소스 애플리케이션 프레임워크이다.<br/>
순수 자바 객체(\*POJO)만을 사용하여 복잡성을 제거하고, 단순하고 가벼운 코드로 기업용 애플리케이션을 개발하기 위한 목적으로 개발되었다.

Spring의 특징은 다음과 같다.

- 제어 역전: Spring은 객체의 생명 주기 및 의존성 관리를 담당하는 IoC 컨테이너를 제공한다. 개발자는 객체의 생성과 관계 설정을 스프링에 위임할 수 있으며, 스프링 컨테이너가 객체의 생명주기를 관리하고 필요한 의존성을 주입한다.

- 의존성 주입: 스프링은 의존성 주입을 통해 객체 간의 관계를 설정한다. 이로 인해 애플리케이션의 결합도를 낮추고 유연성과 테스트를 용이하게 한다.
- AOP 지원: 애플리케이션의 핵심 비즈니스 로직과 부가적인 기능을 분리하여 모듈화할 수 있다.
- 웹 개발 지원: 웹 애플리케이션 개발을 위한 다양한 기능과 웹 프레젠테이션 계층을 제공한다. 스프링 MVC는 유연하고 확장 가능한 웹 애플리케이션을 개발할 수 있는 MVC 아키텍처를 지원한다.<br/>

하지만 Spring에도 문제점이 있다.

- 설정의 복잡성
- 러닝커브
- 의존성 관리 문제
- 별도 WAS 서버 구성의 번거로움

이러한 문제를 해결하기 위해 Spring Boot가 개발되었다.

Spring Boot는 기본적인 설정과 보일러 플레이트 코드의 작성을 최소화하고, 자동 설정과 컨벤션을 통해 빠르게 애플리케이션을 개발할 수 있도록 지원하는 스프링 프레임워크다.

내장형 서버를 사용하여 별도의 웹 애플리케이션 서버의 설치 없이 애플리케이션을 실행할 수 있으며, 다양한 프레임워크 기능과 서드파티 라이브러리의 사용을 간편하게 할 수 있다는 장점이 있다.

애플리케이션 개발 이외에도 배치 처리, 다양한 데이터 베이스 엑세스, 보안 요구 사항 처리, 인증 기능 구현, 클라우드 네이티브 애플리케이션 개발에 용이하다는 장점이 있다.

✨POJO(Plain Old Java Object)란?<br/>
특정한 규약이나 프레임워크에 종속되지 않는 간단하고 순수한 자바 객체를 의미<br/>
객체지향 개발의 원칙에 충실한 객체를 말하며, 특정한 제약이나 요구사항에 종속되지 않고 유연하고 확장 가능한 코드의 작성에 용이

✨모듈화<br/>
[모듈은](http://www.ktword.co.kr/test/view/view.php?no=2226) 이해할 수 있는 작은 단위로 이루어진 것이다. 각 모듈은 논리적ㆍ기능적으로 분리되어 격리되고 독립적인 일을 수행한다.

모듈화를 하면 수정과 유지보수가 쉽고 재사용성에 용이하다는 장점이 있다.

자바에서의 모듈은 여러 패키지들의 모음이고, 패키지는 여러 클래스들의 모음이다.

### Spring initializer

[Spring initializer](https://spring.io/guides/gs/spring-boot)는 Spring Boot 기반으로 프로젝트를 생성해주는 사이트이다.

[프로젝트 생성하기](https://start.spring.io/) 에서 프로젝트를 쉽게 생성할 수 있다.

- Project: SpringBoot를 빌드하고 배포하는 방식이다(주로 Gradle 사용)
- Language: 사용하고자하는 언어를 선택하면 된다. (일반적으로 Java가 사용됨)
- SpringBoot: 버전을 선택해 준다. SNAPSHOT은 데모버전이고 높은 버전은 높은 자바버전을 필요로 하므로 SNAPSHOT이 없는 낮은 버전을 선택하는 것이 좋다.
- Group: 기업 도메인명
- Artifact: 빌드되어 나올 결과물
- Name: 프로젝트명 (일반적으로 Artifact와 동일하게 사용)
- Description: 설명
- Package name: 패키지이름(Group과 Artifact를 설정하면 자동 생성)
- Packaging: 기본이 .jar이다. (spring framework와 model2는 .war 사용)

포트 번호를 바꾸고 싶다면,

```java
  // application.properties 파일
  server.port = 8000
```

를 추가해주면 포트가 변경된다.

### Web Server와 Web Application Server(WAS)

Web Server는 정적인 파일을 제공하는 역할을 한다. 대표적으로 Apache와 NginX가 있다. Web Server 클라이언트의 요청을 받아들이고 그에 맞는 정적 파일을 응답으로 제공한다. Web Server는 주로 웹페이지의 전달과 같은 단순한 기능을 수행하는 역할을 담당한다.

✔ Web Server의 주요 기능

- HTTP 프로토콜 지원
  Web Server는 클라이언트와 서버 간 통신에 사용되는 HTTP 프로토콜을 지원
- 정적 파일 제공
  Web Server는 클라이언트가 요청한 정적인 컨텐츠 제공(HTML, Image, CSS)
- MIME 타입 처리
  Web Server는 MIME(Multipurpose Internet Mail Extensions) 타입을 처리하여 클라이언트에게 올바른 파일 형식으로 데이터를 전송
- 가상 호스팅
  Web Server는 하나의 서버에서 여러 개의 도메인을 호스팅할 수 있도록 가상 호스팅(Virtual Hosting) 지원
- 로깅
  Web Server는 서버에 접근한 클라이언트의 정보를 로그 파일에 저장하여 추적 및 분석 가능
- 보안 기능
  Web Server는 SSL(Secure Socket Layer) 및 TLS(Transport Layer Security) 프로토콜을 지원하여 데이터의 보안 유지
- Web Server 소프트웨어 확장성
  Web Server는 다양한 소프트웨어 확장 기능을 제공

Web Application Server는 동적인 컨텐츠를 생성하고, 데이터를 처리하는 역할을 한다. 사용자의 요청에 따라 데이터베이스 조회, 비즈니스 로직 처리 등의 작업을 수행한다. 웹 애플리케이션의 실행 환경을 제공하며, 동적인 응답을 생성한다.

### Tomcat

아파치는 흔히 아파치라고 부르는 Apache Software Foundation에서 만든 웹서버 프로그램이다.
아파치 서버는 클라이언트에서 요청하는 HTTP 요청을 처리하는 웹서버를 의미한다. 정적 타입 데이터만을 처리하기 때문에 톰캣이 추가되었다.

톰캣 WAS(Web Application Server)은 아파치 서버와는 다르게 DB연결, 다른 응용프로그램과 상호 작용 등 동적인 기능들을 사용할 수 있다.

### Model-View-Controller(MVC) 아키텍처 패턴

MVC는 Model-View-Controller의 약자로, 개발할 때 3가지 형태로 역할을 나누어 개발하는 방법론이다.

Model은 애플리케이션이 <b>무엇</b>을 할 것인지 정의한다.<br/>
Constoller는 모델이 <b>어떻게</b> 처리할 것인지 정의한다. 모바일에서는 화면의 로직처리 부분이다. 화면에서 사용자의 요청을 받아 처리하는 부분을 구현하게 되며, 요청 내용을 분석하여 Model과 View에 업데이트 요청을 하게 된다.<br/>
View는 화면에 <b>무엇을 보여주기</b>위한 역할을 한다. 컨트롤러 하위에 종속되어, 모델이나 컨트롤러가 보여주려고 하는 모든 필요한 것들을 보여준다.

View는 Controller에 연결되어 화면을 구성하는 단위요소이므로 다수의 View를 가질 수 있다. 그리고 Model은 Controller를 통해 View와 연결되지만 Controller를 통해 하나의 View에 연결될 수 있는 Model도 여러개가 될 수 있다.

즉, 화면의 복잡환 화면과 데이터의 구성이 필요하다면 Controller에 다수의 Model과 View가 복잡하게 연결될 수 있다는 문제점을 갖고 있다.

### 관심사의 분리(Seperation of Concern)

스프링에서의 관심사의 분리는 코드의 유지 보수성, 재사용성, 테스트 가능성 등의 기능을 향상시키는 방법으로, 코드를 모듈화하여 각 모듈이 특정한 역할과 책임을 갖도록 하는 것을 의미한다.

### Spring MVC

스프링에서의 관심사의 분리는 다음과 같은 방식으로 이뤄진다.

1. 의존성 주입<br/>
   : 의존성 주입은 객체 간의 의존성을 외부에서 주입하는 방식으로, 객체 간의 결합도를 낮추어 각 객체는 자신이 수행해야 할 기능에만 집중할 수 있으며, 객체 간의 의존성을 분리 할 수 있다.

2. 제어 역전<br/>
   : 제어 역전은 객체의 생명주기와 의존성 관리를 프레임워크가 담당하도록 하는 개념이다. 스프링은 제어 역전을 통해 객체의 생성, 관리, 소멸 등의 생명 주기를 관리하고, 필요한 의존성을 주입한다.
3. 관점 지향 프로그래밍<br/>
   : AOP는 애플리케이션의 핵심 로직과 관련 없는 부가적인 기능들을 모둘화하여 분리하는 방식이다. 이를 통해 핵심 로직의 코드는 더욱 간결해지고, 부가적인 기능은 별도의 모듈로 분리하여 관리할 수 있다.

### Java Annotation

Annotation이란 자바 소스코드에 추가하여 사용할 수 있는 메타데이터의 일종이다.<br/>
클래스, 인터페이스, 메소드, 메소드 파라미터, 필드, 지역 변수 위에 작성하여 사용하면 된다.

사용 용도

- 컴파일러에게 코드 작성 문법 에러를 체크하도록 정보를 제공하기 위해
- 소프트웨어 개발 툴이 빌드나 배치할 때 코드를 자동으로 생성 할 수 있도록 제공
- 실행 시 특정 기능을 실행하도록 정보 제공

사용 예시는 이렇다.

```java

```

### @RestController

`@RestController`는 `@Controller`에 `@ResponseBody`가 추가된 것이다. RestController의 주용도는 Json 형태로 객체 데이터를 반환하는 것이다. 최근에 데이터를 응답으로 제공하는 REST API를 개발할 때 주로 사용하며 객체를 ResponseEntity로 감싸서 반환한다. 이러한 이유로 동작 과정 역시 @Controller에 @ResponseBody를 붙인 것과 완벽히 동일하다.

```java
@Controller
@ResponseBody
public class App{
	logic...
}

@RestController
public class App{
	logic...
}
```

`@RestController`로 작성하면 모든 메서드가 뷰 대신 객체로 작성된다.
Restful 웹 서비스를 만드는 경우 `@RestController`를 사용하는게 더 좋다고 한다.
직접 사용해보면서 차이점에 대해 느껴보는 것이 좋을 것 같다.

### @Controller

뷰에 표시될 데이터가 있는 Model 객체를 만들고 올바른 뷰를 선택하는 일을 담당한다. `@Controller`는 클래스를 Spring MVC 컨트롤러로 표시하는 데 사용된다.

### @ResponseBody

서버에서 클라이언트에 응답을 보낼 때, 본문에 데이터를 담아서 보내는데, 요청 본문(RequestBody), 응답 본문(ResponseBody)을 담아서 보내야한다.

`@ResponseBody`가 붙은 파라미터에는 HTTP 요청의 본문 body 부분으로 매핑하여 클라이언트로 전송한다.

이 어노테이션을 사용하면 http 요청 body를 자바 객체로 전달받을 수 있다.

### @GetMapping

요청 url에 따른 GET 요청을 메서드와 mapping 시키는 것이다.

이런식으로 사용하면 된다.

```java
@GetMapping(path = "/hello")
```

### @RequestMapping

특정 url로부터 요청을 받으면 어떤 Controller에서 처리할 지 알아야 한다.
이 때, 특정 url을 요청을 수행할 Controller과 매핑하여 지정하는 어노테이션이 @RequestMapping이다.
