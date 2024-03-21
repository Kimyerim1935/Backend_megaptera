## ✔️ 키워드 정리

### Java text blocks

자바 17의 Text Blocks 기능은 이런 방식으로 사용하면 된다.

```java
    public class Main {
        public static void main(String[] args) {
           String message = """
            HTTP/-1 200 OK
            
            Hello, world!
            """;
            System.out.println(message);
        }
    }
```

이전 버전의 자바에서는 여러 줄의 코드를 작성하여 멀티 라인 문자열을 처리했어야 했다.

```java
    public class Main {
        public static void main(String[] args) {
            String body = "Hello, world!";
            String message = "" +
                "HTTP/-1 200 OK\n" +
                "Content-Type: text/html; charset=UTF-8\n" +
                "Content-Length: " + bytes.length + "\n" +
                "\n" +
                body;
        }
    }
```

가독성 측면에서는 ``` """ ``` 를 사용한 멀티 라인 문자열이 더 좋아보인다.

자바스크립트의 템플릿 리터럴이랑 비슷한 문법으로 보인다.

### Java InputStream과 OutputStream

자바에서 데이터는 Stream을 통해 입출력 된다.

1. 데이터를 입력 받을 때: InputStream(모든 바이트 기반 입력 스트림은 이 클래스를 상속 받아서 만들어짐)
2. 데이터를 출력할 때: OutputStream(모든 바이트 기반 출력 스트림은 이 클래스를 상속받아서 만들어짐)

프로그램이 네트워크 상의 다른 프로그램과 데이터를 교환하기 위해서는 양쪽 모두 입력 스트림과 출력 스트림이 따로 필요함.

자바의 기본적인 데이터 입출력은 java.io 패키지에서 제공함.

InputStream과 OutputStream 모두 바이트 단위 입출력을 위한 최상위 입출력 스트림 클래스이다.

✨ outstream에 write를 할때 항상 마지막에 줄바꿈(\n)를해주어야 한다. 그래야 데이터가 전송된다.

### Java try-with-resources

사용 후에 반납해주어야하는 자원들은 Closable 인터페이스를 구현하고 있으며, 사용후에 close 메소드를 호출해줘야 했었다.

java7 이전에는 close를 호출하기 위해 ```try-catch-finally```를 이용하여 Null 검사와 함께 직접 호출했는데 해당 방식은 이런 문제점들을 갖고 있었다.

- 자원 반납으로 인한 코드의 복잡도 증가
- 번거로운 작업
- 실수로 인한 자원 미반납
- 에러로 인한 자원 미반납
- 에러 스택 트레이스가 누락되어 디버깅의 어려움

이러한 문제점들을 해결하기 위해 java7부터 자원을 자동으로 반납해주는 ```try-with-resources``` 문법이 추가됐다.

AutoCloseable 인터페이스를 구현하고 있는 자원에 대해 ```try-with-resources```를 적용 가능하도록 하였고, 이로 인해 코드가 유연해지고 모든 에러를 잡을 수 있게 되었다.

기존의 Closeable에 부모 인터페이스로 AutoCloesable을 추가해서 기존에 구현된 자원 클래스들 모두 ```try-with-resources```가 사용가능해졌다.

try-catch-finally가 아닌 ```try-with-resources```를 사용해야 하는 이유는 다음과 같다.

try-catch-finally로 반납할 경우에는 에러 스택 트레이스가 누락되는 경우가 있다. 하지만 ```try-with-resources``` 를 사용하면 누락되는 에러 트레이스 없이 모두 남길 수 있다.

또 다른 이유는 누락없이 모든 자원을 반납할 수 있다는 점이다.

자원을 반납해줘야할 경우에는 ```try-with-resources```를 사용하는게 좋아보인다.

```java
    try (Socket socket = new Socket(host, port)) {
    // Request
    // Response
    }
```
### Java ServerSocket

Java에서 네트워크 서버 애플리케이션을 개발하는 데 사용되는 클래스이다. 

이 클래스는 TCP(전송 제어 프로토콜)를 기반으로 한 서버 소켓을 생성하고 관리하기위해 사용된다.<br/>
TCP는 연결 지향적인 프로토콜로, 데이터를 안정적으로 전송하는 데 사용된다.

서버 애플리케이션을 개발할 때, serverSocket을 사용하여 클라이언트의 연결을 수락하고 데이터를 주고받는 소켓 통신을 구현할 수 있다.

ServerSocket의 기능

- ServerSocket은 클라이언트의 연결을 수락하는 데 사용된다. 서버 애플리케이션은 서버 소켓을 특정 포트에서 생성하고, 클라이언트가 해당 포트로 연결 요청을 보내면 ServerSocket은 이 연결 요청을 수락한다.
- ServerSocket은 특정 포트에 바인딩 된다. 클라이언트는 해당 포트로 서버에 연결하게 된다. 서로 다른 포트 번호는 각 프로토콜에 대한 서버로 연결을 분리할 수 있도록 한다.
- ServerSocket은 동시에 여러 클라이언트 연결을 관리할 수 있도록 연결 대기열을 관리한다. 이 대기열은 연결을 기다리는 클라이언트의 큐를 나타내며 서버는 대기열에서 연결을 하나씩 수락하고 처리할 수 있다.
- ServerSocket 클래스는 accept 메서드를 제공하여 클라이언트의 연결 요청을 수락하고 클라이언트와 통신할 수 있는 socket 객체를 반환한다. 서버는 이 socket을 사용하여 클라이언트와 데이터를 교환한다.
- ServerSocket은 보안 및 소켓 설정을 구성하는 데 사용되는 메서드와 옵션을 제공한다.

### Blocking vs Non-Blocking

[Blocking과 Non-Blocking](https://velog.io/@nandong1104/Blocking-vs-Non-Blocking-%EB%8F%99%EA%B8%B0-%EB%B9%84%EB%8F%99%EA%B8%B0#blocking-vs-non-blocking-1)은 주로 IO의 read, write에서 주로 사용되는 용어이다.

Blocking
- 요청한 작업을 마칠때까지 대기한다.
- 제어권이 호출된 친구에게 넘어가서 그 작업을 끝날때까지 갖고 있는다.
- return 값을 받아야만 끝나는 작업 방식이다.
- Thread 관점에서는, 요청한 작업이 끝날 때까지 계속 대기해야하는 방식이다.

Non-Blocking
- 요청한 작업을 마칠 수 없다면 완료되지 않았다는 상태와 함께 즉시 return 한다.
- 제어권을 호출자에게 바로 넘겨준다.
- 이전에 호출하고 결과를 기다리는 것이 아니라 다른 친구에게 작업을 시키고 호출자의 입장에서는 계속 다른 작업을 수행한다.
- Thread 관점으로 보면 하나의 Thread가 여러 개의 I를 처리 할 수 있다.

### Java HTTP Server