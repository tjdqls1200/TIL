# netwhat

What are the different ways to represent an *IP address* with the *Netmask*

* `192.168.0.1/24` 은 IP 주소가 `192.168.0.1` 이고 Netmask가 24 bits라는 의미이다.


What are the differences between public and private IPs

- Private IP address* 란?
  - Class A: `10.0.0.0` ~ `10.255.255.255`
  - Class B: `172.16.0.0` ~ `172.31.255.255`
  - Class C: `192.168.0.0` ~ `192.168.255.255`
- 초기 네트워크 디자인은 모든 기기가 고유한 IP 주소를 갖고있었지만 항상 필요하다는게 아니라는걸 알게되며 private IP 주소가 등장하게 됐다.
  * 공장의 기계들은 기계들끼리만의 통신이 필요할 뿐 인터넷에 연결되어 있을 필요가 없고 고유 IP 주소가 필요하지 않다.
  * 오늘날 사설 네트워크는 널리 쓰이고있고 필요할 때 NAT (network address translation)을 이용해 인터넷에 접속한다.

*Public IP address* vs *Private IP Address*

* 공용 IP 주소는 유일하지만 사설 IP 주소는 유일하지 않다.
\* What is a *class* of *IP addresses*

* Class 등장 이전에는 32-bit의 IPv4 주소 중 8 bits는 네트워크 주소를 표현하는데 사용되었다.
* ARPANET과 같은 몇 안되는 큰 네트워크만이 존재할 때는 256개의 네트워크로 충분했지만 이후 LAN이 빠른 속도로 확산되면서 네트워크 주소가 부족하게 되었다.
* 기존 주소를 유지하며 더 많은 네트워크 주소를 표현하기 위해 Class 방식이 도입되었다.
* 클래스 정의: *n*, *H*, *X*는 각각 네트워크, 호스트, 그 외 비트를 표현하기 위해 사용된다.
  * **Class A**: `0.0.0.0` ~ `127.255.255.255`
  	* `0nnnnnnn.HHHHHHHH.HHHHHHHH.HHHHHHHH`
  * **Class B**: `128.0.0.0` ~ `191.255.255.255`
  	* `10nnnnnn.nnnnnnnn.HHHHHHHH.HHHHHHHH`
  * **Class C**: `192.0.0.0` ~ `223.255.255.255`
  	* `110nnnnn.nnnnnnnn.nnnnnnnn.HHHHHHHH`
  * **Class D**: `224.0.0.0` ~ `239.255.255.255`
  * `1110XXXX.XXXXXXXX.XXXXXXXX.XXXXXXXX`
  * **Class E**: `240.0.0.0` ~ `255.255.255.255`
  	* `1111XXXX.XXXXXXXX.XXXXXXXX.XXXXXXXX`
  \* What is *TCP*
* Transmission Control Protocol, TCP
* Transport Layer
* Circuit Switching 방식에서 Packet Switching 방식으로 바꾸기 위해 고안된 프로토콜
* Circuit Switching 방식과는 달리 네트워크 환경의 안정성이 떨어지므로 데이터 유실 등의 문제를 해결하기 위해 등장
* 동작 순서
  * 연결 설정
  	1. **SYN**: 통신 요청 (Synchronization)
  	2. **SYN+ACK**: 통신 요청 응답 (Acknowledge)
  	3. **ACK**: 통신 시작 알림
  	* 네트워크 연결을 확인하는 과정
  * 데이터 전송
  	* Flow Control
  		1. 데이터 전송
  		2. Timeout 동안 ACK가 오지 않는다면 데이터 유실로 판단해 재전송
  		3. ACK를 수신하면 다음 데이터 전송
  		* 데이터 유실 문제 해결
  * 연결 종료
  	1. **FIN**: 통신 종료 요청
  	2. **ACK**: 통신 종료 요청 응답
  	3. **FIN+ACK**: 서버 종료 알림
  	4. **ACK**: 최종 종료 알림
* 특징
  * 호스트 내 프로세스간에만 존재하는 연결
  	* 중간 네트워크 요소는 이 연결을 감지하지 못함
* 연결지향적
  * 멀티캐스트 불가능 (1:1 전송 방식)
  * 양방향 연결
  \* What is *UDP*
* User Datagram Protocol
* Transport Layer
* 실시간 스트리밍 등 실시간성 또는 응답성이 중요한 프로그램에 적용하기 위해 등장
* 동작 순서
  * 연결 설정하지 않음
  * 데이터 전송
  	* 촐발지 포트, 도착지 포트, 길이, 체크섬이 헤더에 포함되어 있음
* 특징
  * 비연결성, 신뢰성이 없고 순서화되지 않음
  	* **확인 응답 없음**: 메세지가 도착했는지 확인하지 않음
  	* **순서 제어 없음**: 메세지의 순서를 맞추지 않음
  	* **흐름 제어 없음**: 흐름 제어 피드백을 제공하지 않음
  	* **최소한의 오류 제어**: Checksum을 제외한 오류 검출 및 제어가 없음
  	* **비연결성**: 논리적인 가상회선 연결이 필요 없음
  * 빠른 요청 및 응답
  * 멀티캐스트 가능 (1:N 전송 방식)
  * 전송속도 제한 없음



What are the *network layers*

	- 컴퓨터 네트워킹의 7계층 *OSI model* 중 제 3계층
	- 네트워크를 통해 가변 길이 네트워크 패킷을 전송하는 수단을 제공한다.
	- 기능
		- **Connectionless communication**: 데이터 패킷은 수신자가 사전 정보 없어도 발신자로부터 수신자로까지 전송이 가능하다.
		- **Host addressing**: 네트워크의 모든 호스트는 고유한 주소가 있어야 한다.
		- **Message forwarding**: 많은 네트워크들이 서브네트워크로 나뉘어있고 넓은 지역으로의 통신을 위해 서로 통신하기 때문에 네트워크에서는 네트워크 간 통신을 위해 특별한 호스트인 *gateway*나 *router*을 사용한다.
\* What is the *OSI model*
	* Open Systems Interconnection model
	* 통신 기술에서 구조나 기술에 관계 없이 특징을 갖고 표준화 한 모델
	* 다양한 통신 프로토콜과 시스템을 통한 상호운용성을 목표로 함
	* Layer 1: Physical layer
		* 디지털 신호를 전기, 라디오, 또는 광학 신호로 변환해 전송하는 규칙을 정의한다.
		* 물리적 전송, 매체와 전송 신호 방식등을 정의한다.
	* Layer 2: Data link layer
		
		* 두 개의 인접한 개방 시스템들 간의 신뢰성 있고 효율적인 정보 전송을 할 수 있도록 한다.
	* Layer 3: Network layer
		
		* 개방 시스템들 간의 네트워크 연결을 관리하는 기능과 데이터 교환 및 중계 기능을 한다.
	* Layer 4: Transport layer
		
		* 논리적 안정과 균일한 데이터 전송 서비스를 제공함으로써 종단 시스템 간에 투명한 데이터 전송을 가능하게 한다.
	* Layer 5: Session layer
		
		* 송, 수신 측 간의 관련성을 유지하고 대화 제어를 담당하는 계층이다.
* Layer 6: Presentation layer
		
		* L7로 부터 받은 데이터를 L5로 보내기 전에 통신에 적당한 형태로 변환하고 L5에게 받은 데이터는 L7에 맞게 변환하는 기능을 한다.
	* Layer 7: Application layer
		* 사용자가 OSI 환경에 접근할 수 있도록 서비스를 제공한다.
	\* What is a *DHCP server* and the *DNS protocol*
	* Dynamic Host Configuration Protocol
		* IP 주소를 동적으로 할당한 후 더 이상 사용되지 않으면 회수한다.
		1. DHCP Discover: 아이피 할당 요청
		2. DHCP Offer: 아이피 주소, 단말의 MAC 주소 등을 네터워크 정보와 함께 전송
	3. DHCP Request: 아이피 주소 정보 확인했다는 메시지를 보내 확정 요청
		4. DHCP Ack: 아이피 주소를 확정함
	* Domain Name System
		
		* 특정 컴퓨터의 주소를 찾기 위해 사람이 이해하기 쉬운 도메인 이름을 숫자로 된 IP 주소로 변환해 준다.
* 둘 다 OSI Layer 7에 속한다.
	\* How does *routing* work with IP
	
	* 어떤 네트워크 안에서 데이터를 보낼 때 가장 짧은 거리 또는 가장 적은 시간 안에 전송할 수 있는 경로를 선택하는 과정이다.
* Fixed / Static Routing: 미리 정해진 루트를 따라 경로 선택
	* Dynamic / Adaptive Routing: 망의 상태에 따라 경로 선택
		* 목적지 주소, 토폴로지, 트래픽 부하, 링크 비용 등의 정보를 이용해 결정
	\* What is a *default gateway* for routing
	* 다른 기술로 구성된 네트워크에 접속시켜주는 네트워크 노드이다.
	* 라우터가 존재한다면 *default gateway*는 라우터의 IP 주소가 된다.
	\* What is a *port* from an IP point of view and what is it used for when connecting to another device
	* OSI Layer 4에서 주로 사용하며 네트워크 서비스나 특정 프로세스를 식별하는 논리 단위다.
	* IP 주소와 함께 쓰여 해당하는 프로토콜에 의해 사용된다.
	* 포트는 크게 세 종류로 구분된다.
		* **Well-known port**: 0 ~ 1023
		* **Registered port**: 1024 ~ 49151
		* **Dynamic port**: 49152 ~ 65535