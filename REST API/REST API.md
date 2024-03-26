## ✔️ 키워드 정리

### API(Application Programming Interface)

[API](https://www.redhat.com/ko/topics/api/what-are-application-programming-interfaces)는 컴퓨터나 컴퓨터 프로그램 사이의 연결이다. 컴퓨터와 인간을 연결시키는 [UI](https://ko.wikipedia.org/wiki/%EC%82%AC%EC%9A%A9%EC%9E%90_%EC%9D%B8%ED%84%B0%ED%8E%98%EC%9D%B4%EC%8A%A4)와는 반대로 컴퓨터나 소프트웨어를 서로 연결한다.<br/>
애플리케이션 소프트웨어를 빌드하고 통합하기 위한 정의 및 프로토콜 세트인 애플리케이션 프로그래밍 인터페이스를 뜻한다.

API 종류는 다음과 같다.

- 프라이빗<br/>
    : API 를 내부에서만 사용할 수 있도록 하며, 기업이 API를 최대한으로 제어할 수 있다. VPC 내에서만 액세스 할 수 있으며, VPC 엔드포인트에 프라이빗 DNS를 활성화 했는지에 따라 허용된다.
    프라이빗 DNS를 활성화했다면 프라이빗 DNS 이름으로 프라이빗 API에 액세스 할 수 있다.

- 파트너<br/>
    : API를 특정 비즈니스 파트너와 공유하며, 품질 저하 없이 추가 수익원 창출 가능

- 퍼블릭<br/>
    : API가 모두에게 제공되며, 제 3자가 API와 상호작용하는 애플리케이션을 개발하여 혁신을 끌어낼 수 있음

가장 자주 사용하는 [웹 API](https://ko.wikipedia.org/wiki/%EC%9B%B9_API)는 웹 서버나 웹 브라우저를 위한 API다.

### 정보은닉(Information Hiding)과 캡슐화(Encapsulation) : 

캡슐화는 여러 요소들을 하나의 단위로 묶는 것 이상으로 ```외부에 대한 가시적인 부분```과 ```내부 및 구현에 관계되는 세부적인 사항```을 분리하는 모델링 및 구현기법이다. 객체 지향 프로그래밍에서 많이 쓰인다.

캡슐화를 통해 복잡하고 불필요한 부분을 사용자에게 안보이게 하고 외부세계와 인터페이스를 잘 할 수 있도록 표준화시킨 포장이 되도록 한다.

OOP에서의 캡슐화의 주요 특징으로는

- 데이터 및 함수를 논리적으로 하나로 묶어놓음
- 임의의 객체 요소의 접근 제한 방법 제공
- 내부 데이터를 캡슐화시켜 변경을 어렵게 하고 보호함

이 있다.

정보 은닉은 객체가 가진 언어적 요소(instance 변수나 메서드)를 활용하여 객체에 대한 구체적인 정보를 노출시키지 않도록 하는 기법이다.<br/>
데이터 보호가 주 목적이며, instance 변수의 값을 직접 변경하지 못하게 하고 메서드를 통해 변경, 조회하도록 만든다.

객체지향 언어를 통해서 유연성을 얻고자 한다면 정보 은닉은 그 유연성을 가능하게 하려는 전략이다. 객체, 상속, 캡슐화 등은 정보 은닉의 수단에 불과하고 좋은 정보 은닉은 잘 된 추상화를 통해 얻어진다. 

### Architecture와Architecture Style의 차이

아키텍처 스타일은 이름이 붙어있는 제약사항의 집합이다. REST 또한 아키텍처 스타일 중의 하나이다.

MSA도 대표적인 아키텍처 스타일인데, [microservices.io](https://microservices.io/)의 첫 페이지에서 "
애플리케이션을 서비스 모음으로 구성하는 아키텍처 스타일" 라고
설명한다

아키텍처는 

- 시스템 구성 및 동작 원리를 나타내는 것
- 구성 요소 간의 고나계 및 시스템 외부 환경과의 관계를 묘사하는 것
- 요구 사양 및 시스템 수명 주기를 고려하는 것
- 시스템의 전체적인 최적화를 목표로 하는 것

이다. 서비스의 동작원리(어떻게 구성되고 어떻게 동작이 되는지)를 나타내는 것이다.

### REST(7가지 제약 조건 위주로 정리)

- Starting with the Null Style</br>
    : Architectural Design을 할 때 두 가지 관점이 있다.
    하나는 빈 곳에서 시작하여 원하는 시스템의 조건을 충족시킬 때까지 Architecture를 생성하는 것이고, 다른 하나는 제한에 없던 시스템에서 출발하여 제한을 추가하면서 원하는 시스템으로 만드는 것이다.<br/>
    첫 번째 방법은 창의성을 중시하고, 두 번째 방법은 제한과 시스템 context에 대한 이해를 중시한다.

    REST는 두 번째 방법에 의해서 발전되어 왔다.
- Client-Server</br>
    : 첫 번째로 추가된 제한이다. UI와 데이터 저장을 분리함으로써 여러 플랫폼에서의 이식성을 높이고 서버를 단순화시켜 scale up하기 수월해졌다. 이런 분리가 웹의 독립적인 진화를 가능케했다.

- Stateless</br>
    :다음으로 추가된 제한은 client-server의 Interaction에 추가되었다. 커뮤니케이션은 stateless여야만하고 client로부터 서버로 가는 각 request들은 request를 이해할 때 필요한 모든 정보를 포함하고 있어야 하며, server에 저장된 어떠한 context에 의해서도 advantage를 받으면 안된다.

    Session State는 client에 의해서만 관리된다.

    이러한 제안은 visibility(하나의 Request를 너머서 볼 필요가 없어지기 때문), reliability(부분적인 failurs로부터 task의 복구가 쉽기 때문), scalablitiy(state를 저장할 필요가 없고 implementation도 단순화 시켜 서버의 자원 사용 최소화)의 속성을 향상시킨다.

    sateless도 trade-off가 있다. stateless는 반복되는 data에 의해 network performance를 감소시킨다.

- Cache</br>
    :네트워크 효율성을 높이기 위해 stateless에 cache constraint를 더하게 되었다. Cache contraint는 response 에 담긴 data에 cacheable한지 아닌지 라벨링을 강제한다.
    
    cache constraint의 장점은 부분적인 interaction들을 제거하여 효율성과 scalability를 높이고 평균적인 지연을 줄여 user가 느끼는 performance를 향상시켜준다.

    trade-off로 cache에 있는 데이터가 stale 된 경우에도 server로 보낼 수 있어 reliability를 떨어뜨린다.

- Uniform Interface</br>
    :Component interface를 도입함으로써 전체적인 시스템 architecture가 단순해지고 interaction의 visibility도 높아졌다.

    Implemenation이 서비스를 주는 쪽과 decoupled 되면서 독립적인 발전이 가능해졌다.

    Trade-off는 uniform interface가 정보들이 표준화되어 이동하다 보니 효율성을 낮아졌다.

    REST는 Web의 흔한 case와 hypermedia data 전송에 효율적이나 다른 형태의 architectural interaction에 최적화된 것은 아니다.

    uniform interace를 위해 component들의 behavior에 대해서 여러 architectural 제한들이 더 요구된다.

    - identification of resources
    - manipulation of resources through representations
    - self-descriptive messages
    - hypermedia as the engine of application state

- Layered System</br>
    : internet-scale에서의 성능 향상을 위해 Layered system constraints을 추가했다.<br/>
    layered system style은 component들을 제한시켜(예를 들면 각 component는 자신과 소통하고 있는 layer의 너머를 보지 못한다) architecture을 구조적인 layer들로 이뤄지게 한다.

    한 layer의 knowledge를 제한시켜 전체적인 시스템의 복잡도를 제한시키고 독립성을 촉진시킨다.

    Layer는 legacy service들을 캡슐화시키고 새로운 서비스를 legacy client로부터 보호한다. 또한 자주 사용되지 않는 기능을 공유되는 intermediary로 이동시켜 component들을 단순화 시킨다.

    Intermediary는 여러 네트워크와 프로세서들 사이에서 로브 밸런싱을 수행해 시스템 scalability를 높일 때 사용되기도 한다.

    Layered system의 가장 큰 단점은 데이터를 처리할 때 오버헤드와 지연이 생겨 유저가 느끼는 performance를 떨어뜨릴 수 있다.

    Cache constraints을 지원하는 network-based system의 경우 intermediaries의 shared caching의 이득으로 이는 상쇄된다. organizational domain의 경계에 공유되는 cache를 놓는 것은 큰 performance 향상을 낳는다.

    Layered system과 uniform interface constraints의 조합으로 architectural 속성들은 uniform pipe-and-filter style과 흡사해진다. REST interaction은 two-way인데도 불구하고, hypermedia interacion은 data-flow network처럼 처리된다. filter component들이 선택적으로 data stream에 적용을 함으로써 컨텐츠가 전달될 때 변환시킬 수 있기 때문이다.

    REST에서는 intermediary component들이 content들의 메시지는 self-descriptive하고 의미가 intermediary에게 visible하기 때문에 actively하게 바꿀 수 있다.

- Code-On-Demand</br>
    :REST는 client에게 코드(애플릿, 스크립트 형태)를 다운로드하고 실행할 수 있게 하였다.

    하지만 visibility를 감소시키므로 REST에 optional한 constraint이다.

✨Refference

[객체지향의 올바른 이해:5. 정보 은닉](https://effectiveprogramming.tistory.com/entry/%EA%B0%9D%EC%B2%B4%EC%A7%80%ED%96%A5-%EC%A0%95%EB%B3%B4-%EC%9D%80%EB%8B%89information-hiding%EC%97%90-%EB%8C%80%ED%95%9C-%EC%98%AC%EB%B0%94%EB%A5%B8-%EC%9D%B4%ED%95%B4)<br/>

[REST -Roy Fielding 번역 요약](https://woojinger.tistory.com/33)