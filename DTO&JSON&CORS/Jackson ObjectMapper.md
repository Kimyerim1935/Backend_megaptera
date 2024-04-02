## ✔️ 키워드 정리

### Jackson ObjectMapper 란

Jackson ObjectMapper 클래스는 Java에서 Jackson을 사용하여 JSON을 구문 분석하는 가장 간단한 방법이다.

Jackson은 문자열, 스트림 또는 객체 그래프를 생성할 수 있다. JSON을 Java 객체로 구문 분석 하는 것은 JSON에서 Java 객체를 역직렬화하는 작업이라고도 한다.

writeValue API를 사용하면 모든 Java 객체를 JSON 출력으로 직렬화할 수 있다.

```Java
ObjectMapper objectMapper = new ObjectMapper();
Car car = new Car("yellow", "renault");
objectMapper.writeValue(new File("target/car.json"), car);

```

해당 파일을 출력하면 `{"color":"yellow","type":"renault"}` 이런 값이 나온다.

ObjectMapper 클래스의 writeValueAsString 및 writeValueAsBytes 메서드는 Java 객체에서 JSON을 생성하고, 생성한 JSON을 문자열이나 바이트 배열로 반환한다.

ObjectMapper 클래스를 사용하여 JSON 문자열을 Java 객체로 변환할 수 있다.

```java
String json = "{ \"color\" : \"Black\", \"type\" : \"BMW\" }";
Car car = objectMapper.readValue(json, Car.class);
```

이외에도 다양한 예제가 [공식문서](https://www.baeldung.com/jackson-object-mapper-tutorial)에 있으니 참고하면 좋을 것 같다.

### ObjectMapper

ObjectMapper란 JSON 형식을 사용할 때, 응답들을 직렬화하고 요청들을 역직렬화할 때 사용하는 기술이다.

사용법은 다음과 같다.

```java
@Getter // Object -> String 문자열로 바꿀 때 필요!
class Car {
 private String name;
 private String color;

 public Car(String name, String color) {
  this.name = name;
  this.color = color;
 }

 public Car() { // String 문자열 => Object로 바꿀 때 필요!
  this.name = null;
  this.color = null;
 }
}

// Object에서 String으로 변경
ObjectMapper mapper = new ObjectMapper();
Car car = new Car("K5", "gray");

String text = mapper.WriteValueAsString(car); //{"name":"K5","color":"gray"}

// String 문자열에서 Object로 변경
Car carObject = mapper.readValue(text, Car.class); //Car{name='k5',color='gary'}
```

### @JsonProperty

[@JsonProperty](https://www.baeldung.com/jackson-annotations) 주석을 추가하면 JSON의 속성 이름을 나타낼 수 있다.

```java
    @JsonProperty("body")
    public String getContent() {
        return content;
    }
```

이런식으로 작성하면 된다.
