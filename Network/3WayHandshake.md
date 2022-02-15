## 3 Way handshake와 4 Way handshake
<br>
* TCP 통신은 연결지향 / 데이터 전달보증 / 순서보장 의 특징을 가진다.
* 여기서, **연결지향**을 위해 필요하다.
<br>
1. 3 Way handshake
  - 양쪽이 모두 전송 준비가 되었음을 보장하기 위한 과정
[1 단계] 
+ A 클라이언트는 B서버에 접속을 요청하는 SYN패킷을 보냄
+ 클라이언트(SYN_SENT상태) 서버(Wait for Client상태)
[2 단계]
+ B 서버는 SYN요청을 받고 A클라이언트에 요청을 수락하는 의미로 ACK 와 SYN flag가 설정된 패킷을 발송하고 대기
+ 서버(SYN_RECEIVED상태)
[3 단계]
+ A 클라이언트는 B서버에게 ACK을 보내고 연결 완료 + 통신 시작
+ 서버(ESTABLISHED상태)


