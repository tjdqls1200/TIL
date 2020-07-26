## 전송 계층(Transport Layer)의 TCP와 UDP 특징

전송 계층은 네트워크 계층에서 받은 데이터들을 호스트 간에 전송하기 위해 전송 방식을 결정하여 데이터를 전달하는 역할을 한다. 그리고 데이터를 보내기 위해 사용되는 프로토콜이 바로 TCP 와 UDP다.

- TCP (Transmission Control Protocol)

  TCP/IP 에서 IP 가 데이터의 전송을 처리한다면 TCP 는 패킷을 추적 및 관리하는 역할을 한다. (패킷에 번호를 부여)

  TCP 는 연결형 서비스로 가상 회선 방식을 제공하는데 이는 발신지와 수신지를 연결하여 패킷을 전송하기 위한 논리적 경로를 배정하는 방식이다. 그리고 속도는 느리지만 논리적이면서 높은 신뢰성을 가지는 전송을 보장하기 위해 3-way handshake 방법을 사용한다. 3-way handshake 는 데이터를 전송하기에 앞서 정확한 전송을 보장하기 위해 상대방 호스트와 사전에 세션을 수립하는 과정이다.

  3-way handshaking (TCP 의 연결 초기화 과정)

  1. Client → Server (접속을 요청하는 SYN 패킷을 전송, Client = SYN_SENT 상태)
  2. Client ← Server (요청을 수락하는 ACK + SYN 패킷을 전송, Server = SYN_RECEIVED 상태)
  3. Client → Server (ACK 전송 후 연결 성공, Server = ESTABLISHED 상태)

  4-way handshaking (TCP 의 연결 종료 과정)

  1. Client → Server (연결을 종료하는 FIN 플래그 전송)
  2. Client ← Server (확인 메세지 ACK 전송, TIME_WAIT 대기 상태)
  3. Client ← Server (연결 종료 후 FIN 플래그 전송)
  4. Client → Server (확인 메세지 ACK 전송)

- UDP (User Datagram Protocol)

  UDP 는 데이터를 데이터그램(독립적인 관계를 지니는 패킷) 단위로 처리하는 프로토콜로서 TCP 와 달리 연결을 위해 할당되는 논리적인 경로가 없는 비연결형 프로토콜이다. 그래서 각각의 패킷은 다른 경로로 전송되어 독립적으로 처리가 된다. 신호 절차를 거치지 않기 때문에 TCP 보다 속도가 빠르고 네트워크 부하가 적지만 TCP 처럼 패킷에 순서를 부여하고 재조립을 하지 않기 때문에 신뢰성을 보장하지는 못 한다. 주로 전화, 실시간 서비스 등 연속성이 중요한 서비스에 사용된다.