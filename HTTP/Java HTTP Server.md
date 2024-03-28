## ✔️ 키워드 정리 

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
- Thread 관점으로 보면 하나의 Thread가 여러 개의 IO를 처리 할 수 있다.

### Java HTTP Server

[Java HTTP Server](https://docs.oracle.com/javase/8/docs/jre/api/net/httpserver/spec/com/sun/net/httpserver/package-summary.html) 패키지를 사용하면 기본적인 웹 서버를 간단히 실행할 수 있다.



예시 코드는 다음과 같다.

```java
package _study;

import com.sun.net.httpserver.Headers;
import com.sun.net.httpserver.HttpExchange;
import com.sun.net.httpserver.HttpServer;

import java.io.IOException;
import java.io.InputStream;
import java.io.OutputStream;
import java.net.InetSocketAddress;
import java.net.URI;
import java.util.List;

public class App {

    public static void main(String[] args) throws IOException {
        App app = new App();
        app.run();

    }

    private void run() throws IOException {
        InetSocketAddress address = new InetSocketAddress(8080);
        HttpServer httpServer = HttpServer.create(address, 0);

        httpServer.createContext("/", exchange -> {
            // 1. Request
            String method = exchange.getRequestMethod();
            System.out.println("method: " + method);
            URI uri = exchange.getRequestURI();
            String path = uri.getPath();

            System.out.println("path: " + path);

            Headers headers = exchange.getRequestHeaders();
            for (String key : headers.keySet()) {
                List<String> values = headers.get(key);
                System.out.println(key);
            }

            InputStream inputStream = exchange.getRequestBody();
            String body = new String(inputStream.readAllBytes());

            System.out.println(body);

            // 2. Response
            String content = "Hello world \n";
            sendContent(exchange, content);
        });

        httpServer.createContext("/hi", exchange -> {
            String content = "wow hihi!! \n";
            sendContent(exchange, content);
        });
        httpServer.start();

    }

    private static void sendContent(HttpExchange exchange, String content) throws IOException {

        byte[] bytes = content.getBytes();

        exchange.sendResponseHeaders(200, bytes.length);

        OutputStream outputStream = exchange.getResponseBody();
        outputStream.write(bytes);
        outputStream.flush();
    }
}

```

### Java NIO

✨ [Java NIO](https://jenkov.com/tutorials/java-nio/buffers.html)(New Input Output)

Java에서의 NIO API는 기존 IO 패키지를 개선하기 위해 나온 패키지다.
Java는 JVM 위에서 동작하므로 주로 C/C++에 비하면 자바는 느리다고 인식되고 실제로도 그렇다고 한다.

Java NIO 버퍼는 NIO 채널과 상호작용할 때 사용된다. 데이터는 채널에서 버퍼로 읽혀지고 버퍼에서 채널로 쓰인다.<br/>
버퍼는 기본적으로 데이터를 기록하고 나중에 다시 읽을 수 있는 메모리 블록이다. 이 메모리 블록은 NIO 버퍼 객체로 래핑되어 메모리 블록 작업을 더 쉽게 해주는 메서드를 제공한다.

버퍼 사용법은 다음과 같다.

1. 버퍼에 데이터 쓰기
2. ```buffer.flip()```
3. 버퍼에서 데이터 읽기
4. ```buffer.close()```

### Java Lambda expression(람다식)

위에 코드 httpServer.createContext 부분에서 

```java
    httpServer.createContext("/hi", exchange -> {
        String content = "wow hihi!! \n";
        sendContent(exchange, content);
    });
```

이런식으로 작성하는데 ```->``` 기호를 사용하여 작성된 표현식이 람다식이다. 람다식은 반드시 함수형 인터페이스의 구현에만 사용할 수 있다

람다식은 다음과 같은 특징을 갖고 있다.

1. 람다식은 함수형 인터페이스를 구현할 때 사용한다.<br/>
    : 함수형 인터페이스는 추상 메소드가 하나만 존재하는 인터페이스를 의미한다. 그리고 람다식은 그 추상 메소드를 구현하는 역할을 한다. 반대로 함수형 인터페이스가 아닌 다른 변수에는 람다식을 사용할 수 없다.

2. 하나의 메서드이며, 메서드와 동일한 스택을 갖는다.<br/>
    : 람다식은 익명 메서드라고 불리기 때문에 일반적인 자바 메서드와 동일한 스코프를 갖게 된다.

3. 일급 객체로서 파라미터나 반환값 등으로 사용할 수 있다.<br/>
    : 자바에서 일급 객체는 변수의 할당, 파라미터, 반환 값으로 사용할 수 있어야한다.

### Java Functional interface(함수형 인터페이스)

함수를 일급 객체로 사용할 수 없는 자바 언어의 단점을 보완하기 위해 자바 8에서 ```java.util.function``` 패키지가 추가되었다.

Functional Interface는 일반적으로 구현해야 할 추상 메서드가 하나만 정의된 인터페이스를 의미한다.

위 코드에서는 다음과 같이

```java
 private static void sendContent(HttpExchange exchange, String content) throws IOException {

        byte[] bytes = content.getBytes();

        exchange.sendResponseHeaders(200, bytes.length);

        OutputStream outputStream = exchange.getResponseBody();
        outputStream.write(bytes);
        outputStream.flush();
    }
```

Functional Interface를 작성하여 사용했다.