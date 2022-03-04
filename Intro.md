### CPU의 구성 : ALU(연산장치) + Control Unit(제어장치) + Registers(PC,IR,MAR,MBR)(레지스터)
+ Registers
  - PC : 다음에 수행할 명령어
  - IR : 현재 수행중인 명령어
  - MAR : Read/Write한 데이터의 주소값
  - MBR : Read한 데이터 값 or Write할 데이터 임시저장
  - AL : 연산 결과값
### Process 메모리 할당 :  CODE + DATA + HEAP + STACK
+ CODE : 프로그램 코드
+ DATA : 전역 변수, static 변수
+ HEAP : 동적할당 (자바에서는? 객체?)
+ STACK : 지역변수, parameter
### 프로세스 VS. 쓰레드
+ 프로세스 : 자신만의 고유공간 + 자원 할당
+ 쓰레드 : 공간,자원을 공유... (stack 영역)

+ 멀티 프로세스 : 여러 cpu가 하나의 컴퓨터에서 병렬처리 되는 것 : 장점 - 안정성 단점 - 시간,자원 소모 大 (context switching)
+ 멀티 쓰레드 : 한 프로그램 내에서 여러 스레드가 하나의 작업을 처리 : 단점 - 안정성(critical section으로 방지) 장점 - 시간,자원 공유
