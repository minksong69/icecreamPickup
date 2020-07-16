# icecreamPickup

## 시나리오

1. 고객이 매장과 상품을 선택하여 아이스크림 주문을 한다.
1. 고객이 결제를 한다.
1. 결제승인이 완료되면 매장에 주문접수요청 알림이 된다.
1. 매장에서는 주문접수를 받아 아이스크림 포장을 한다.
1. 매장에서 주문접수를 하면 고객에게 알림을 보낸다.
1. 포장이 완료되면, 고객에게 픽업 알림을 보낸다.
1. 고객은 포장 완료 전까지 주문 취소를 할 수 있다.
1. 주문취소가 되면 결제승인취소가 된다.
1. 주문취소가 되면 매장에서도 주문취소 처리한다.
1. 고객이 픽업하면, 해당 주문은 최종 완료된다.
1. 고객은 픽업완료 후 리뷰를 작성할 수 있다.(개발에서는 적용 제외)


## 비기능적 요구사항
 트랜젝션
  - 결제가 되지 않으면 주문접수가 되지 않음(결제동기호출)
 장애 처리
  - 주문접수는 다른 서비스와 관계없이 항상 처리 가능하도록 한다.
  - 결제시스템이 과중되면 사용자를 잠시동안 받지 않고 결제를 잠시후에 하도록 유도한다 Circuit breaker, fallback
 성능
  - 매장별 주문현황을 집계하여 볼 수 있도록 한다.(CQRS)
  
## 이벤트스토밍 결과 모델
http://msaez.io/#/storming/tumGnckjgrc4UVXq2EBT4EFYhnT2/mine/2917e88a6d4dba0647c591d614a87766/-MBZKH7RqZmoriv609f3

### 설계 중 이벤트스토밍
![image](https://user-images.githubusercontent.com/56263370/87503600-9fb8a780-c69f-11ea-9920-d4f8add392d6.png)

### 이벤트스토밍 최종 결과
![image](https://user-images.githubusercontent.com/56263370/87503406-186b3400-c69f-11ea-82e1-3acb967c40d5.png)

