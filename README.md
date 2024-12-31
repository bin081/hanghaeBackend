![image](https://github.com/user-attachments/assets/4555e1ec-6dc7-4576-8890-41fe5c5b272f)
**과제 필수 사항**

- **`콘서트 예약 서비스`**를 구현해 봅니다.
- 대기열 시스템을 구축하고, 예약 서비스는 작업가능한 유저만 수행할 수 있도록 해야합니다.
- 사용자는 좌석예약 시에 미리 충전한 잔액을 이용합니다.
- 좌석 예약 요청시에, 결제가 이루어지지 않더라도 일정 시간동안 다른 유저가 해당 좌석에 접근할 수 없도록 합니다.


❓  [과제] 콘서트 예약 서비스
- 아래 5가지 API 를 구현합니다.
    - 유저 토큰 발급 API
    - 예약 가능 날짜 / 좌석 API
    - 좌석 예약 요청 API
    - 잔액 충전 / 조회 API
    - 결제 API
- 각 기능 및 제약사항에 대해 단위 테스트를 반드시 하나 이상 작성하도록 합니다.
- 다수의 인스턴스로 어플리케이션이 동작하더라도 기능에 문제가 없도록 작성하도록 합니다.
- 동시성 이슈를 고려하여 구현합니다.
- 대기열 개념을 고려해 구현합니다.

### **커밋 링크**
<!-- 
좋은 피드백을 받기 위해 가장 중요한 것은 코드를 작성할 때 커밋을 작업 단위로 잘 쪼개는 것입니다.
모든 작업을 하나의 커밋에 진행하고 PR을 하면 구조 파악에 많은 시간을 소모하기 때문에 절대로
좋은 피드백을 받을 수 없습니다.


필수 양식)
시퀀스 다이어그램 : 커밋 링크

예시)
동시성 처리 : c83845
동시성 테스트 코드 : d93ji3
-->
- 시퀀스 다이어그램 : 커밋 링크
---
### **리뷰 포인트(질문)**
- 리뷰 포인트 1
- 리뷰 포인트 2
<!-- - 리뷰어가 특히 확인해야 할 부분이나 신경 써야 할 코드가 있다면 명확히 작성해주세요.(최대 2개)
  
  좋은 예:
  - `ErrorMessage` 컴포넌트의 상태 업데이트 로직이 적절한지 검토 부탁드립니다.
  - 추가한 유닛 테스트(`LoginError.test.js`)의 테스트 케이스가 충분한지 확인 부탁드립니다.

  나쁜 예:
  - 개선사항을 알려주세요.
  - 코드 전반적으로 봐주세요.
  - 뭘 질문할지 모르겠어요. -->
---
### **이번주 KPT 회고**

### Keep
<!-- 유지해야 할 좋은 점 -->

### Problem
<!--개선이 필요한 점-->

### Try
<!-- 새롭게 시도할 점 -->