# Software Architecture & System Design
> The Software architecture of a system is a high-level description of the system's structure,
> its different components, 
> and how those components communicate with each other to fulfill the system's requirements and constraints.
* 고수준의 시스템 구조
  * 시스템을 이해하기 위한 중요한 구송 요소만 설계
  * 자세한 수행 과정은 정의 하지 않는 추상화
  * 실행하기 위한 기술 및 프로그래밍 언어들은 아키텍처가 아닌 구현의 일부에 해당
* 각기 다른 구성 요소와 그 요소간의 관계를 표현
  * 구성 요소란 행위나 API를 정의하는 블랙박스를 의미
  * 구성 요소 자체만으로 복잡하다면 재귀적으로 관계를 다시 표현할 수 있음
* 시스템의 요구 사항과 제약 사항을 만족해야 함
  * 모든 구성 요소들이 기능을 위해 어떻게 결합 해야하는지 나타내야 함
  * 시스템 제약 조건으로서 해서는 안되는 것을 안 하도록 해야 함