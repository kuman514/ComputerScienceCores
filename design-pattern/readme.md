# 디자인 패턴 모음집

## 디자인 패턴 (Design Pattern)
- 디자인 패턴이란, 소프트웨어 디자인 과정에서 발생하는 공통된 문제에 대해 재사용이 가능한 해결책이다.
- 상황에 맞게 사용될 수 있는 문제들을 해결하는데 쓰이는 템플릿을 의미하며, 프로그래머가 소프트웨어 시스템을 설계할 때 직면하는 문제를 해결하는 형식화된 해결법이다.
- 소프트웨어 아키텍처와의 차이점?
  - 소프트웨어 아키텍처는 소프트웨어의 뼈대나 고수준의 기반을 담당하며, 디자인 패턴은 각각의 모듈들이 어떤 역할을 하는지나 클래스의 범위 또는 함수의 목적 등 코드 수준의 기반을 담당하고 있다.
  - 즉, 소프트웨어 아키텍처는 거시적인 관점에서의 설계, 디자인 패턴은 세부적인 관점에서의 설계라고 보면 될 것이다.

## SOLID

### Single Responsibility Principle (단일 책임 원칙)
- 소프트웨어 모듈은 변화를 일으키는 이유가 단 한 가지뿐이어야 한다.
- 모든 클래스는 단 하나의 책임만을 가지며, 그 책임을 모두 캡슐화해야 한다.
- 하나의 클래스에서 두 가지 이상의 책임을 가지면, 결합도가 높아져 유지보수가 어렵게 된다.

### Open/Closed Principle (개방-폐쇄 원칙)
- 확장에는 개방적이고 변경에는 폐쇄적이어야 한다.
- 확장에 개방적이라는게 무슨 의미?
  - 클래스를 상속(extends class)하거나 인터페이스를 구현(implements interface)함으로써 기능을 추가하는 것.
- 변경에 폐쇄적이라는게 무슨 의미?
  - 클래스 자체를 직접적으로 바꾸는 것을 지양하고 상속과 구현을 통해 기능을 추가하라는 것.

### Liskov Substitution Principle (리스코프 치환 원칙)
- 자식 클래스는 부모 클래스인 것 마냥 완전히 똑같이 다루어져야 한다.
- 자식 클래스는 부모 클래스의 행동을 파괴해선 안 된다.
- 예: Sparrow 클래스와 Ostrich 클래스가 Bird 클래스를 상속하고자 한다.
  - 이 때, Bird 클래스에 하늘을 난다는 fly 메소드가 있을 때, 날 수 없는 타조인 Ostrich 클래스가 이를 상속받으려면 fly 메소드를 파괴해야 한다.
  - 해결 방안으로, Bird 클래스 대신 이를 상속받는 FlyingBird 클래스에 fly 메소드를 부여하고, Ostrich 클래스는 Bird 클래스를, Sparrow 클래스는 FlyingBird 클래스를 상속받는다.

### Interface Segregation Principle (인터페이스 분리 원칙)
- 사용자들은 사용하지 않는 인터페이스를 강요받아선 안 된다.
- 예: Mechanic 클래스는 Car 클래스에 대해 repair 메소드를 제공받을 것인데, 이 때 Mechanic 클래스에 불필요한 sell같은 메소드가 Car 클래스에 있으면 안 된다.
  - 해결 방안으로, Car 클래스를 repair 메소드만 있는 Repairable 인터페이스와 sell 메소드만 있는 Sellable 인터페이스로 나누고, Mechanic 클래스에는 Repairable 인터페이스만 제공될 수 있도록 한다.
  - Repairable 인터페이스: repair(...) 메소드
  - Sellable 인터페이스: sell(...) 메소드
  - Car 클래스 implements Repairable, Sellable
  - Mechanic 클래스: repair(repairable: Repairable) { repairable.repair(...); }

### Dependency Inversion Principle (의존 역전 원칙)
- 고수준 모듈은 저수준 모듈에 의존하지 말아야 하고, 둘 다 추상 모듈에 의존해야 한다.
- 추상 모듈은 세부 모듈에 의존하지 말아야 하고, 세부 모듈은 추상 모듈에 의존해야 한다.

## 디자인 패턴 - 생성

### 싱글톤 패턴 (Singleton Pattern)

### 팩토리 메소드 패턴 (Factory Method Pattern)

### 프로토타입 패턴 (Prototype Pattern)

### 빌더 패턴 (Builder Pattern)

### 추상 팩토리 패턴 (Abstract Factory Pattern)

## 디자인 패턴 - 구조

### 어댑터 패턴 (Adapter Pattern)

### 브릿지 패턴 (Bridge Pattern)

### 컴포지트 패턴 (Composite Pattern)

### 데코레이터 패턴 (Decorator Pattern)

### 파사드 패턴 (Facade Pattern)

### 플라이웨이트 패턴 (Flyweight Pattern)

### 프록시 패턴 (Proxy Pattern)

## 디자인 패턴 - 행동

### 옵저버 패턴 (Observer Pattern)
- 객체를 관찰하는 옵저버들을 등록하여, 상태가 변화할 때마다 객체가 옵저버들에게 메소드 등을 통해 변화를 통지하는 방식의 패턴이다.
- 사용 예시: Redux, MobX 등의 상태 관리 라이브러리

### 책임 연쇄 패턴 (Chain Of Responsibility Pattern)

### 인터프리터 패턴 (Interpreter Pattern)

### 이터레이터 패턴 (Iterator Pattern)

### 중재자 패턴 (Mediator Pattern)

### 상태 패턴 (State Pattern)

### 전략 패턴 (Strategy Pattern)

### 템플릿 메소드 패턴 (Template Method Pattern)

### 비지터 패턴 (Visitor Pattern)

### 메멘토 패턴 (Memento Pattern)
