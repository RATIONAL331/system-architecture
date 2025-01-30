# Crucial Quality Feature

## Performance
* 성능이 떨어지면 다음의 원인이 있을 수 있음
  * High usage CPU
  * High usage Memory
  * Many Network Connection
  * Message Queue Capacity
### Response Time
* 고객이 요청하고 응답을 받기까지의 시간
  * 처리시간 + 대기 시간(지연 시간)
* 응답 시간이 곧 성능에 대한 시간은 아님
### Throughput
* 시스템이 실정한 시간 동안 처리할 수 있는 작업의 양 또는 데이터의 양
* 시스템 성능을 측정하는 가장 중요한 척도

## Scalability
* 시스템에 리소스를 추가함으로써 증가하는 작업량을 처리하는 시스템 능력의 판단 척도
* 시스템이 느려지는 시점을 성능 저하 지점이라고 부름
* 기본적으로 투입되는 양 대비 성능이 정비례하면 아주 좋음
  * 그렇지만 일반적으로 로그 형태를 띄며, 더 투입되었을 때 하락한다면 매우 좋지 않음
### Vertical Scalability
* 시스템의 성능을 높이는 방법
* 코드 수정이 필요 없음
* 마이그레이션이 편리함
* 한계가 있음
* 고가용성과 내결함성을 갖추지 못함

### Horizontal Scalability
* 시스템을 여러개의 인스턴스로 확장하는 방법
* 확장성에 제한이 없음
* 고가용성과 내결함성을 갖출 수 있음
* 코드를 대대적으로 바꿔야 함
* 더 복잡하고 조정을 위한 오버헤드가 필요함

### Team/Organizational Scalability
* 투입되는 개발자가 많아지면 많아질 수록 시스템을 수정하기 어려워짐
  * 더 많은 회의
  * 더 많은 코드 충돌
  * 더 많은 시간의 온보딩
  * 테스트가 더욱 힘들어지며 느려짐
  * 출시할 때 마다 더 취약해 짐
* 작업하는 코드베이스를 모듈로 분리하거나 라이브러리로 단위로 분리하여 개발하여 최대한 간섭을 줄임

## Availability
* 사용자가 서비스를 접근 가능한 시간을 비율로 표기한 것

### Terms
* Uptime: 사용자가 서비스를 정상적으로 이용할 수 있는 시간
* Downtime: 사용자가 서비스를 이용하지 못하는 시간
* Availability: Uptime / (Uptime + Downtime)
* Availability: MTBF / (MTBF + MTTR)

### MTBF(Mean Time Between Failures)
* 시스템의 평균 가동 시간
* 여러개의 하드웨어를 사용할 때 유용함
  * 각자의 하드웨어는 수명이 존재함
### MTTR(Mean Time To Recovery)
* 문제를 발견하고 복구하는 평균 시간

## HA(High Availability) & Fault Tolerance
* 인적 오류(배포 순서 문제 등등)
* 소프트웨어 오류(NPE, 가비지 컬렉션 등등)
* 하드웨어 문제(하드웨어 수명)
### Fault Tolerance
* 오류가 발생하더라도 시스템이 정상적으로 작동하도록 유지하는 기능

#### Failure Prevention
* 시스템의 오류를 일으키는 요인들을 제거
* 복제(Replication) 또는 중복(Redundancy)을 이용도록 함
* 실패할 때 성공할 때 까지 재시도 하는 방법도 포함
##### Active-Active Architecture
* 모든 노드들이 동기화 하게끔 하여 HA를 구성하는 방법
* 더 많은 트래픽을 처리할 수 있고 기본적으로 수평 분할과 똑같다
* 동기화되게 유지되는 것이 쉽지 않으며 오버헤드 발생
##### Active-Passive Architecture
* 한 기기로만 요청을 보내고 나머지 노드들은 이를 복사만 함
* 시스템 확장 능력을 잃게 된다
* 구현이 쉽다
#### Failure Detection
* 헬스 체크: 메시지를 직접 주고 받으면서 확인하는 방법
* 하트 비트: 인스턴스가 하트 비트 시그널을 주지 않으면 해당 인스턴스가 오류가 발생했다고 가정

#### Recovery From Failure
* 인스턴스 재시작, 롤백과 같은 방법으로 온전한 상태로 되돌림

## SLA(Service Level Agreement)
* 가용성 및 성능, 데이터 보존성, MTTR과 같은 것을 합의하는 법적 계약
* 이를 위반할 경우 페널티 또는 보상이 필요할 수 있음

## SLO(Service Level Objectives)
* 서비스가 충족해야하는 목표값
* 시스탬 내의 특정 척도에 대한 SLA 내에서의 개별 협의
* SLA가 없더라도 SLO는 일반적으로 존재해야 함

## SLI(Service Level Indicators)
* 서비스 수준 목표를 이행하는데 관련된 실제 값
* 추후에 SLO값들과 비교할 수 있음
* 측정이 가능해야지 해당 값을 추출할 수 있음