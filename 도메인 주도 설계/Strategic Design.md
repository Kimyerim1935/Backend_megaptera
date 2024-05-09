### 보편언어 (Ubiqutious Language)

[Ubiqutious Language](https://martinfowler.com/bliki/UbiquitousLanguage.html)는 에릭 에반스가 도메인 중심 디자인에서 개발자와 사용자 간에 공통의 엄격한 언어를 구축하는 관행에 사용하는 용어이다. 이것은 DDD가 제공하는 이점을 구현하고 실현하는 초석이 된다. 표현력이 풍부한 공통 모델은 비즈니스 핵심 역량과 관련된 소프트웨어 애플리케이션을 전달하고 개발하기 위한 토대를 제공한다.

이 언어는 소프트웨어에서 사용되는 도메인 모델을 기반으로 해야하며, 소프트웨어는 모호성에 잘 대처하지 못하기 때문에 엄격해야 한다.


### 제한된 컨텍스트 (Bounded Context)

[Bounded Context](https://martinfowler.com/bliki/BoundedContext.html)는 도메인 중심 디자인의 핵심 패턴이다. 이는 대규모 모델과 팀을 다루는 DDD의 전략적 디자인 섹션의 초점이다. DDD는 대규모 모델을 서로 다른 Bounded Context로 나누고 상호 관계를 명확히 함으로써 대규모 모델을 다룬다.

소프트웨어 개발을 할 때 기술적/비즈니스적 한계를 마주하게 된다. 어떤 이슈를 발견하게 되면 그 한계로 인해 side-effect가 발생하게 되는데 도메인을 통해 side-effect를 관리할 수 있다.

도메인은 소프트웨어에서 사용자가 알 숭 있는 곳에 있으므로, 무언가 변경이 필요하면 관련된 요소들이 무엇인지 쉽게 찾을 수 있다.

도메인에 집중하면 도메인이 설명하는 범위와 도메인 간의 경계들이 명확하게 드러나는데, 이것을 Bounded Context라고 한다.<br/>
Bounded Context는 하나의 도메인 또는 도메인의 집합이며, DDD에서 소프트웨어를 쉽게 바라볼 수 있도록 하는 시야를 제공한다.

Bounded Context는 해당 요소가 최소한이자 최대한으로 필요로 하는 범위를 나타내고, 보편 언어를 자연스럽게 반영한다.

이와 같이 개발자에 의해 구현된 요소가 도메인으로 정의 되고 그 관계와 경계를 명확하게 알 수 있다면 코드의 가독성과 함께 복잡성(의존성)을 관리할 수 있다.

코드를 쉽게 읽고 의존성들을 쉽게 파악할 수 있다면, 주어진 문제를 해결하기 위해 무엇을 해야 하는지 쉽게 접근할 수 있고, 불필요한 시간의 소비와 예상치 못한 side-effect를 최소화할 수 있다

### 하위 도메인 (Subdomain)

DNS 계층에서 [Subdomain](https://ko.wikipedia.org/wiki/%EC%84%9C%EB%B8%8C%EB%8F%84%EB%A9%94%EC%9D%B8)은 다른 도메인의 일부인 도메인이다.

```bash
## en이 wikipedia.org의 서브도메인이다.

https://en.wikipedia.org/wiki/Subdomain
```
어떠한 서브도메인도 포함하지 않는 도메인 네임은 루트 도메인(root domain), 베어 도메인(bare domain), 에이펙스 도메인(apex domain)으로 부른다.

예를 들어 wikipedia.org는 위키백과의 에이펙스 도메인이며 서브도메인 www.wikipedia.org로 리다이렉트한다.

시스템을 나누는데 Bounded Context라는 단위를 사용한다면, 도메인을 나눌 땐 Subdomain이라는 단위를 사용한다. 

전자는 소프트웨어를 조직화하는 방법이라면, 후자는 현실을 조직화하는 방법이다. 전자는 개발하면서 발전시킬 수 있지만, 후자는 개발하면서 맞춰나가야 한다. 

좀 더 어렵게 (하지만 더 정확하게) 표현하면, Subdomain은 Problem Space고, Bounded Context는 Solution Space다.

✨ Reference
https://medium.com/@johnboldt_53034/domain-driven-design-the-ubiquitous-language-4f516a385ca4<br/>
https://medium.com/crossplatformkorea/%EB%8F%84%EB%A9%94%EC%9D%B8-%EC%A3%BC%EB%8F%84-%EC%84%A4%EA%B3%84-domain-driven-design-in-real-project-bounded-context-e2bee96deeb2<br/>