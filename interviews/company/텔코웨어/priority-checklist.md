# 텔코웨어 필기시험 최종 우선순위와 검수 결과

## 결론

텔코웨어 1차 필기시험은 일반 서비스 회사 백엔드보다 `통신 + 서버 + 네트워크` 비중이 높을 가능성이 있다. 다만 IMS, Core Network, 5G, MEC 자체를 깊게 설명하라는 수준보다는, 통신 솔루션 회사가 중요하게 보는 네트워크 기초와 서버 기본기를 확인할 가능성이 더 높다.

따라서 우선순위는 아래 3축으로 잡는다.

1. Java/Spring 기본기
2. DB/Transaction/Index
3. Network/TCP/IP/HTTP/Thread

알고리즘보다 JVM, 트랜잭션, TCP/IP, DB 인덱스를 우선 복습하는 편이 합격 확률을 더 높인다.

## S급: 무조건 준비

### Java

- OOP 4대 특성
- JVM 구조
- GC
- HashMap
- ConcurrentHashMap
- equals/hashCode
- String/StringBuilder/StringBuffer
- Collection Framework

### Spring

- IoC
- DI
- Bean
- AOP
- `@Transactional`
- Filter
- Interceptor

### DB

- Index
- Join
- Transaction
- Isolation Level
- Deadlock
- 정규화

### REST/Auth

- GET/POST/PUT/PATCH
- HTTP 상태코드
- JWT
- Session/Cookie

## A급: 텔코웨어라서 중요

### TCP와 UDP 차이

TCP:

- 연결지향
- 신뢰성 보장
- 순서 보장
- ACK, Sequence Number, 재전송, 흐름제어, 혼잡제어 사용

UDP:

- 비연결
- 빠름
- 순서 보장 없음
- 신뢰성 보장 없음

### 3-way Handshake

```text
Client -> SYN
Server -> SYN + ACK
Client -> ACK
```

목적:

- 연결 가능 여부 확인
- 양쪽 송수신 가능 상태 확인

### 4-way Handshake

```text
Client -> FIN
Server -> ACK
Server -> FIN
Client -> ACK
```

3번이 아니라 4번인 이유:

- TCP는 양방향 통신이므로 데이터 송신 종료와 수신 종료가 각각 독립적으로 닫힌다.

### HTTP와 HTTPS 차이

HTTP:

- 평문 통신
- 중간에서 내용 노출 가능

HTTPS:

- HTTP + TLS
- 암호화, 서버 인증, 데이터 무결성 제공

### TLS 동작 핵심

- 서버 인증서 확인
- 대칭키 교환 또는 합의
- 이후 HTTP 데이터를 암호화해 전송

### Socket

정의:

- 프로세스 간 네트워크 통신을 위한 endpoint

서버 socket 흐름:

```text
ServerSocket 생성
bind
listen
accept
Socket 생성
send / receive
```

### Keep Alive

사용 이유:

- 매 요청마다 TCP 연결을 새로 만들지 않기 위해 사용한다.
- handshake 비용을 줄이고 latency를 낮춘다.

주의점:

- 연결을 오래 유지하면 서버 리소스를 점유할 수 있다.
- timeout 설정이 필요하다.

### Connection Pool

사용 이유:

- DB나 외부 시스템 연결 생성 비용을 줄인다.
- 매번 새 연결을 만들지 않고 재사용한다.
- pool size가 너무 작으면 대기 시간이 늘고, 너무 크면 DB 부하가 커질 수 있다.

## B급: 통신회사 특화 기초

### OSI 7계층

| 계층 | 역할 | 예시 |
| --- | --- | --- |
| 7 Application | 애플리케이션 프로토콜 | HTTP |
| 6 Presentation | 표현/인코딩/암호화 | TLS 일부 관점 |
| 5 Session | 세션 관리 | 세션 제어 |
| 4 Transport | 종단 간 전송 | TCP, UDP |
| 3 Network | 라우팅/주소 | IP |
| 2 Data Link | 인접 노드 전송 | Ethernet |
| 1 Physical | 물리 신호 | Cable, Radio |

빠른 답:

- HTTP: 7계층
- TCP: 4계층
- UDP: 4계층
- IP: 3계층
- Ethernet: 2계층

### HTTP Stateless

의미:

- HTTP 요청 자체는 이전 요청 상태를 서버가 자동으로 기억하지 않는다.

상태 유지 방법:

- Session
- Cookie
- JWT

### JWT 사용 이유

- 서버가 세션 저장소를 직접 들고 있지 않아도 인증 정보를 검증할 수 있다.

주의점:

- 탈취되면 만료 전까지 위험하다.
- 민감 정보를 payload에 넣으면 안 된다.
- 만료, refresh, blacklist 전략이 필요하다.

### Cache

사용 이유:

- 반복 조회 성능 개선
- DB 부하 감소
- latency 감소

Redis 장점:

- in-memory 기반 빠른 처리
- 다양한 자료구조 제공
- TTL 설정 가능
- 분산 환경에서 cache/session/rate limit 등에 활용 가능

Cache Aside Pattern:

```text
1. cache 조회
2. miss면 DB 조회
3. DB 결과를 cache에 저장
4. 다음 요청부터 cache 사용
```

주의점:

- cache와 DB 정합성
- cache stampede
- TTL 설계

### Thread

Process:

- 독립된 메모리 공간을 가진 실행 단위

Thread:

- process 안에서 실행되는 작업 단위
- heap 등 일부 메모리를 공유한다.

Thread Pool 사용 이유:

- thread 생성/삭제 비용 감소
- 동시 실행 수 제한
- 서버 리소스 보호

`synchronized`:

- monitor lock 기반으로 임계영역에 한 번에 하나의 thread만 진입하게 한다.

`volatile`:

- 변수 변경이 다른 thread에 보이도록 visibility를 보장한다.
- 복합 연산의 atomicity는 보장하지 않는다.

## 실제 출제 TOP 35

### Java

1. JVM
2. GC
3. HashMap
4. ConcurrentHashMap
5. StringBuilder
6. equals/hashCode
7. Collection Framework
8. OOP 4대 특성
9. Generic과 type erasure

### Spring

10. IoC
11. DI
12. Bean
13. AOP
14. Transaction
15. Propagation
16. Filter
17. Interceptor
18. Spring MVC 요청 처리 흐름

### DB

19. Index
20. Join
21. N+1
22. Transaction
23. Isolation Level
24. Deadlock
25. 정규화
26. 기본 SQL: DDL/DML/DCL, ORDER BY, LIMIT, COUNT, DISTINCT

### Network

27. TCP vs UDP
28. 3-way Handshake
29. 4-way Handshake
30. HTTP vs HTTPS
31. Socket
32. OSI 7 Layer
33. IP 주소, Port, Socket 관계
34. HTTP header/body와 Content-Type/Authorization header

### Backend 설계

35. REST API, JWT, Cache

## 수진 이력서 기준 추가 준비

아래 항목은 필기보다 기술면접으로 이어질 가능성이 높지만, 서술형 필기에도 나올 수 있다.

- Spring Batch 구조
- Chunk vs Tasklet
- `REQUIRES_NEW`
- MyBatis 동작 원리
- FeignClient
- Parquet
- MSA
- S3
- Aurora MySQL
- 운영DB/통계DB 분리 이유
- DB를 물리 분리한 이유
- 실패 격리 전략
- 트랜잭션 전파 속성

## 경력직 서술형 답변 소재

### 성능 개선 경험

답변 소재:

- 통계 DB 분리
- 운영 DB 부하 감소
- batch 처리 단위 조정
- `REQUIRES_NEW` 적용
- 장애 격리

### 트랜잭션 처리 경험

답변 소재:

- Spring Batch
- service_id 단위 처리
- `REQUIRES_NEW`
- 전체 실패 대신 부분 실패 격리

### 장애 대응 경험

답변 소재:

- Schema Validation
- reset 로직 개선
- S3 업로드 실패 처리
- 로그 기반 원인 추적
- 재처리 기준 정리

## 기존 예상문제 문서 검수 결과

대상 문서:

- `interviews/company/텔코웨어/written-test-expected-questions.md`

### 이미 반영되어 있던 항목

- JVM
- GC
- HashMap
- ConcurrentHashMap
- equals/hashCode
- String/StringBuilder/StringBuffer
- Collection
- IoC/DI/Bean/AOP
- `@Transactional`
- Filter/Interceptor
- Index/Join/Transaction/Isolation Level/Deadlock
- GET/POST/PUT/PATCH
- HTTP 상태코드
- JWT
- Session
- TCP/UDP
- 3-way Handshake
- 4-way close
- TLS
- OSI 7 Layer
- Process vs Thread
- synchronized
- volatile
- ThreadPool
- MSA
- Redis
- Cache Aside

### 보강이 필요했던 항목

아래 항목은 기존 문서에 없거나 약하게 들어가 있어 추가 반영했다.

- OOP 4대 특성
- 정규화/반정규화
- HTTP vs HTTPS 직접 비교
- HTTPS/TLS 암호화 흐름
- Socket 정의
- ServerSocket 통신 흐름
- TCP 신뢰성 보장 원리
- HTTP stateless와 상태 유지 방식
- JWT 사용 이유와 주의점
- Connection Pool 설명
- Cache 사용 이유
- Redis 장점
- Spring Batch
- Chunk vs Tasklet
- `REQUIRES_NEW`
- MyBatis
- FeignClient
- Parquet
- S3 업로드 실패 정합성
- Aurora MySQL
- 운영DB/통계DB 물리 분리
- 실패 격리 전략
- service_id 단위 처리

### 서브에이전트 추가 검수 후 보강한 항목

서브에이전트 검수 결과, 문서 전체에는 큰 누락이 없지만 TOP 30 우선순위와 일부 기본기가 약하다는 지적이 있었다. 이에 아래 항목을 추가 반영했다.

- TOP 30을 TOP 35로 확장하고 OOP, Thread, HTTP method/status, 정규화, Spring MVC 흐름, timeout 관점을 더 드러나게 재정렬
- Java Generic
- type erasure
- SOLID 중 OCP/DIP
- Spring MVC 요청 처리 흐름
- Servlet과 DispatcherServlet 관계
- IP 주소, Port, Socket 관계
- HTTP header/body, Content-Type, Authorization header
- DDL/DML/DCL
- `ORDER BY`, `LIMIT`, `COUNT`, `DISTINCT`
- connection timeout, read timeout, socket timeout 차이

## 우선순위 낮게 봐도 되는 항목

아래 항목은 문서에는 남겨두되, 필기 직전에는 정의와 역할만 짧게 보는 수준이면 충분하다.

- SEPP, UPF, NRF, UDM/UDR, MANO, VNF/CNF
- Kubernetes readiness/liveness probe
- Saga, 2PC, CQRS, Kafka vs RabbitMQ
- deserialization, file upload, password hashing

## 최종 판단

현재 예상문제 문서는 네가 가져온 GPT 분석과 서브에이전트 검수 의견의 핵심을 포함하도록 보강됐다. 특히 텔코웨어 특성상 `TCP/IP + OSI 7계층 + HTTP/HTTPS + Socket + Thread`는 별도 우선순위로 보고 준비해야 한다.

필기시험 전까지는 아래 순서로 공부하는 것이 가장 효율적이다.

1. Java: JVM, GC, HashMap, ConcurrentHashMap, equals/hashCode
2. Spring: IoC/DI, Bean, AOP, Transaction, Propagation
3. DB: Index, Join, Isolation Level, Deadlock, 정규화
4. Network: TCP/UDP, 3-way, 4-way, HTTP/HTTPS, OSI 7계층, Socket
5. Thread: Process vs Thread, synchronized, volatile, ThreadPool
6. Resume: Spring Batch, REQUIRES_NEW, 운영DB/통계DB 분리, S3, FeignClient
