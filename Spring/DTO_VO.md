### DTO와 VO
1. DTO (Data Transfer Object)
	+ 데이터 전달용
	+ 데이터를 전달하기 위해 사용하는 객체(=데이터를 담아서 전달하는 바구니)
	+ Controller(Web layer) 와 Service(Service layer) 사이에서
	+ 특성
    - 오직 getter/setter 메서드만 가진다.
    - 다른 로직은 갖지 않는다(데이터 전달만 담당하므로)
    - setter가 잇으면 데이터가 가변적... --> get만 있으면 분변객체가 됨
    - 속성값이 모두 같다고 같은 객체가 아니다.
  
2. VO(Value Object)
	+ 값 표현용 (속성값이 같으면 같은 객체이다 --> hash와 equalto를 overriding 해주어야함)
	+ 값 그 자체를 표현하는 객체
	+ **반드시 불변**이어야 하므로 setter는 없음
	+ 다른 로직을 가질 수 잇음
---
*[10분 테코톡] 인비의 DTO vs VO*
