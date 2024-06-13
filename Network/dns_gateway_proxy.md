1. DNS (Domain Name System) : 사람이 읽을 수 있는 도메인 (www.naver.com)을 머신이 읽을 수 있는 IP 주소(92.0.2.44)로 변환하는 시스템
    - 변환 과정
![img.png](img%2Fimg.png)
   1. [www.naver.com](http://www.naver.com) 에 접속하려고 할 때 pc에 설정된 로컬 DNS서버에 해당 도메인과 호스트명의 IP 주소를 가지고 있는지 확인
   2. 로컬 DNS 서버에 주소가 있으면 반환, 없으면 Root DNS 서버에서 .com 으로 끝나는 도메인을 담당하는 서버의 IP 주소를 반환
   3.  .com 으로 끝나는 도메인을 담당하는 서버에게서 [naver.com](http://naver.com) 의 도메인 정보를 가진 서버의 IP 주소를 반환
   4. [www.naver.com](http://www.naver.com) 서버의 IP 주소를 얻어 브라우저에게 반환
   5. [www.naver.com]\(http://www.naver.com) 서버에 접속 

2. 게이트웨이(Gateway) : 한 네트워크에서 다른 네트워크로 이동하기 위하여 거쳐야하는 지점
    - 같은 대역에서 통신을 한다면 (192.168.0.1 → 192.168.10.3) 바로 통신이 가능하지만 다른 대역으로 통신을 한다면 (192.168.0.1 → 172.16.0.0) 게이트웨이를 거쳐야 통신이 가능하다
    - 게이트웨이로 활용되는 것
        - 프록시 서버 : 서버와 클라이언트 사이 중재자 역할을 하는 서버
        - 유무선 공유기(라우터) : 내부 네트워크와 외부 네트워크를 연결해주며 데이터들의 전송 경로를 설정하는 장치
        - 방화벽 : 허용된 트래픽만을 네트워크 출입이 가능하도록 관리하여 네트워크 보안을 강화

3. 프록시 (Proxy) : 서버와 클라이언트 사이에 중재자로서 클라이언트 대신 서버와 대리로 통신을 수행하는 것
    - 프록시 서버의 역할
        - 클라이언트 대신 서버에게 요청을 받아 응답
        - 캐시를 통해 자원을 저장
![img_1.png](img%2Fimg_1.png)
          - 네트워크 비용 감소
          - 응답 속도 향상
      - 프록시 서버를 거치는 요청 및 응답 확인(필터기능)
          - 보안성 향상
          - 프록시를 통한 모든 요청 로깅 가능
      - 프록시 서버로 넘어온 데이터 조작 가능 (데이터 압축, 언어 변환, 암호)
          - 네트워크 비용 감소
          - 원 서버 역할 감소
          - 보안성 향상
    - Forward Proxy vs Reverse Proxy
![img_2.png](img%2Fimg_2.png)
      - Forward Proxy : 클라이언트 요청을 받아 인터넷을 통해 외부 서버의 데이터를 가져와 클라이언트에게 응답하는 방식
      - Reverse Proxy : 클라이언트가 웹서비스 접근시 웹서버가 아닌 프록시로 요청을 하고 프록시가 서버에서 데이터를 가져오는 방식
          - Load Balancing : 여러 대의 서버에 요청을 나누어 진행할 수 있도록 결정해주는 작업
      > 로드밸런싱이 Reverse Proxy에서 가능한 이유 
      > - 포워드 프록시는 클라이언트 요청을 직접 받아 인터넷을 통해 외부서버에 데이터를 요청함
      > - 하지만 클라이언트 요청이 특정 외부 서버로만 집중되는 경우가 드물어 로드밸런싱을 적용하기 어려움
      > - 리버스 프록시는 다수의 사용자가 내부의 서버에 접근을 할 때 요청을 분산시켜줄 수 있음

참고 : https://www.youtube.com/watch?v=6fc9NAQkcv0,
https://aws.amazon.com/ko/route53/what-is-dns/,
https://hstory0208.tistory.com/entry/Gateway게이트웨이란-Router라우터란-각-개념과-차이점에-대해-알아보자,
https://codedatasotrage.tistory.com/48,
https://www.youtube.com/watch?v=lg-wHikZg0Q,
https://docs.oracle.com/cd/E19636-01/819-3161/agcache.html,
https://inpa.tistory.com/entry/NETWORK-📡-Reverse-Proxy-Forward-Proxy-정의-차이-정리