### 상황
 - 이클립스와 달리 인텔리제이에서는 이미 component에 등록된 것을 @Autowired하려면
 - **"Could not autowire. No beans of {클래스명} type found"** 라는 에러가 발생한다.

### 원인
 - 인텔리제이가 버그로 인식을 가끔씩 못한다는 말도 있고,([인프런 답변](https://www.inflearn.com/questions/170577))
 - 생각엔, 이미 컴포넌트에 등록이 되어있으니까, Autowired할 때 스캔하지 않고 생략해버려서 그런게 아닐까?
 - Autowired에 대한 공부가 좀 더 필요하다...

### 해결
 - 컴파일 및 서버 실행에는 문제가 없지만, [컴포넌트스캔]()으로 수정할 수 있다.
 - @ComponentScan("{해당 클래스가 존재하는 패키지명}")으로 해결.
