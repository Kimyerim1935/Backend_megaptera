## ✔️ 키워드 정리

### 관심사의 분리

[관심사 분리](https://ko.wikipedia.org/wiki/%EA%B4%80%EC%8B%AC%EC%82%AC_%EB%B6%84%EB%A6%AC)는 컴퓨터 프로그램을 구별된 부분으로 분리시키는 디자인 원칙으로, 각 부문은 개개의 관심사를 해결한다.

관심사의 분리는 프로그램을 관심사 별로 쪼개서 가능하면 한 번에 한 가지 걱정만 함으로써 프로그램 개발과 유지보수 시의 복잡성을 줄이자는 것이다. 관심사의 분리가 잘 이뤄지면, 개별 부문을 이해하기 쉽고, 각 부문을 재사용할 수 있게 되며, 한 부문을 개선하거나 수정할 때 다른 부문에 대해 자세히 알 필요가 없어지고, 다른 부문이 변하는 것에도 신경 쓸 필요가 없어지는 장점이 있다.

### 응집도

[응집도](https://en.wikipedia.org/wiki/Cohesion_(computer_science))는 모듈 내부의 요소가 함께 속해 있는 정도를 나타낸다. 

높은 응집력은 견고성, 신뢰성, 재사용성 및 이해 가능성을 포함한 여러가지 바람직한 소프트웨어 특성과 연관되어 있기 때문에 응집력이 높은 모듈이 선호되는 경향이 있다. 낮은 응집력은 유지 관리, 테스트, 재사용 등 바람직하지 않은 특성과 관련이 있다.

객체 지향 프로그래밍에서는 클래스를 제공하는 메서드가 여러 측면에서 유사하면 클래스의 응집력이 높다고 한다. 응집력이 높은 시스템에서는 코드 가독성과 재사용성이 향상되는 동시에, 복잡성은 관리 가능하게 유지된다.

### 결합도

[결합도](https://en.wikipedia.org/wiki/Coupling_(computer_programming))는 모듈 간의 상호 의존성 정도를 나타낸다. 일반적으로 응집도와 대조된다. 낮은 결합도는 높은 응집도와 상관관계가 있는 경우가 많다.

낮은 결합도는 잘 구조화된 컴퓨터 시스템과 좋은 디자인의 표시로 간주되는 경우가 많으며, 높은 응집력과 결합되면 높은 가독성과 유지 관리성이라는 일반적인 목표를 지원한다.

일반적으로 모듈 간의 상호작용이 필요한 경우에만 결합도를 높이고, 그 외의 경우에는 낮은 결합도를 유지하는게 좋다.

### Layered Architecture

계층화된 아키텍처 패턴내의 구성 요소는 수평 계층으로 구성되며, 각 계층은 애플리케이션 내 특정 역할을 수행한다.

계층형 아키텍처 패턴의 강력한 기능 중 하나는 구성 요소 간의 관심사를 분리하는 것이다. 특정 레이어 내의 구성 요소는 해당 레이어와 관련된 로직만 처리한다.

`Layered Architehcture`의 목적은 각 레이어들이 특정 고나심사와 관련된 개체만을 포함하도록 만듦으로써 전체적인 시스템의 결합도를 낮추고, 개발자의 인지 과부화를 방지하며 재사용성을 높이고 유지보수성을 향상시키는 것이다.

### UUID

[UUID(Universally unique identifier)](https://ko.wikipedia.org/wiki/%EB%B2%94%EC%9A%A9_%EA%B3%A0%EC%9C%A0_%EC%8B%9D%EB%B3%84%EC%9E%90)는 소프트웨어 구축에 쓰이는 식별자 표준이다.

`123e4567-e89b-12d3-a456-426614174000` 이런식으로 표현된다.

네트워크 상에서 서로 모르는 개체를 식별하고 구별하기 위해서는 각각 고유한 이름이 필요하다.

컴퓨터 시스템은 매우 큰 난수를 사용해 로컬에서 UUID를 생성한다. 이론적으로 ID는 전역적으로 고유하지 않을 수 있지만, 중복 가능성은 거의 없다.

이런식으로 id를 생성하면 된다.

```java
 @PostMapping
   @ResponseStatus(HttpStatus.CREATED)
   public PostDto create(@RequestBody PostDto postDto) {
       String id = UUID.randomUUID().toString().replace("-", "");
       
       postDto.setId(id);
       postDto.add(postDto);

       return postDto;
   }
```

ULID(Universally Unique Lexicographically Sortable Identifier)라는것도 있는데, 대소문자를 구별하지 않는 시간을 나타내는 26자 글자와 16자의 임의의 값으로 구성되어 있다.

ULID는 생성 순서를 밀리세컨 단위로 기록할 수 있어서 생성 순서대로 정렬을 할 때 편하다.

[ULID Creator](https://github.com/f4b6a3/ulid-creator)를 사용하면 ULID를 쉽게 생성할 수 있다.


```java
// build.gradle에 추가
implementation 'com.github.f4b6a3:ulid-creator:5.1.0'

// Controller
 @PostMapping
   @ResponseStatus(HttpStatus.CREATED)
   public PostDto create(@RequestBody PostDto postDto) {
       String id = UlidCreator.getUlid().toString();

       postDto.setId(id);
       postDto.add(postDto);

       return postDto;
   }
```

✨Reference

https://medium.com/@segene99/%EA%B7%B8%EB%9E%98%EC%84%9C-%EC%96%BC%EB%A7%88%EB%82%98-%EC%9D%91%EC%A7%91%EA%B3%BC-%EA%B2%B0%ED%95%A9%EB%90%98%EC%96%B4%EC%95%BC-%EB%90%98%EB%8A%94%EA%B1%B0%EC%95%BC-31f24d70334c<br/>
https://msolo021015.medium.com/layered-architecture-deep-dive-c0a5f5a9aa37