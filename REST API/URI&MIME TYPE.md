## ✔️ 키워드 정리

### URI & URL & URN

URI(Uniform Resource Identifier)는 통합 자원 식별자라고 불린다.

- Uniform은 리소스를 식별하는 통일된 방식을 말한다.
- Resource는 URI로 식별이 가능한 모든 종류의 자원을 지칭한다.
- Identifier는 다른 항목과 구분하기 위해 필요한 정보를 일컫는다.

```bash
naver.com
```

즉, URI는 인터넷 상의 리소스 "자원 자체"를 식별하는 고유한 문자열 시퀀스이다.

URL(Uniform Resource ocator)은 네트워크 상에서 리소스의 위치를 나타내기 위한 규약이다. 특정 웹 페이지의 주소에 접속하기 위해서는 웹사이트의 주소 뿐만 아니라 프로토콜을 함께 알아야 하는데, 이를 모두 나타낸 것이 URL이다.

```bash
https://www.naver.com
```

URI가 더 포괄적인 개념이며, URL은 일종의 URI이다.

URI는 그 자체로 이름이 될 수 있다.

URI는 그 자체로 이름이거나, 이름+위치(https://www.naver.com)를 나타낸 형태 모두를 해당한다.

```bash

# 네이버에서 사과 검색
https://search.naver.com/search.naver?where=nexearch&sm=top_hty&fbm=0&ie=utf8&query=%EC%82%AC%EA%B3%BC
```

```https://```부분을 Scheme라고 하는데, 리소스에 접근하는 데 사용할 프로토콜에 말한다. 웹에서는 주로 https나 http를 사용한다.

```search.naver.com```부분을 Host라고 하는데 접근할 대상(서버)의 호스트 명을 말한다.

```search.naver?where=nexearch&sm=top_hty&fbm=0&ie=utf8&query=%EC%82%AC%EA%B3%BC```부분을 Path라고 하는데, 접근할 대상(서버)의 경로에 대한 상세 정보를 확인할 수 있다.

URN은 리소스의 위치, 프로토콜, 호스트와는 상관 없이 각 자원의 이름을 부여한 것이다. 웹 문서의 물리적인 위치와 상관 없이 웹 문서 자체를 나타낸다.

이렇게 개별 자원에 식별자를 부여하게 되면 해당 정보에 대한 URN은 일정하게 유지되며, 리소스의 위치, 프로토콜, 호스트와 관계없이 위치를 파악할 수 있다는 장점이 있다.

URN < URL < URI로 기억하면 될 것 같다.

### MIME type

[MIME Type](https://developer.mozilla.org/ko/docs/Web/HTTP/Basics_of_HTTP/MIME_types)은 인터넷에서 전송되는 다양한 종류의 데이터를 식별하기 위한 형식이다. 주로 웹 브라우저가 웹 서버로부터 받은 데이터를 해석할 때 사용된다.

MIME Type은 파일의 확장자나 내용에 따라 결정된다.

HTTP Headers에 Content-Type 속성으로 전달한다.

이런 것들을 주로 사용한다.

- text/plain ⇒ E-mail에서 자주 사용.
- text/html ⇒ 일반적인 웹 문서. HTML 문서.
- text/css
- text/javascript
- application/xml ⇒ 범용. 자기서술적이기 상대적으로 어렵다.
- application/atom+xml
- application/json ⇒ 범용. 자기서술적이기 굉장히 어렵다.
- application/dns+json
- form-data ⇒ 파일 객체 데이터 전송할 때 사용

 # CQS

 [CQS(Command Query Separation)](https://medium.com/@su_bak/cqs-command-query-separation-pattern-%E1%84%8B%E1%85%B5%E1%84%85%E1%85%A1%E1%86%AB-f701eabf8754)은 소프트웨어 디자인 패턴 중에 하나로, 모든 객체의 메서드 작업을 수행하는 ```command```와 데이터를 반환하는 ```query``` 이렇게 2개로 구분하는 디자인 패턴이다.

 주의할 점은 하나의 메서드가 command이면서 query일 수는 없고 둘 중 하나에만 속해야 한다는 것이다.

 command는 객체의 내부 상태를 바꾸지만 값을 반환하지는 않는다.
 query는 객체 내부 상태를 바꾸지 않고 객체의 값을 반환하기만 한다.

 CQS 배턴을 사용하면 ```데이터 읽기```와 ```데이터 쓰기```를 분리할 수 있다는 장점이 있기 때문에 성능 최적화 및 가독성에 도움이 된다.

 하지만, 관리해야하는 객체가 많아질 수록 query와 command가 많아지기 때문에 중복되는 코드가 발생할 수 있고, 유지보수에도 어려움을 겪을 수 있다는 단점이 있다.

 