# Netwhat



#### Introduction

Netwhat will allow you to discover the network and to learn about its inner workings. This will allow you to understand how some things work that you already use in your everyday life.

- 네트워크와 네트워크의 내부 동작에 대한 학습
- 이미 일상에서 사용하고 있는 네트워크의 기능들에 대해 이해하기.



#### General instructions

Netwhat is a multiple choice project. This project will evaluate your network knowledge. You can start by reading network lessons on the internet. After that you can use online quizes to test your knowledge. Once you’ve done that and you feel that you are ready to pass our quiz, you can go to: netwhat.42.fr.

- 객관식 풀이 문제로 네트워크의 지식을 평가
- 인터넷에 네트워크 개념들을 찾아 공부하고, 온라인 퀴즈를 통해 네트워크 지식을 테스트
- 준비가 다 되면 netwhat.42.fr 사이트에 접속하여 퀴즈 풀기.



#### Mandatory part

1) first of all, you should know a few things:

- **IP address** 란 무엇인가?

  -  **컴퓨터(노드) 간 통신**하기 위해 각 컴퓨터에 부여된 **네트워크 주소**.

-  **Netmask**란 무엇인가?

  - IP 주소에서 **네트워크 주소와 호스트 주소를 구분**하는 비트마스크

- **Subnet**란 무엇인가?

  - IP 주소의 효율성을 위하여 **네트워크 영역을 부분적으로 나눈 부분망**(네트워크 세분화)

- Subnet의 **Broadcast**란 무엇인가?

  - **네트워크에 연결된 모든 호스트에 데이터를 전송하는 방식**으로 해당 브로드캐스트 주소를 사용하여 해당 주소 범위에 있는 전체 호스트에 트래픽을 전달

- **IP 주소를 나타내는 여러 방법**은 무엇인가?

  - **IPv4** (32bit 주소 체계),  **IPv6** (128bit 주소 체계)

- **public IP 와 private IP의 차이**는 무엇인가?

  - public IP는 **공인기관에서 인증한 공개형 IP주소**로 외부에 공개되어 있어 이 **IP 주소를 통해 호스트 간 직접적으로 통신할 수 있게 된다.** 
  - private IP는 **외부에 공개되지 않은 패쇄형 IP 주소**로 이 IP 주소만으로는 **외부에서 직접적으로 통신할 수가 없다.**

- **IP 클래스**가 무엇인가?

  - **하나의 IP 주소에서 네트워크 영역과 호스트 영역을 나누는 방법**으로 네트워크의 규모에 따라 클래스가 결정된다.

-  **TCP** 란 무엇인가?

  - IP보다 느리지만 도착한 조각들을 정렬하고 손실된 부분을 다시 요청하여 **데이터를 안전하게 전달**하는 프로토콜로 속도는 느리지만 논리적이면서 높은 신뢰성을 가지는 전송을 보장하기 위해 **3 & 4way handshake** 방법을 사용한다 

- **UDP**란 무엇인가?

  - **데이터를 데이터그램(독립적인 관계를 지니는 패킷) 단위로 처리**하는 프로토콜 (각각의 패킷은 다른 경로로 전송)로 TCP 와 달리 연결을 위해 할당되는 **논리적인 경로가 없는 비연결형** 프로토콜이다. 신호 절차를 거치지 않기 때문에 TCP 보다 속도가 빠르고 **네트워크 부하가 적지만 신뢰성을 보장하지는 못 한다.**

- **network layers**란 무엇인가?

  - **논리적 주소(IP)** 를 구분하고 연결하여 패킷 데이터를 목적지까지 최적의 경로로 가장 빠르게 전달하는 역할을 하는 계층

- **OSI model**이란 무엇인가?

  - 국제 표준화 기구에서는 통신이 일어나는 과정을 **계층별로 세분화**시켜 **응용(Application) -> 표현(Presentation) -> 세션(Session) -> 전송(Transport) -> 네트워크(Network) -> 데이터 링크(Data Link) -> 물리(Physical)** 의 7계층으로 이루어진 모델.

- **DHCP server 와 the DHCP protocol**이란 무엇인가?

  - IP 주소를 할당하는 **특정 서버가 보내 주는 IP 주소 그대로 컴퓨터에 자동 할당되는 방식**으로 컴퓨터가 많은 환경에서 간편하고 유용하다.

- **DNS server 와 the DNS protocol**이란 무엇인가?

  - **도메인 네임과 해당 IP 주소를 한 쌍으로 저장**하고 있는 **분산형 데이터 베이스** 시스템으로 호스트의 도메인 네임을 **컴퓨터가 인식할 수 있는 네트워크 주소로 변환**해주는 역할을 한다.

- What are **the rules to make 2 devices communicate using IP addresses**

  - 

- How does **routing work with IP**

  - 

- What is  **a default gateway for routing**

  - 

- What is **a port from an IP point of view** and what is it used for when **connecting to another device**

  - 

  

2) Go to the website: netwhat.42.fr. This site will provide access to the network quiz.

Once connected, you will have access to the quiz interface. You can only pass it once per try, and you will have to retry the project to be able to retry the quiz. At the end an encrypted key will be generated. This key will be used during your evaluation (see Turn-in and peer-evaluation).

- netwhat.42.fr 사이트에 접속해서 퀴즈를 풀면 key를 지급 받을 것.

- 이 key는 동료 평가 때 풀이를 보기 위해 사용

  

**Turn-in and peer-evaluation**

To submit your work, paste the key, without modifying it, in a file answer.txt in the root of your git repo. Your evaluator will use that key to verify your answers during defence.

- 문제를 제출하려면 키를 복사하여 answer.txt 라는 파일에 붙여넣기
- answer.txt 파일은 git repository의 root에 위치