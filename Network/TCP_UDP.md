1. Transport Layer
    - OSI 모델의 네번째 계층으로, 데이터 패킷이 발신자와 수신자 간에 정확하고 신뢰성있게 전달되도록 함
    - TCP, UDP 프로토콜을 사용

1. TCP 프로토콜
    - 전송계층에 위치하여 네트워크 정보 전달을 메세지 형태로 보내기 위해 IP와 함께 사용하프로토콜 → 연결형
    - TCP 헤더와 세그먼트로 이루어짐
        - 세그먼트 : TCP가 헤더를 제외하고 실을 수 있는 데이터의 크기
        - TCP 헤더 : 신뢰성 보장, 흐름제어, 혼잡제어를 할 수 있는 요소들을 포함
      ![img_10.png](img%2Fimg_10.png)
    - TCP 작동 : 3-way handshake
      ![img_11.png](img%2Fimg_11.png)
        - syn : TCP 연결을 할 때 보내는 연결 요청
        - ack : 데이터 패킷이 잘 전달되었음을 알림
    - TCP 의 특징
        - 흐름 제어 : window size, acknowledgment number, sequence number 등으로 받을 수 있는 데이터의 양, 지금까지 받은 데이터 등의 정보를 보내 데이터의 흐름을 끊임없이 확인함
        - 혼잡 제어 : 네트워크망의 혼잡을 판단하여 데이터 송출량을 조절함
        - 3-way-handshaking 방식으로 연결하고 4-way-handshaking 을 통해 해제
        - 높은 신뢰성과 전송 순서를 보장

1. UDP
    - 데이터를 데이터그램(독립적인 관계를 지니는 패킷) 단위로 처리하는 프로토콜 → 비연결형
    - UDP 특징
        - 정보를 주고 받을 때 정보를 보내거나 받는다는 신호 절차를 거치지 않음
        - checksum 필드를 통해 최소한의 오류만 검출
        - 신뢰성이 낮으나 속도가 빠름
      
![img_12.png](img%2Fimg_12.png)     

참고 :
https://www.youtube.com/watch?v=ikDVGYp5dhg,
https://aws-hyoh.tistory.com/57,
https://mangkyu.tistory.com/15