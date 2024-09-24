# 소프트웨어 아키텍처 모음집

## 소프트웨어 아키텍처 (Software Architecture)
- 소프트웨어 아키텍처란, 소프트웨어 시스템의 구조이자, 소프트웨어 시스템 제작에 관한 규칙이다.
- 각 구조는 소프트웨어 요소, 요소 간의 관계, 요소와 관계의 속성으로 이루어져 있다.
- [위키피디아 원문](https://en.wikipedia.org/wiki/Software_architecture)
  - Software architecture is the set of structures needed to reason about a software system and the discipline of creating such structures and systems. Each structure comprises software elements, relations among them, and properties of both elements and relations.

## 아키텍처 패턴

### MVC 패턴 (Model-View-Controller Pattern)
- 모델, 뷰, 컨트롤러로 이루어진 패턴
  - 모델: 앱에 필요한 모든 데이터와 정보를 담고 있는 부분으로, 데이터와 정보를 가공하여 뷰에 전달하는 부분이다.
  - 뷰: 사용자에게 직접 보여지는 부분으로, 텍스트 인풋이나 버튼 등등을 통해 사용자로부터 입력을 받고, 텍스트나 이미지 등등을 통해 사용자에게 화면으로 출력을 한다.
  - 컨트롤러: 사용자의 조작이 감지되었을 때 구현된 핸들러를 통해 변경해야 할 데이터를 모델(이나 뷰)에 통지하는 부분이다.
- 사용 예시: Angular

### MVVM 패턴 (Model-View-Viewmodel Pattern)
- 모델, 뷰, 모델뷰로 이루어진 패턴
  - 모델: 앱에 필요한 모든 데이터와 정보를 담고 있는 부분으로, 데이터와 정보를 가공하여 뷰에 전달하는 부분이다.
  - 뷰: 사용자에게 보여지는 부분으로, UI를 담당하고 있다.
  - 모델뷰: 뷰가 UI만 담당할 수 있도록, 일대다 관계로 연결된 여러 모델로부터 데이터를 받아와 가공하여 뷰에 전달하는 역할을 하는 부분이다.

### 레이어드 패턴 (Layered Pattern)
- 역할에 따라 독립된 모듈로 나뉘어 층층히 의존도에 따라 연결되어 전체 시스템을 구성하는 패턴.
- 계층
  - 표현 계층 (Presentation Layer)
  - 비즈니스 계층 (Business Layer)
  - 지속 계층 (Persistence Layer)
- 핵심 요소
  - 단방향 의존성: 각 레이어는 자기의 하위 레이어에만 의존한다.
  - 레이어 역할 분리: 각 레이어는 자기의 역할이 명확하게 구분된다.
- 백엔드 API를 개발할 때 널리 쓰이는 패턴 중 하나이기도 하다.

### 마스터 슬레이브 패턴 (Master-Slave Pattern)

### 클라이언트 서버 패턴 (Client-Server Pattern)

### 파이프 필터 패턴 (Pipe-Filter Pattern)

### 브로커 패턴 (Broker Pattern)

### 블랙보드 패턴 (Blackboard Pattern)

### 인터프리터 패턴 (Interpreter Pattern)

### 이벤트 버스 패턴 (Event-Bus Pattern)

### 피어 투 피어 패턴 (Peer To Peer Pattern)
