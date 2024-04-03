## ✔️ 키워드 정리

### CORS 란

[CORS(Cross-Origin Resource Sharing)](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS)는 교차 출처 리소스 공유라고 번역하는데, 출처는 origin의 번역 표현이다. 

```bash
https://myshop.com:8080/path/page?p1=v1&p2=v2...#hash
```

href의 구조

- `https:`: Protocol
- `myshop.com`: Hostname
- `8080`: Port
- `path/page`: Pathname
- `p1=v1&p2=v2`: Search
- `#hash`: Hash

Hostname과 Port를 합쳐서 Host라고 하고, Protocol과 Host를 합쳐서 Origin이라고 한다.

CORS를 설정한다는 건 출처가 다른 서비스간의 리소스 공유를 허용한다는 것이다.

보안상의 이유로 브라우저는 스크립트에서 시작된 교차 출처 HTTP 요청을 제한한다.


CORS 에러에 대응하기 위해서는

1. 서버에서 `Access-Control-Allow-Origin` 응답 헤더 세팅하거나
2. 웹 애플리케이션이 리소스를 직접적으로 요청하는 대신, 프록시 서버를 사용하여 웹 애플리케이션에서 리소스로의 요청을 전달하는 방법도 있다. 웹 애플리케이션이 리소스와 동일한 출처에서 요청을 보내는 것처럼 보이므로 CORS 에러를 방지할 수 있다.

### 동일 출처 정책

[동일 출처 정책](https://developer.mozilla.org/en-US/docs/Web/Security/Same-origin_policy)은 한 출처에서 로드한 문서나 다른 출처의 리소스와 상호 작용하 수 있는 방식을 제한하는 중요한 보안 메커니즘이다.

웹과 상호작용하는 자바스크립트 코드에 대한 보안 제약 사항 중 하나다.

- 전송 제한 종류: 도메인, 메서드, 헤더
    - 도메인: 자바스크립트에서, 요청 가능한 사이트 도메인 제한
    - 메서드: 전송 가능한 메서드 제한
    - 헤더: 웹 브라우저 능력을 넘어서는 것 금지

 문서 출처가 동일한 곳으로 제한: URL, 프로토콜, 호스트, 포트번호

이 중 하나라도 다르면 동일 출처 정책에 위반됨

자바스크립트 코드를 포함하는 본 문서의 출처는 제약받지 않지만, 그 안의 내용을 확인할 수는 없음

### JSONP

JSONP란 CORS가 활성화 되기 이전의 데이터 요청 방법으로, 다른 도메인으로부터 데이터를 가져오기 위해 사용하는 방법이다.

JSONP는 HTML 문서의 script 태그로 다른 도메인을 요청 할 시 SOP 정책이 적용되지 않는 방식을 이용하여 동작한다.

script 태그는 src 속성 값을 호출한 결과를 javascript로 불러와서 즉시 실행시키는 기능이다.

### Access-Control-Allow-Origin


### @CrossOrigin

✨ Reference

https://docs.tosspayments.com/resources/glossary/cors<br/>
https://medium.com/@lifthus531/cors%EC%97%90-%EB%8C%80%ED%95%9C-%EA%B9%8A%EC%9D%80-%EC%9D%B4%ED%95%B4-8c84c2137c83<br/>
https://velog.io/@yesdoing/JSONP%EB%9E%80-jujowt4jy7<br/>