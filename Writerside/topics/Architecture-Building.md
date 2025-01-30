# Architecture Building
## Load Balancing
![LB.png](LB.png)
* 여러 서버에 트래픽을 분산
* 확장성을 얻을 수 있으며, 오토 스케일링이 가능해짐 (Scalability)
* 한 인스턴스가 에러가 나더라도 다른 서버로 요청을 보낼 수 있음 (HA)
* 처리량을 높게 유지할 수 있음 (Throughput)
* 유지 보수를 쉽게 할 수 있음 (Maintainability)
### DNS Load Balancing
![DNSLB.png](DNSLB.png)
* 하나의 DNS가 복수개의 IP 리스트로 매핑될 수 있는데 이를 롤링 제공하여 LB를 구현
* 헬스 체크를 진행이 어려워짐
* 서버로 요청이 보내지지 않을 수 있음
* 시스템 보안이 약해질 수 있음
  * 특정 서버로만 요청을 보낼 수 있음
### Hardware Load Balancing
* L4 장비를 이용하여 LB
* 헬스 체크가 가능함
### Software Load Balancing
* LB를 할 수 있는 프로그램을 이용
* [HAProxy](https://www.haproxy.org/), [Nginx](https://www.f5.com/go/product/welcome-to-nginx), 
## GSLB (Global Server Load Balancing)
![GSLB.png](GSLB.png)
* DNS 서비스와 HW/SW LB가 결합된 솔루션
* 요청된 사용자의 위치를 파악할 수 있음
  * 더 가까운 LB로 라우팅할 수 있음
* 또한 모니터링도 진행할 수 있음
* [Route 53](https://aws.amazon.com/route53/)
## Message Broker
![MESSAGE_BROKER.png](MESSAGE_BROKER.png)
* 메시지 버퍼링, 라우팅과 같이 비동기적인 통신을 할 수 있도록 하는 도구
* 트래픽이 급증할 경우 대기열을 만들 수 있다
* HA와 Scalability을 얻을 수 있다
* [Kafka](https://kafka.apache.org/), [RabbitMQ](https://www.rabbitmq.com/), [SQS](https://aws.amazon.com/sqs/)
## API Gateway
![GW.png](GW.png)
* 여러개로 쪼개져있는 API의 각각에 대해서 인증과 권한을 모두 구현하기에는 복잡함
* 따라서 API Gateway라는 것을 두어 인증 권한 관리를 통합할 수 있음
* 또한 목적에 따라 같은 API를 다른 서비스 API로 분기시킬 수 있음
  * 모바일, 데스크탑에 따른 분기로 다르게 처리할 수 있음
* 캐싱을 하여 더욱 빠르게 응답할 수 있음
* 통신 프로토콜을 바꿀 수도 있음(REST -> gRPC)
  * ![GWP.png](GWP.png)
* API Gateway는 다른 서비스로 라우팅하는 것을 목적으로 해야함
  * 비즈니스 로직이 들어가는 순간 장점이 사라짐
* API Gateway 자체가 장애 지점이 될 수 있음
  * 장애가 발생하면 시스템 전체가 발생하게 됨
* [Zuul](https://github.com/Netflix/zuul), [Amazon API Gateway](https://aws.amazon.com/api-gateway/)
## CDN (Content Delivery Network)
* Image, Text, HTML, Video와 같은 콘텐츠를 물리적으로 가까운 서버에서 가져옴
* [CloudFront](https://aws.amazon.com/cloudfront/), [CloudFlare](https://www.cloudflare.com/ko-kr/application-services/products/cdn/)
### Pull
![PULL.png](PULL.png)
* 어떤 미디어들이 캐싱 되어야 하는지 알려줘야 함
* 얼마나 자주 무효화 되어야 하는지 설정
* 처음 요청을 하면 그 후에 CDN에 캐싱이 됨
  * 그 다음 요청은 CDN에서 콘텐츠를 들고 옴
  * 만료되었다면 다시 서버에서 원본을 들고온 후 CDN에 캐싱
    * 같다면 만료시간만 변경
* 유지 관리를 많이 하지 않아도 됨
* 대부분 CDN에서 관리를 해줌
* 첫번째 사용자는 많은 시간이 걸림
* 원하는 버전이 곧장 반영되지 않음
### Push
![PUSH.png](PUSH.png)
* 콘텐츠를 직접 CDN에 수동 또는 자동으로 업로드 하거나 배포
* 일반적으로 긴 TTL을 설정
* 콘텐츠가 자주 변경되면 자주 푸시해야 함