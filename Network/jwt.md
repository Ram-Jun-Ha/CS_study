# JWT ( JSON WEB TOKEN )

## 1. 정의

JWT는 전자 서명 된 URL-safe (URL로 이용할 수있는 문자 만 구성된)의 JSON이며, 전자 서명은 JSON 의 변조를 체크할 수 있다.
JWT는 속성 정보 (Claim)를 JSON 데이터 구조로 표현한 토큰으로 RFC7519 표준 체계를 따르며, 서버와 클라이언트 간 정보를 주고 받을 때 Http 리퀘스트 헤더에 JSON 토큰을 넣은 후 서버는 별도의 인증 과정없이 헤더에 포함되어 있는 JWT 정보를 통해 인증하는 과정을 처리할 수 있다.
JWT는 HMAC 알고리즘을 사용하여 비밀키 또는 RSA를 이용한 Public Key/ Private Key 쌍으로 서명할 수 있다.

### (1) JWS (JSON WEB SIGNATURE) & JWE (JSON WEB ENCRYPTION)

JWT와 관련된 표준으로는 JSON Web Signature (JWS)는 JSON 데이터 구조를 사용하는 서명 표준으로 RFC7515이며, JSON Web Encryption (JWE)는 JSON 데이터 구조를 사용하는 암호화 방법으로 RFC7516 표준이 존재한다.

<p align="center">
<img src="./img/jwt1.png" alt="img1" />
</p>

JWS (JSON Web Signature)은 **JSON으로 전자 서명을하여 URL-safe 문자열로 표현한 것**이며, 
JWE (JSON Web Encryption)는 **JSON을 암호화하여 URL-safe 문자열로 표현한 것**이다.
서명은 서명할 때 사용한 키를 사용하여 JSON이 손상되지 않았는지 확인 할 수 있도록 하는 것이며, 
URL Safe는 말 그대로 URL에 포함 할 수없는 문자를 포함하지 않는 것을 뜻한다.