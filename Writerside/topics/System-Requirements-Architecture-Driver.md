# System Architecture Driver

## Architecture Driver
* 클라이언트를 위해 만들어야 할 항목을 파악하로 정리하는 것
* 클라이언트들은 무엇을 원하는지 정확히 알지는 못한다
  * 실제로 그들은 무엇을 해결해야 하는지를 더 정확히 안다.

### Feature(시스템 기능)
* 기능적 요구사항
* 시스템이 수행해야하는 것
  * 예를 들어 `검색을 하였을 때 이에 맞는 상품 결과가 나옴`
* 요구 사항을 수집하는 효과적인 방법
  * Use Cases(사용 사례)
    * 요구사항을 정리한 시나리오
  * User Flows(사용자 흐름)
    * Use Case를 더욱 세밀하게 사용 사례를 시각화
#### 요구사항 수집
![SEQUENCE_DIAGRAM.png](SEQUENCE_DIAGRAM.png)
1. 모든 사용자 및 액터를 명시
2. 사용 사례 및 시나리오를 모두 설계
3. 작업의 흐름이나 시스템에서의 액터간 상호작용을 시각화
   * Action, Data를 기준으로 시각화
   * 일반적으로 UML을 사용하며 시퀀스 다이어 그램으료 표시

### Quality Attributes(품질 속성)
* 기능적 요구사항이 아닌 요구하는 수준의 품질 유지
* 시스템이 잘 작동할 수 있는 품질
  * 예를 들어 `검색을 하였을 때 100ms 이내의 속도로 결과가 나옴`
* 시스템이 꼭 가져야 하는 특성
  * 확장성
  * 가용성
  * 보안성
  * ...
* 품질 속성 고려 사항
  * Testability and Measurability(측정 가능해야 하며, 테스트가 가능해야 함)
  * Trade offs(어떤 속성들은 성취하기 매우 어려울 수 있으며 때로는 타협하여 적절한 속성을 선택해야 함)
    * 보안과 성능을 둘 다 챙기기 어려울 때 어떤 하나를 타협해야 함
  * Feasibility(실현 가능해야 함)
    * 미국과 한국 사이의 통신 시간을 10ms 이내로 줄이는 것은 불가능

### Constraints(시스템 제약 사항)
* 마감 시간, 예산, 계약 관계, 개발자 수 등
* 프로그래밍 언어, DB의 선택 등도 제약 사항에 포함될 수 있음
* 꼭 부정적인 것은 아님, 시스템 설계의 바탕이 될 수 있음