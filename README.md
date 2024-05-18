## 알고리즘:
### 복잡도와 구현 방법 위주로. 보통 단순 면접 질문보다는 라이브 코딩에서 검증 
- Sort: Quick, Heap, Merge, Radix 등
- Search: Binary Search 등
- DP
- Greedy
- Divide and Conquer
- DFS, BFS
- Tree(Minimum Spanning Tree)
- Backtracking
- Topological Sort
- Two Pointers

 ---

## 자료구조:
### 추가/제거 상황에서의 복잡도, 어디에 왜 쓰이는지, 각 언어에 어떤 구현체가 있는지 파악하는 것이 중요.
- Array
- ArrayList
- LinkedList
- Stack
- Queue
- Heap
- Tree(B Tree, Trie)
- Hash(Hash collision 해결법)

 ---

## 데이터베이스:
### 백엔드 면접의 꽃. 실무와 밀접한 과목이기 때문에 데이터베이스 만큼은 확실히 이해하고 외워가야 한다. 인덱스, 트랜잭션은 실무에서도 자주 마주치는 문제이기 때문에 더더욱 중요하다.
- 인덱스(내부 구현, 장단점)
- 정규화
- 트랜잭션(ACID)
- 트랜잭션 격리수준(Read Uncommitted ~ Serializable)
- 테이블 설계(쿼리, 다대다 관계 등)
- RDBMS vs NoSQL
- 대표적인 NoSQL 

 
---

## 운영체제:
### 개념은 어렵지만, 물어보는 것만 물어보기 때문에 생각보다 양이 많지는 않다. 아무래도 개발과 직접 관련된 부분인 메모리 관리와 스레드 관리 쪽이 질문 비율이 높다.
- 프로세스(PCB)
- 스레드
- Context switching
- Interrupt
- CPU 스케줄링 / 스케줄러
- DeadLock
- Race Condition(세마포어와 뮤텍스)
- 메모리 단편화
- 가상 메모리
- 요구 페이징

---

## 네트워크:
### 백엔드 면접의 꽃2. 데이터베이스에 이어 실무와 밀접한 관계가 있기 때문에 이 부분도 면접에서 반드시 물어본다.
- OSI 7계층(의미)
- TCP: Handshake, 흐름제어, 혼잡제어
- UDP
- http(메서드, 상태코드 등)
- http vs https
- DNS
- 게이트웨이
- 프록시
- CORS
- 세션, 쿠키
- JWT(Json Web Token)
- RESTful API란?

---

## 디자인패턴:
### 신입 면접에서는 자주 물어보지 않지만, 디자인패턴의 종류와, 종류별 최소 한두개 정도의 세부 구현 방식은 이해하고 외워두는 편이 좋다.
- Creational patterns
1) Factory Method
2) Builder
3) Singleton
4) Prototype
5) Abstract Factory

- Structural patterns
1) Adapter
2) Composite
3) Decorator
4) Facade
5) Proxy

- Behavioral patterns
1) Command
2) Strategy
3) Iterator
4) Observer
5) Template Method 

---

## 자바:
### 특히 JVM 메모리와 컴파일 방식, GC, Java8 이후의 문법들에 대한 질문들이 많은 편이다. 전반적인 기초 문법과 용어에 대해서는 혹시나 모를 상황에 대비해서 간단하게 정리해 두는 것이 좋다.
- 객체지향(상속, 다형성, 캡슐화 등)
- JVM 메모리 구조
- 컴파일 과정
- 다양한 GC(parellel, g1gc 등)
- JRE, JDK, JVM의 구분
- 자바 메모리관리(Xms, Xmx)
- Call by Value vs Call by Reference
- String Immutable(String constant pool, "a" vs new String("a"))
- Auto Boxing & UnBoxing
- Error vs Exception
- Checked vs UnChecked Exception
- 비동기처리 문법 비교
- Java 8의 특징
- Lambda(+ Functional Interface)
- Stream API
- Default Method
- Generic
- Reflection(Annotation)
- Collection Framework(List, Map, Set 등) 
- HashMap(https://d2.naver.com/helloworld/831311)
- Abstract Class vs Interface(default method)
- CountDownLatch & CyclicBarrier


 ---

## 스프링:
### 보통 IoC, AOP 같은 스프링 프레임워크에 대한 기초나, MVC 처리 과정에 대한 질문이 많다. JPA를 사용해본 경우에는 n+1 문제에 대한 질문이 나올 가능성이 높다.
- PSA, IoC, AOP, POJO(각각에 대한 내용과 도입 이유)
- Bean(Scope)
- @Autowired 주입 방법별 차이(Field, Setter, Constructor Injection)
- ApplicationContext
- Web MVC 요청 처리 과정(DispatcherServlet을 중심으로)
- Spring vs Spring Boot
- @SpringBootApplication의 내부 구성
- @Controller vs @RestController
- Spring Security의 요청 처리 과정
- (JPA) JPA와 Hibernate
- (JPA) 영속성 컨텍스트(캐시, 동일성보장, 변경감지, 트랜잭션 지연)
- (JPA) Eager, Lazy Loading
- (JPA) n+1 문제
- (JPA) 다대다 해결 전략
- (JPA) JPA의 캐시


---

## 기타 기술:
### 만약에 이 기술들을 사용했고, 이력서에 넣었다면 기본 정도는 알고 가는 것이 좋다.
- Redis: 사용할 수 있는 자료구조와 특징들
- Kafka: 데이터 저장 및 Consuming 방식, 메시지큐의 사용 이유(Loose Coupling 등), RabbitMQ와의 차이 
- ElasticSearch: 역인덱스, query별 차이(term, match 등)

---
출처 : https://appleg1226.tistory.com/37
