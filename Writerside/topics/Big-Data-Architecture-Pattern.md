# Big Data Architecture Pattern
## Big Data
### Volume
* Process, Store, Analyze 하기 위한 데이터양이 주로 하루 동안 테라바이트, 페타바이트 이상
### Variety
* 기존에는 정형적 데이터를 이용했지만, 많은 데이터 소스에서 비정형적 데이터도 같이 처리
### Velocity
* 매우 빠른 속도로 데이터가 인입됨

## Big Data Processing
### Batch Processing
![BATCH.png](BATCH.png)
* 분산 데이터 및 파일시스템에 데이터를 추가하는 형태로 저장
* 각각의 파일을 개별로 처리하지 않고 묶어서 수행
* 검색 엔진과 같은 서비스에서 전체 데이터 세트를 주기적으로 크롤링하여 사용자에게 제공
* 고가용성을 보장
  * 사용자는 기존에 이미 처리되었던 작업만 보면 됨
* 일괄적인 처리는 효율적인 처리를 하게끔 도와줌
* 그렇지만 실시간 현황을 파악하기 힘듬
### Real Time Processing
![REALTIME.png](REALTIME.png)
* 메시지 브로커와 같은 것을 사용하여 실시간 쿼리를 가능하게끔 하는 처리 구조
* 시스템에 유입되는 데이터를 즉시 파악할 수 있음
* 복잡한 분석을 진행하기 어려움
* 각기 다른 시간에 발생하는 다른 이벤트와의 결합이 힘듬

## Lambda Architecture
![LAMBDA.png](LAMBDA.png)
* 일괄 처리와 실시간 처리의 하이브리드 모델
### Batch Layer
* 일괄 처리를 위한 성격과 유사
* 데이터 세트를 관리하며 데이터를 추가하는 역할
* 배치 뷰를 사전에 계산
### Speed Layer
* 실시간 처리를 위한 성격과 유사
* 배치 계층에서 발생하는 지연을 보완
* 최신의 데이터만 처리하여 실시간 뷰만 표현
* 복잡한 뷰 또는 종합적인 결과를 내지는 않음
### Serving Layer
* 배치 뷰와 실시간 뷰를 합친 결과를 반환하는 레이어
* Ad-Hoc 쿼리에 응답