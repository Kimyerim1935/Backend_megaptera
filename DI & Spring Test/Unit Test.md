## ✔️ 키워드 정리

### V 모델

[V모델](https://ko.wikipedia.org/wiki/V_%EB%AA%A8%EB%8D%B8)은 소프트웨어 개발 프로세스로 폭포수 모델의 확장된 형태 중 하나로 볼 수 있다.

V모델은 소프트웨어 개발의 각 단계마다 상세한 문서화를 통해 작업을 진행하는 잘 짜인 방법을 사용한다. 또한 테스트 설계와 같은 테스트 활동을 코딩 이후가 아닌 프로젝트 시작 시에 함께 시작하여, 전체적으로 많은 양의 프로젝트 비용과 시간을 감소시킨다.

### Test Matrix

### 내적 품질(테스트 코드 작성등)을 높이면 좋은 이유

### JUnit

JUnit 플랫폼은 JVM에서 테스트 프레임워크를 시작하기 위한 기반 역할을 한다. 

현재 가장 많이 사용되고 있는 버전은 JUnit5이며, JUnit Platform + JUnit Jupiter + JUnit Vintage 이렇게 구성되어있다.

JUnit Platform은 테스트를 발견하고 테스트 계획을 생성하는 TestEngine 인터페이스를 정의한다.
기초적인 역할을 수행하며, TestEngine API를 제공한다.

JUnit Jupiter는 JUnit5에서 테스트 및 Extension을 작성하기 위한 새로운 프로그래밍 모델과 확장 모델의 조합이며, TestEngine API 구현체이다.

JUnit Jupiter는 JUnit3, JUnit4를 실행할 수 있는 TestEngine이다. 하위 호환성을 위해 존재한다.

### 단위 테스트

단위테스트란 개별적인 코드 단위가 의도한대로 작동하는지 과정이다. 소프트웨어의 개별 코드 단위를 테스트 하여 오류를 발견하고, 이를 수정하여 전체적인 소프트웨어의 품질을 향상시키는 과정이다.

모듈 단위로 테스트를 하며, 작성비용이 적게 들고 실행 속도가 빠르다는 장점이 있다.

Java에서는 JUnit을 사용하고, React에서는 Jest를 사용한다.

### E2E 테스트

E2E 테스트는 개발물을 사용자 관점에서 테스트 하는 방법이다.

일반적으로 웹이나 어플 등에서 GUI를 통해 시나리오, 기능 테스트 등을 수행한다.

Endpoint 테스트를 통과하면 기능이 잘 작동한다는 것이므로 모든 테스트를 할 수 없다면 E2E테스트만이라도 하는 것이 좋다.

### 통합 테스트(Integration Test)

애플리케이션의 여러 컴포넌트 혹은 모듈간의 상호작용과 조정을 검증하는 데 중점을 둔 소프트웨어 테스팅 유형이다. 

유닛 테스트에서 테스트된 유닛들이 결합되었을 때, 올바르게 작동하는지를 확인한다.

개발 프로세스에서 단위 테스트 후 시스템 테스트 전에 수행되며, 자동화 가능한 테스트 영역이다.

✨ Reference

https://junit.org/junit5/docs/current/user-guide/<br/>
https://medium.com/@shinjielee/software-testing-concept-diagram-2ed31356ded1<br/>
https://velog.io/@choidongkuen/Junit-%EC%9D%B4%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%BC%EA%B9%8C-e0w6tlvp<br/>
https://yozm.wishket.com/magazine/detail/1964/<br/>
https://jake-seo-dev.tistory.com/579
