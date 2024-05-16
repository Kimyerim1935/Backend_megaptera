## ✔️ 키워드 정리

### SOLID

프로그래머가 시간이 지나도 유지 보수와 확장이 쉬운 시스템을 만들고자 할 때 이 원칙들을 함께 적용할 수 있다.

SOLID 원칙들은 소프트웨어 작업에서 프로그래머가 소스 코드가 읽기 쉽고 확장하기 쉽게 될 때까지 소프트웨어 소스코드를 리팩토링하여 코드의 문제를 제거하기 위해 적용할 수 있는 지침이다.

👉 엉클 밥이 2003년에 <클린 소프트웨어>에서 5가지 객체지향 설계 원칙을 정리했고, 마이클 페더스가 순서를 조금 바꿔서 SOLID라고 부르기 시작함.

SRP (Single Responsibility Principle, 단일 책임 원칙)
OCP (Open-Closed Principle, 개방-폐쇄 원칙)
LSP (Liskov Substitution Principle, 리스코프 치환 원칙)
ISP (Interface Segregation Principle, 인터페이스 분리 원칙)
DIP (Dependency Inversion Principle, 의존관계 역전 원칙)

### SRP (Single Responsibility Principle, 단일 책임 원칙)

하나의 클래스는 하나의 책임만 가져야 한다.

### OCP (Open-Closed Principle, 개방-폐쇄 원칙)

소프트웨어 요소는 확장성이 있어야 하지만 변경에는 닫혀 있어야 한다.

### LSP (Liskov Substitution Principle, 리스코프 치환 원칙)

프로그램의 객체는 프로그램의 정확성을 깨뜨리지 않으면서 하위 타입의 인스턴스로 바꿀 수 있어야 한다.

### ISP (Interface Segregation Principle, 인터페이스 분리 원칙)

특정 클라이언트를 위한 인터페이스 여러 개가 범용 인터페이스 하나보다 낫다.

### DIP (Dependency Inversion Principle, 의존관계 역전 원칙)

프로그래머는 추상화에 의존해야하고, 구체화에 의존하면 안된다.