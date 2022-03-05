### OSI 7계층
1. 물리 :
> 리피터, 케이블, 허브
2. 데이터링크 : MAC 주소를 통해 통신 : 에러검출, 재전송, 흐름제어
> 브릿지, 스위치
3. 네트워크 : 경로 선택 - IP주소 지정, 패킷전달 : 라우팅, 오류제어, 세그멘테이션
> 라우터, IP
4. 전송
> TCP, UDP (TCP_vs_UDP)
5. 세션
> API, Socket
6. 표현
> JPEG, MPEG
7. 응용
> HTTP, FTP, DNS

### HTTP vs. HTTPS
+ HTTP : 서버 - 클라이언트 사이의 통신규약
+ HTTPS : HTTP + SSL프로토콜(공개키 암호화)

### Web Server vs. Web Application Server 
- 구분이유 : 웹서버는 정적페이지만 처리해 서버의 부담을 줄이기 위해
- WAS는 왜 사용? 웹서버만으로는 사용자가 원하는 요청에 대한 결과값을 모두 미리 만들어놓고 서비스하기에는 리소스가 절대적으로 부족  
> 따라서, 요청이 들어올 때마다 DB와 비지니스 로직을 통해 결과물을 만들어 제공
- WAS만으로 가능하지 않을까? 1) WAS가 정적페이지까지 처리하면 부하가 커짐. 2)동적 컨텐츠 처리가 지연돼 수행속도가 느려짐.

<img width="80%" src="![WSvsWAS](https://user-images.githubusercontent.com/48271665/156865301-fcbcb0fc-fd9e-495d-9e33-b8d664e83687.PNG)"/>



참고 깃허브 : [링크](https://github.com/gyoogle/tech-interview-for-developer/tree/master/Web)
