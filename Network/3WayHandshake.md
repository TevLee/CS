## 3 Way handshake와 4 Way handshake
<br>

* TCP 통신은 연결지향 / 데이터 전달보증 / 순서보장 의 특징을 가진다.
* 여기서, **연결지향**을 위해 필요하다.
<br>

> 3 Way handshake
  - 양쪽이 모두 전송 준비가 되었음을 보장하기 위한 과정
<br>
[1 단계] 

+ A 클라이언트는 B서버에 접속을 요청하는 SYN패킷을 보냄

+ 클라이언트(SYN_SENT상태) 서버(Wait for Client상태)
<br>
[2 단계]

+ B 서버는 SYN요청을 받고 A클라이언트에 요청을 수락하는 의미로 ACK 와 SYN flag가 설정된 패킷을 발송하고 대기

+ 서버(SYN_RECEIVED상태)
<br>
[3 단계]

+ A 클라이언트는 B서버에게 ACK을 보내고 연결 완료 + 통신 시작

+ 서버(ESTABLISHED상태)
-----------------
> 4 Way handshake
  - 3 Way handshake가 TCP 연결을 초기화할 때 사용하였다면, 
  - 4 Way handshake는 세션을 종료하기 위해 수행되는 절차
<br>
[1 단계] 

+ A 클라이언트가 연결을 종료하겠다고 FIN flag를 전송

+ 클라이언트(FIN-WAIT 상태)
<br>
[2 단계]

+ B 서버는 FIN flag를 받고, 일단 확인메세지 ACK를 보내고, 자신의 통신이 끝날때까지 대기

+ 서버(CLOSE_WAIT 상태)
<br>
[3 단계]

+ 연결을 종료할 준비가 되면, B서버는 클라이언트에 FIN flag를 전송 

+ 서버(LAST-ACK 상태)
<br>
[4 단계]

+ A 클라이언트는 해지 준비가 되었다는 ACK를 확인했다는 메세지를 보냄

+ 클라이언트(FIN-WAIT >> TIME-WAIT 상태)

