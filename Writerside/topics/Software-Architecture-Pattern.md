# Software Architecture Pattern
## Multi-Tier Architecture
* 각 계층마다 별도의 기기에서 실행되는 것을 의미
* 시스템 계층을 논리적, 물리적으로 나눈 것
  * 논리적 분리는 각 계층의 책임 범위를 결정함
  * 물리적 분리는 각 계층이 배포, 업그레이드, 확장하게 함
* 각 계층을 독립적으로 개발, 업데이트 확장을 할 수 있음
* 인접한 계층과 짝을 이루는 애플리케이션들은 일반적으로 REST로 서로 응답함
### Multilayer Architecture
* 단일 어플리케이션 안에서 여러 논리적 계층이나 모듈로 나누는 것을 의미
## Three-Tier Architecture (Monolithic Architecture)
![MONOLITHIC.png](MONOLITHIC.png)
* 대부분의 웹 기반 서비스에 적합
* 수평 확장에 용이
* 논리 계층이 하나로 집약되어있다는 부분은 단점 (`Monolithic`)
* `Presentation Tier`와 `Logic Tier` 사이에 `API Gateway Tier`가 삽입될 수 있음
### Presentation Tier
* 웹페이지, 모바일 앱, 데스크톱 앱과 같은 GUI 애플리케이션
* 비즈니스 로직을 일반적으로 포함하지 않음
* 사용자가 비즈니스 규칙을 보면 안됨
### Logic(Application) Tier
* 모든 기능을 담당하는 비즈니스 로직 계층
### Data Tier
* 파일, DB와 같은 저장소
* 사용자 데이터나 비즈니스 데이터를 저장하고 유지

## Microservice Architecture
![MICRO_SERVICE.png](MICRO_SERVICE.png)
* 비즈니스 로직을 독립적으로 배포된 서비스로 조직
* 각 서비스가 각 하나의 도메인, 리소스, 액션을 맡아야 함
* 서비스마다 다른 DB를 사용해야 할 것임


## Event-Driven Architecture
![EVENT_DRIVEN.png](EVENT_DRIVEN.png)
* 각각의 마이크로서비스간 통신에 동기식 명령 대신 이벤트 기반으로 처리
* 각각은 메시지 브로커를 사용하여 연결
  * 의존성을 줄일 수 있게 됨
  * 단순히 이벤트만 발행하면 해당 이벤트를 컨슘하는 곳은 해당 부분을 처리
### Event Sourcing Pattern
![EVENT_SOURCING.png](EVENT_SOURCING.png)
* 모든 불변 이벤트에 대해서 원하는 만큼 저장하여 DB 없이도 리플레이 가능
* 중간에 스냅샷을 두어 더욱 빠르게 조회 가능
### CQRS Pattern
![CQRS.png](CQRS.png)
* C(Command), Q(Query), R(Responsibility), S(Segregation)
* 일기와 업데이트 작업을 DB를 분리하여 수행
  * 업데이트 발생 시 메시지 브로커를 통하여 읽기 DB에도 반영
* 각각의 마이크로 서비스에서 변경될 때 마다 해당 변경된 것을 조인 전용 DB에 저장
  * 조인이 필요할 때마다 해당 전용 DB를 보게끔 하여 별도의 서비스에 질의를 하지 않아도 됨