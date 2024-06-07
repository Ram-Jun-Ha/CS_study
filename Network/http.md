# 1. HTTP

프로젝트하던 당시에는 사실 크게 구별하지 않으면서 용어를 썼다. 실제로도 둘은 약간 비슷한 의미이기도 하고. 다만 정확한 의미를 따지자면, **HTTP API**는 **RESTful API**보다 더 넓은 범위를 포함한다. HTTP API에서 여러 제약과 조건을 걸어둔 것이 RESTful API라고 할 수 있겠다.

## 1) HTTP API
HTTP API(`Hyper Text Transfer Protocol`)는 **HTTP 프로토콜**을 사용해서, **서로 정해둔 스펙으로 데이터를 주고 받으며 통신**하는 것을 말한다. 정의가 간단한 만큼 제약이나 제한이 크게 없지만, 일단 정의 하나하나 뜯어볼 예정.

### (1) HTTP 프로토콜
![](https://velog.velcdn.com/images/kim00ngjun_0112/post/95cbf1c0-c6c0-4fdb-b566-8997f22d0ecc/image.png)

HTTP는 HTML 문서와 같은 리소스들을 가져올 수 있도록 해주는 프로토콜이다. 웹에서 이루어지는 모든 데이터 교환의 기초이며, 클라이언트-서버 프로토콜의 의미를 지니고 있다.

클라이언트-서버 프로토콜이란 (보통 웹브라우저인) 수신자 측에 의해 요청이 초기화되는 프로토콜을 의미하는데, 하나의 완전한 문서는 텍스트, 레이아웃 설명, 이미지, 비디오, 스크립트 등 불러온(**fetched**) 하위 문서들로 재구성된다.

### (2) 서로 정해둔 스펙
거창한 단어를 쓴 것 같지만, 단순하게 클라이언트와 서버 간에서 약속을 정하는 것이다. 어떤 형식으로 데이터를 주고 받을지(**JSON, XML 등등**), 어떤 메소드를 사용하여 통신할지(**RESTful API의 경우, 어떻게 GET, POST, PATCH, DELETE를 할 지**), 데이터의 구조(**배열, 연결 리스트, 객체 등등**)는 어떻게 정의되어 있는지 등에 대한 약속이다.

### (3) HTTP? HTTPS?
![](https://velog.velcdn.com/images/kim00ngjun_0112/post/03cec63c-597b-4275-b8e5-79df2c57ef6c/image.png)

HTTPS는 **암호화 및 인증**이 있는 HTTP를 뜻한다. 두 프로토콜의 유일한 차이점은 HTTPS는 **TLS**를 사용하여 일반 HTTP 요청과 응답을 암호화하고 해당 요청과 응답에 디지털 서명을 한다는 점이다.

TLS는 IETF에서 유지, 관리하는 웹의 보안 암호화를 위한 새로운 프로토콜을 의미한다. 90년대 중반에는 넷스케이프에 의해 생성된 SSL 프로토콜을 사용했으나 지금은 폐지됐다.

통상의 `GET` **요청**을 일반적인 HTTP 프로토콜로 수행하면, 이렇게 구성된다.

```
GET /hello.txt HTTP/1.1
User-Agent: curl/7.63.0 libcurl/7.63.0 OpenSSL/1.1.l zlib/1.2.11
Host: www.example.com
Accept-Language: en
```
![](https://velog.velcdn.com/images/kim00ngjun_0112/post/31697640-c6e7-46d4-ba14-030d0cceb74f/image.png)

---

또한, 해당 요청에 대한 원본 서버에서의 **응답**은 아래처럼 이뤄진다.
```
HTTP/1.1 200 OK
Date: Wed, 30 Jan 2019 12:14:39 GMT
Server: Apache
Last-Modified: Mon, 28 Jan 2019 11:17:01 GMT
Accept-Ranges: bytes
Content-Length: 12
Vary: Accept-Encoding
Content-Type: text/plain

Hello World!
```
![](https://velog.velcdn.com/images/kim00ngjun_0112/post/2e4b53d2-0592-41ef-9ab8-219b45bce527/image.png)

어떤 내용이 담겨있는지 통신에 정상적으로 참여하지 않는 제삼자가 해당 내용을 읽어서 정보를 탈취할 수 있다는 부분이 HTTP 프로토콜의 대표적인 단점이 된다.

이것을 HTTPS로 치환하면 요청과 응답은 암호화돼서 송수신한다. 이를 통해서 제삼자는 위의 해당 내용 대신, 아래와 같은 무작위 텍스트 나열을 확인하게 된다.
```
t8Fw6T8UV81pQfyhDkhebbz7+oiwldr1j2gHBB3L3RFTRsQCpaSnSBZ78Vme+DpDVJPvZdZUZHpzbbcqmSW1+3xXGsERHg9YDmpYk0VVDiRvw1H5miNieJeJ/FNUjgH0BmVRWII6+T4MnDwmCMZUI/orxP3HGwYCSIvyzS3MpmmSe4iaWKCOHQ==
```

TLS는 **공개 키 암호화**라는 기술을 사용한다. 암호화에 있어 두 개의 키인 **공개 키**와 **개인 키**가 있으며, 공개 키는 서버의 SSL 인증서를 통해 클라이언트 장치와 공유된다. 클라이언트가 서버와의 연결을 열면 두 장치는 공개 키와 개인 키를 사용하여 **세션 키**라는 새로운 키에 동의하여 두 장치 간의 추가 통신을 암호화하게 된다.

모든 HTTP 요청과 응답이 이 세션 키로 암호화되므로 통신에 침입해 정보를 가로채는 제삼자는 일반 텍스트가 아닌 임의의 텍스트 나열만 볼 수 있게 된다.

*참고 링크*
*https://www.cloudflare.com/ko-kr/learning/ssl/why-is-http-not-secure/*

## 2) RESTful API

앞서 얘기했듯이 HTTP API에서 제약과 조건을 걸어둔 것이 RESTful API라고 했다. 그렇다면 중요한 키워드는 **제약**과 **조건**이 될 것인데, 저 부분들에 대해서 중점적으로 확인할 예정. 물론 정의부터 하나하나 뜯으면서 말이지

### (1) REST API? RESTful API?

RESTful은 REST의 설계 규칙을 잘 지켜서 작성된 API를 뜻한다. 즉, 예를 들어서 모든 CRUD 기능을 `POST`로 처리하는 API는 REST API를 사용하였지만 RESTful 하지 못한 시스템이라고 볼 수 있겠다.

### (2) REST API의 특징

#### URL과 URI 구분
>#### URL(Uniform Resource Locator)
인터넷 상에서의 리소스 위치
>#### URI(Uniform Resource Identifier) 
인터넷 상의 자원을 식별하기 위한 문자열의 구성
>URI는 URL을 포함하며 더 포괄적인 의미라고 볼 수 있다.
>

#### REST 구성 요소
> #### 리소스 
리소스는 서버에 위치하며, 자원에는 고유한 **ID**가 있으며, 리소스를 구별하는 ID는 */exgroups/:exgroup_id*와 같은 **HTTP URI**이다. 클라이언트는 URI를 지정해서 리소스를 지정하고 해당 리소스의 상태(정보)에 대한 조작을 서버에 요청한다.
>#### 메소드
>메소드는 쉽게 말해서 **행위**이며, HTTP 프로토콜은 **GET, POST, PUT, PATCH, DELETE**의 메소드를 제공하고 이를 통해 CRUD를 구현한다. PUT은 데이터 전체를 업데이트하고, PATCH는 데이터 일부를 업데이트한다.
>#### 표현
>클라이언트와 서버 간에서 데이터를 주고받는 표현의 방식에는 **JSON, XML, TEXT, RSS 등등**이 있다.

상기의 용어를 바탕으로 REST API의 대표적인 특징은 **각 요청이 어떤 동작이나 정보를 위한 것인지를 그 요청의 모습 자체로 추론이 가능**하다는 점이다. 

REST API가 준수해야 할 규칙은 다음과 같다.

>- URI는 명사를 사용한다.(리소스명은 동사가 아닌 명사를 사용해야 한다.)
>
- 슬래시(`/`)로 계층 관계를 표현한다.
>
- URI 마지막 문자로 슬래시 (`/`)를 포함하지 않는다.
>
- 밑줄(`_`)을 사용하지 않고, 하이픈(`-`)을 사용한다.
>
- URI는 소문자로만 구성한다.
>
- HTTP 응답 상태에 대하여 코드를 사용함으로써, 클라이언트는 해당 요청에 대한 실패, 처리완료 또는 잘못된 요청 등에 대한 피드백을 받아야 한다.
>
- 파일확장자는 URI에 포함하지 않는다.

### (3) RESTful하게 설계한다는 것
RESTful한 API는 요청을 보내는 주소만으로도 어떤 것을 요청하려는 것인지에 대한 의도가 명확하게 보인다. 예시를 보자.

---
```
https://school.com/grade

# 다음과 같은 주소는 학교에서 학년에 대한 정보를 요청하는 것임을 파악할 수 있다.
```
---
```
https://school.com/grade/2/students

# 다음과 같은 주소는 학교에서 2학년 학생들에 대한 정보를 요청하는 것임을 파악할 수 있다.
```
---
```
https://school.com/grade/2/students?gender=male

# 다음과 같은 주소는 조건을 설정함으로써 학교에서 2학년 남학생에 대한 정보를 요청하고 있다.
```
---
```
https://school.com/grade/2/students?page=2&count=10  

# 다음과 같은 주소는 한 페이지에 정보를 10개씩 받아오는 경우를 상정할 때,
# 2페이지에 존재하는 2학년 학생 정보를 총 10개 요청하고 있다.
```
---

### (4) 무조건 RESTful해야만 하는가?
정답은 아니다. 오히려 성능이 중요시되면서 간단한 경우일 때는 해당 내용을 무조건 준수하지 않아도 된다. REST API를 구현함에 있어 주어진 기준을 잘 준수하는 것이 RESTful한 것이지만, 어떤 것에 있어 적용되는 **기준**에 불과할 뿐.

다만 REST API를 적용할 때에는 적어도...
>- URI는 **리소스의 정보**만을 명시한다.
- **리소스의 행위**는 HTTP 메소드가 명시한다.

이 두 개의 원칙만큼은 꼭 준수할 것!

*참조 링크*
*https://dev-coco.tistory.com/97*
*https://positiwise.com/blog/difference-between-restapi-restful-api*