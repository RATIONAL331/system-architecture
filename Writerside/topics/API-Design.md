# API Design
* 고객들은 우리가 만든 API를 통하여 그들의 비즈니스를 향상할 수 있음
* 고객들이 API의 구현이 내부적으로 어떻게 되어있는지 몰라도 됨
* 또한 우선 정의를 해둔다면 추후에 개발을 진행하더라도 고객이 기다리지 않게 할 수 있음
## RPC
![RPC.png](RPC.png)
* 원격서버에 프로시져를 호출
  * 네트워크 통신의 추상화
* 클라이언트가 보기에는 로컬 메서드를 호출하는 것과 똑같음
  * 실제로는 네트워크를 통한 호출
  * 속도가 느리거나, 응답에 실패할 수 있음을 기억해야 함
* 3개의 컴포넌트가 필요함
  * IDL(Interface Description Language)
  * Server Stub
  * Client Stub
* 백엔드 시스템간 통신할 때 흔히 사용됨
* 쿠키, 헤더와 같은 정보를 같이 이용하고 싶다면 RPC는 적절한 선택지는 아님
* [gRPC](https://grpc.io/), [Apache Thrift](https://thrift.apache.org/tutorial/), [RMI](https://docs.oracle.com/javase/tutorial/rmi/) 와 같은 도구들이 존재함
## REST
* 반드시 Stateless 해야하며, 각각의 메시지는 이전 요청과 별개로 이루어저야 함
* `/{Collection}/{Simple}/{Collection}/{Simple}`와 같은 형태로 구조화
* 명사로만 이름을 지정하는 것이 좋음
  * 추상적인 명사는 피해야 함