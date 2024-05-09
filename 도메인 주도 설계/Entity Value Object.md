### 전술적 설계 (Tactical Design)

[Tactical Design](https://thedomaindrivendesign.io/what-is-tactical-design/#google_vignette)는 도메인 모델 구축에 사용되는 일련의 기술 리소스이며, 이런 리소스는 단일 경계 컨텍스트에서 작업하려면 적용되어야 한다.

전술적 설계는 빌딩 블록을 사용하여 도메인 모델을 생성하는 데 도움이 된다.

### 엔티티 (Entity) vs 일반적으로 이야기하는 개체 (Entity)

OOP에서 대부분의 객체는 속성이 아니라 연속성, 식별성에 따라 정의된다.

식별자(Identifier)가 존재하고, 이를 통해 동일성(Identity)을 확인한다면 Entity라고 할 수 있다.

### 값 객체 (Value Object, VO)

Value Object는 속성을 통해 동등성(Equality)을 판단한다.<br/> 
Value Object는 항상 Java의 equals 메서드를 구현해야 한다. 또한, 예측 가능성을 높이고 혼란을 막기 위해, 가능하면 불변 객체로 만들어야 한다. 

Java 14 이상이라면 record가 이를 간단히 지원한다(다만, 아직은 JPA와 함께 사용하기 어렵다).

### 동일성(Identity)과 동등성(Equality)

[Identity](https://en.wikipedia.org/wiki/Identity_document)는 개인을 데이터베이스에 있는 개인 정보에 연결하는 데 사용된다.

반면에, [Equality](https://en.wikipedia.org/wiki/Equality)는 같은 가치를 지닌다는 사실을 의미한다.

✨ Reference

https://medium.com/@cangut/domain-driven-design-part-ii-tactical-design-16bc527c6263<br/>
