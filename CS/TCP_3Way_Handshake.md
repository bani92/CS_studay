### TCP 이용한 통신과정

1. 클라이언트가 서버에게 요청 패킷을 보내고 (SYN)
2. 서버가 클라이언트의 요청을 받아들이는 패킷을 보내고 (SYN+ACK)
3. 클라이언트는 이를 최종적으로 수락하는 패킷을 보낸다 (ACK)

### SYN(Synchronize Sequence Number) 
- 연결을 요청할 때 SYS bit를 사용한다.
- 연결을 요청하는 경우에 SYN bit를 1로 설정한다.

### ACK(Acknowledgement) 
- 패킷을 받았다는 응답을 할 때 사용한다.

### Port 상태 정보
- LISTEN : 포트가 열린 상태로 연결 요청을 대기하는 상태
- SYS-SENT : 연결 요청을 하고 Server의 ACK를 기다리는 상태
- SYN_RCVD : 연결 요청에 응답/연결을 요청하고 Client의 응답을 기다리는 상태
- ESTABLISHED : 연결된 상태

### [step 1] : 클라이언트 - (SYN) - 서버
- 클라이언트가 서버에게 연결을 요청하는 SYN Segment를 보낸다.
- SYN Segment를 전송한 후 SYS-SENT 상태로 서버의 ACK Segment를 기다린다.
- 서버는 클라이언트로부터 SYN Segment를 수신한다.

### [step 2] : 클라이언트 - (ACK + SYN) - 서버
- 서버가 클라이언트의 SYN Segment에 대한 ACK Segment를 전송한다.
- SYN/ACK Segment를 전송하고 SYN RCVD의 상태로 클라이언트의 ACK를 기다린다.
- 클라이언트는 ACK Segment을 받고 연결이 완료된 ESTAB 상태가 된다.

### [step 3] : 클라이언트 - (ACK) - 서버
- 클라이언트는 서버의 SYN Segment에 대한 ACK Segment를 전송한다.
- 서버는 ACK Segment을 받고 연결이 완료된 ESTAB 상태가 된다

### [after] : 클라이언트 - (Data) - 서버
- 클라이언트와 서버가 서로 데이터를 주고 받는다.

출처 : https://hojunking.tistory.com/106