# 텔코웨어 1차 필기시험 예상문제

## 준비 방향

텔코웨어의 Web Application back-end 개발 직무는 Java, Spring Boot, RDB, Gradle/Tomcat, MSA, RESTful 경험을 요구한다. 회사 도메인은 통신 Core Network, IMS, 5G/LTE Core, Cloud/VNF/CNF 쪽이므로 일반 백엔드 필기보다 네트워크, Linux, DB, 동시성, 고가용성 문제 비중이 높을 가능성이 있다.

아래 문제는 실제 기출이 아니라, 회사 정보와 채용 키워드에 맞춰 뽑은 예상 문제다.

## 1. Java 기본 문법과 객체지향

1. Java에서 `==`와 `equals()`의 차이를 설명하시오.
2. `hashCode()`와 `equals()`를 함께 재정의해야 하는 이유를 설명하시오.
3. `String`, `StringBuilder`, `StringBuffer`의 차이를 설명하시오.
4. Java의 primitive type과 wrapper type의 차이를 설명하시오.
5. 오토박싱/언박싱이 성능 문제를 만들 수 있는 상황을 예로 드시오.
6. `final` 키워드를 변수, 메서드, 클래스에 붙였을 때 각각의 의미를 설명하시오.
7. 추상 클래스와 인터페이스의 차이를 설명하시오.
8. Java 8 이후 인터페이스의 `default method`가 필요한 이유를 설명하시오.
9. 오버로딩과 오버라이딩의 차이를 설명하시오.
10. 다형성이 실제 백엔드 코드에서 어떤 장점을 주는지 예시를 드시오.
11. 접근 제어자 `private`, `default`, `protected`, `public`의 범위를 설명하시오.
12. 불변 객체가 필요한 이유와 만드는 방법을 설명하시오.
13. `record` 타입의 장점과 한계를 설명하시오.
14. `enum`을 단순 문자열 상수 대신 사용할 때의 장점을 설명하시오.
15. Checked Exception과 Unchecked Exception의 차이를 설명하시오.
16. 예외를 무조건 `RuntimeException`으로 감싸는 방식의 장단점을 설명하시오.
17. try-with-resources가 필요한 이유를 설명하시오.
18. Java에서 `Object` 클래스의 주요 메서드를 나열하고 설명하시오.
19. static 변수와 instance 변수의 차이를 설명하시오.
20. static method에서 instance field에 직접 접근할 수 없는 이유를 설명하시오.
21. 객체지향의 4대 특성인 캡슐화, 상속, 추상화, 다형성을 설명하시오.
22. 캡슐화가 유지보수성과 안정성에 어떤 도움을 주는지 설명하시오.
23. 상속보다 조합을 선호하는 이유를 설명하시오.
24. Java Generic이 필요한 이유와 장점을 설명하시오.
25. type erasure가 무엇인지 설명하시오.
26. SOLID 원칙 중 OCP와 DIP를 설명하시오.

## 2. Java Collection과 자료구조

1. `ArrayList`와 `LinkedList`의 내부 구조와 시간 복잡도를 비교하시오.
2. `HashMap`의 기본 동작 원리를 설명하시오.
3. `HashMap`에서 hash collision이 발생하면 어떻게 처리되는지 설명하시오.
4. `HashMap`과 `ConcurrentHashMap`의 차이를 설명하시오.
5. `HashSet`이 중복을 제거하는 원리를 설명하시오.
6. `TreeMap`과 `HashMap`의 차이를 설명하시오.
7. `Queue`, `Deque`, `Stack`의 용도를 비교하시오.
8. LRU Cache를 구현한다면 어떤 자료구조를 사용할지 설명하시오.
9. Java Stream API의 장점과 단점을 설명하시오.
10. Stream의 `map`, `flatMap`, `filter`, `reduce` 차이를 설명하시오.
11. `Optional`을 사용할 때 주의할 점을 설명하시오.
12. `List`를 순회하면서 요소를 삭제할 때 발생할 수 있는 문제와 해결 방법을 설명하시오.
13. Comparable과 Comparator의 차이를 설명하시오.
14. `Collections.unmodifiableList()`와 불변 컬렉션의 차이를 설명하시오.
15. 대량 데이터 처리에서 Stream 사용 시 주의할 점을 설명하시오.

## 3. Java 동시성

1. 프로세스와 스레드의 차이를 설명하시오.
2. Java에서 스레드를 생성하는 방법을 두 가지 이상 설명하시오.
3. `synchronized`의 동작 원리를 설명하시오.
4. `volatile`의 의미와 한계를 설명하시오.
5. `AtomicInteger`가 thread-safe한 이유를 설명하시오.
6. race condition이 무엇인지 예시와 함께 설명하시오.
7. deadlock의 발생 조건 4가지를 설명하시오.
8. deadlock을 예방하거나 회피하는 방법을 설명하시오.
9. `wait()`와 `sleep()`의 차이를 설명하시오.
10. `notify()`와 `notifyAll()`의 차이를 설명하시오.
11. ExecutorService를 사용하는 이유를 설명하시오.
12. ThreadPool의 core size와 max size를 어떻게 정할지 설명하시오.
13. CPU-bound 작업과 I/O-bound 작업의 스레드 풀 크기 기준을 비교하시오.
14. `Future`와 `CompletableFuture`의 차이를 설명하시오.
15. 병렬 처리에서 공유 mutable state가 위험한 이유를 설명하시오.
16. 고가용성 통신 서버에서 동시성 버그가 치명적인 이유를 설명하시오.
17. 멀티스레드 환경에서 singleton을 안전하게 만드는 방법을 설명하시오.
18. ThreadLocal의 용도와 메모리 누수 위험을 설명하시오.
19. BlockingQueue가 어떤 상황에서 유용한지 설명하시오.
20. Java memory model에서 happens-before 관계가 필요한 이유를 설명하시오.

## 4. JVM과 성능

1. JVM 메모리 구조를 설명하시오.
2. heap과 stack의 차이를 설명하시오.
3. GC가 필요한 이유와 stop-the-world가 무엇인지 설명하시오.
4. Young Generation과 Old Generation의 역할을 설명하시오.
5. Minor GC와 Major GC의 차이를 설명하시오.
6. 메모리 누수가 발생하는 Java 코드 예시를 설명하시오.
7. OutOfMemoryError 발생 시 확인할 지표와 로그를 설명하시오.
8. CPU 사용률이 높은 Java 프로세스를 분석하는 순서를 설명하시오.
9. thread dump에서 deadlock 또는 blocking 상태를 어떻게 확인할지 설명하시오.
10. heap dump를 분석해야 하는 상황을 설명하시오.
11. JIT 컴파일러의 역할을 설명하시오.
12. class loader의 역할을 설명하시오.
13. 객체 생성이 많은 코드가 성능에 미치는 영향을 설명하시오.
14. Java 서버에서 connection pool 누수가 발생하면 어떤 증상이 나타나는지 설명하시오.
15. latency가 중요한 서버에서 GC 튜닝이 왜 중요한지 설명하시오.

## 5. Spring Boot와 Spring Framework

1. Spring Framework의 IoC와 DI를 설명하시오.
2. Bean 생명주기를 설명하시오.
3. Singleton Bean이 thread-safe하지 않을 수 있는 이유를 설명하시오.
4. `@Component`, `@Service`, `@Repository`, `@Controller`의 차이를 설명하시오.
5. `@RestController`와 `@Controller`의 차이를 설명하시오.
6. Spring Boot Auto Configuration의 동작 원리를 설명하시오.
7. `@SpringBootApplication`에 포함된 주요 annotation을 설명하시오.
8. Filter와 Interceptor, AOP의 차이를 설명하시오.
9. AOP를 로깅, 트랜잭션, 인증에 사용할 수 있는 이유를 설명하시오.
10. Spring에서 프록시 기반 AOP의 한계를 설명하시오.
11. `@Transactional`의 동작 원리를 설명하시오.
12. 같은 클래스 내부 메서드 호출에서 `@Transactional`이 적용되지 않을 수 있는 이유를 설명하시오.
13. `@Transactional(readOnly = true)`의 의미를 설명하시오.
14. transaction propagation 옵션 중 REQUIRED와 REQUIRES_NEW의 차이를 설명하시오.
15. Controller, Service, Repository 계층을 나누는 이유를 설명하시오.
16. DTO와 Entity를 분리하는 이유를 설명하시오.
17. validation을 Controller에서 할지 Service에서 할지 기준을 설명하시오.
18. `@ControllerAdvice`를 사용하는 이유를 설명하시오.
19. Spring Boot Actuator로 확인할 수 있는 정보를 설명하시오.
20. 운영 환경에서 profile을 분리해야 하는 이유를 설명하시오.
21. Spring MVC 요청 처리 흐름을 `Filter -> DispatcherServlet -> Controller` 관점에서 설명하시오.
22. Servlet과 DispatcherServlet의 관계를 설명하시오.

## 6. REST API와 Web Backend

1. RESTful API의 특징을 설명하시오.
2. HTTP method GET, POST, PUT, PATCH, DELETE의 차이를 설명하시오.
3. GET 요청이 idempotent해야 하는 이유를 설명하시오.
4. PUT과 PATCH의 차이를 설명하시오.
5. HTTP status code 200, 201, 204, 400, 401, 403, 404, 409, 500의 의미를 설명하시오.
6. API에서 pagination을 설계하는 방법을 설명하시오.
7. offset pagination과 cursor pagination의 차이를 설명하시오.
8. API versioning 전략을 설명하시오.
9. request/response DTO를 분리하는 이유를 설명하시오.
10. 멱등성이 중요한 API 예시를 설명하시오.
11. 중복 요청 방지 idempotency key를 설계하는 방법을 설명하시오.
12. CORS가 무엇이고 언제 문제가 되는지 설명하시오.
13. JWT의 구조와 주의할 점을 설명하시오.
14. Session 기반 인증과 Token 기반 인증의 차이를 설명하시오.
15. rate limiting이 필요한 이유와 구현 방법을 설명하시오.
16. API timeout을 설정해야 하는 이유를 설명하시오.
17. 외부 API 연동 시 retry를 무조건 걸면 위험한 이유를 설명하시오.
18. circuit breaker 패턴의 목적을 설명하시오.
19. REST API에서 에러 응답 포맷을 표준화해야 하는 이유를 설명하시오.
20. 서버 간 통신에서 correlation id 또는 trace id가 필요한 이유를 설명하시오.

## 7. RDB, SQL, 트랜잭션

1. RDB와 NoSQL의 차이를 설명하시오.
2. primary key와 unique key의 차이를 설명하시오.
3. foreign key의 장점과 단점을 설명하시오.
4. index의 동작 원리를 설명하시오.
5. B-Tree index가 range query에 유리한 이유를 설명하시오.
6. composite index에서 컬럼 순서가 중요한 이유를 설명하시오.
7. index를 많이 만들면 왜 쓰기 성능이 저하되는지 설명하시오.
8. full table scan이 발생하는 원인을 설명하시오.
9. SQL 실행 계획에서 확인해야 할 항목을 설명하시오.
10. N+1 query 문제가 무엇인지 설명하시오.
11. join의 종류 inner join, left join, right join을 설명하시오.
12. group by와 having의 차이를 설명하시오.
13. where 조건과 having 조건의 실행 의미를 비교하시오.
14. transaction의 ACID를 설명하시오.
15. isolation level READ COMMITTED와 REPEATABLE READ의 차이를 설명하시오.
16. dirty read, non-repeatable read, phantom read를 설명하시오.
17. optimistic lock과 pessimistic lock의 차이를 설명하시오.
18. deadlock이 DB에서 발생하는 예시와 해결 방법을 설명하시오.
19. connection pool이 고갈되는 원인을 설명하시오.
20. batch insert 성능을 높이는 방법을 설명하시오.
21. MariaDB와 PostgreSQL에서 sequence/auto increment 전략 차이를 설명하시오.
22. 대량 로그 테이블을 설계할 때 partitioning을 고려하는 이유를 설명하시오.
23. 통신 시스템의 가입자/세션 데이터처럼 읽기와 쓰기가 많은 테이블의 인덱스 설계 기준을 설명하시오.
24. 장애 복구를 위해 DB 변경 이력을 남기는 방법을 설명하시오.
25. DB migration 도구를 사용하는 이유를 설명하시오.
26. 정규화가 필요한 이유와 1정규형, 2정규형, 3정규형의 차이를 설명하시오.
27. 반정규화를 고려해야 하는 상황을 설명하시오.
28. Aurora MySQL 같은 managed DB를 사용할 때 운영 관점에서 장점과 주의할 점을 설명하시오.
29. 운영 DB와 통계 DB를 물리적으로 분리하는 이유를 설명하시오.
30. 통계성 조회나 배치가 운영 DB에 주는 부하를 줄이는 방법을 설명하시오.
31. DDL, DML, DCL의 차이를 설명하시오.
32. `ORDER BY`, `LIMIT`, `COUNT`, `DISTINCT`의 용도와 성능상 주의점을 설명하시오.

## 8. Linux와 운영체제

1. Linux에서 process 상태 `R`, `S`, `D`, `Z`의 의미를 설명하시오.
2. zombie process가 생기는 이유를 설명하시오.
3. `top`, `htop`, `ps`, `netstat` 또는 `ss` 명령어의 용도를 설명하시오.
4. 특정 포트를 점유한 프로세스를 찾는 방법을 설명하시오.
5. CPU load average의 의미를 설명하시오.
6. context switching이 많아지면 성능이 저하되는 이유를 설명하시오.
7. file descriptor가 고갈되면 어떤 문제가 생기는지 설명하시오.
8. Linux에서 open file limit을 확인하고 조정하는 방법을 설명하시오.
9. log file이 디스크를 가득 채웠을 때 발생하는 문제를 설명하시오.
10. `tail -f`, `grep`, `awk`, `sed`를 장애 분석에 어떻게 사용할지 설명하시오.
11. foreground process와 background process의 차이를 설명하시오.
12. signal `SIGTERM`과 `SIGKILL`의 차이를 설명하시오.
13. graceful shutdown이 필요한 이유를 설명하시오.
14. cron과 systemd timer의 차이를 설명하시오.
15. 운영 서버에서 timezone 설정이 중요한 이유를 설명하시오.

## 9. 네트워크와 TCP/IP

1. OSI 7 Layer와 TCP/IP 4 Layer를 설명하시오.
2. TCP와 UDP의 차이를 설명하시오.
3. TCP 3-way handshake를 설명하시오.
4. TCP 4-way close 과정을 설명하시오.
5. TIME_WAIT 상태가 필요한 이유를 설명하시오.
6. connection timeout과 read timeout의 차이를 설명하시오.
7. keep-alive가 필요한 이유를 설명하시오.
8. HTTP/1.1과 HTTP/2의 차이를 설명하시오.
9. TLS handshake의 목적을 설명하시오.
10. DNS resolution 과정을 설명하시오.
11. NAT가 무엇인지 설명하시오.
12. load balancer L4와 L7의 차이를 설명하시오.
13. health check가 잘못 설정되면 어떤 문제가 생기는지 설명하시오.
14. packet loss가 API latency에 미치는 영향을 설명하시오.
15. socket programming에서 backlog의 의미를 설명하시오.
16. 서버가 `Connection refused`를 반환하는 상황을 설명하시오.
17. 서버가 `Connection timed out`을 반환하는 상황을 설명하시오.
18. 통신 Core 시스템에서 네트워크 지연과 장애 감지가 중요한 이유를 설명하시오.
19. long-lived connection과 short-lived connection의 장단점을 설명하시오.
20. 메시지 프로토콜 설계 시 header/body를 분리하는 이유를 설명하시오.
21. HTTP와 HTTPS의 차이를 설명하시오.
22. HTTPS에서 TLS가 어떤 역할을 하는지 설명하시오.
23. TCP가 신뢰성을 보장하는 방법을 ACK, sequence number, 재전송, 흐름제어, 혼잡제어 관점에서 설명하시오.
24. HTTP가 TCP 위에서 동작한다는 말의 의미를 설명하시오.
25. HTTP가 stateless하다는 말의 의미를 설명하시오.
26. 서버가 상태를 유지하기 위해 Session, Cookie, JWT를 사용하는 방식을 비교하시오.
27. Socket이 무엇인지 설명하시오.
28. ServerSocket 기반 socket 통신 과정을 `bind`, `listen`, `accept`, `send/receive` 흐름으로 설명하시오.
29. TCP 연결 종료가 3-way가 아니라 4-way로 이루어지는 이유를 설명하시오.
30. OSI 7계층에서 HTTP, TCP, IP, Ethernet이 각각 어느 계층에 속하는지 설명하시오.
31. IP 주소, Port, Socket의 관계를 설명하시오.
32. HTTP header, body, Content-Type, Authorization header의 역할을 설명하시오.
33. connection timeout, read timeout, socket timeout의 차이를 설명하시오.

## 10. 알고리즘과 코딩 테스트형 문제

1. 배열에서 중복되지 않는 첫 번째 값을 찾는 알고리즘을 작성하시오.
2. 문자열이 palindrome인지 확인하는 함수를 작성하시오.
3. 괄호 문자열이 올바른지 판별하는 함수를 작성하시오.
4. LRU Cache를 구현하시오.
5. 두 정렬 배열을 병합하는 함수를 작성하시오.
6. linked list에서 cycle을 감지하는 알고리즘을 설명하시오.
7. binary search를 구현하고 시간 복잡도를 설명하시오.
8. BFS와 DFS의 차이를 설명하고 각각 구현하시오.
9. graph에서 최단 경로를 구하는 알고리즘을 설명하시오.
10. Dijkstra 알고리즘이 음수 간선에서 사용할 수 없는 이유를 설명하시오.
11. sliding window를 사용해 연속 부분 배열의 최대합을 구하시오.
12. hash map을 사용해 two sum 문제를 해결하시오.
13. 대량 로그에서 가장 많이 등장한 user id 상위 K개를 찾는 방법을 설명하시오.
14. 문자열 배열을 anagram group으로 묶는 알고리즘을 작성하시오.
15. 재귀와 반복문의 장단점을 설명하시오.
16. stack overflow가 발생하는 재귀 코드를 어떻게 개선할지 설명하시오.
17. 시간 복잡도 O(N), O(N log N), O(N^2)의 차이를 예시로 설명하시오.
18. 통신 이벤트 로그에서 특정 시간 구간의 요청 수를 빠르게 구하는 자료구조를 설계하시오.
19. 장애 이벤트가 시간순으로 들어올 때 최근 5분간 실패율을 계산하는 방법을 설계하시오.
20. 문자열 형태의 프로토콜 메시지를 파싱하고 필수 필드를 검증하는 코드를 작성하시오.

## 11. 설계와 아키텍처

1. Monolithic Architecture와 MSA의 차이를 설명하시오.
2. MSA의 장점과 단점을 설명하시오.
3. service discovery가 필요한 이유를 설명하시오.
4. API Gateway의 역할을 설명하시오.
5. circuit breaker, bulkhead, retry, timeout의 차이를 설명하시오.
6. 분산 시스템에서 eventual consistency가 필요한 상황을 설명하시오.
7. Saga 패턴과 2PC의 차이를 설명하시오.
8. message queue를 사용하는 이유를 설명하시오.
9. Kafka와 RabbitMQ의 차이를 설명하시오.
10. event-driven architecture의 장단점을 설명하시오.
11. CQRS가 필요한 상황과 단점을 설명하시오.
12. cache aside 패턴을 설명하시오.
13. cache stampede가 무엇이고 어떻게 막을 수 있는지 설명하시오.
14. Redis를 session store로 사용할 때 주의할 점을 설명하시오.
15. 고가용성 서버 설계에서 active-active와 active-standby를 비교하시오.
16. 장애 격리를 위해 시스템을 어떻게 나눌지 설명하시오.
17. 배포 중 무중단을 달성하는 방법을 설명하시오.
18. blue-green 배포와 rolling 배포의 차이를 설명하시오.
19. configuration을 코드와 분리해야 하는 이유를 설명하시오.
20. 통신망 솔루션에서 안정성과 관측성이 중요한 이유를 설명하시오.
21. Cache를 사용하는 이유와 주의할 점을 설명하시오.
22. Redis를 cache로 사용할 때 장점과 장애 시 주의할 점을 설명하시오.
23. Cache Aside Pattern의 동작 방식과 단점을 설명하시오.
24. 실패 격리 전략이 필요한 이유를 설명하고, circuit breaker와 bulkhead를 예로 들어 설명하시오.

## 12. Tomcat, Gradle, 배포

1. Tomcat의 역할을 설명하시오.
2. Servlet container와 Spring Boot embedded Tomcat의 관계를 설명하시오.
3. Tomcat thread pool이 고갈되면 어떤 증상이 나타나는지 설명하시오.
4. Tomcat max threads와 DB connection pool size를 함께 고려해야 하는 이유를 설명하시오.
5. Gradle과 Maven의 차이를 설명하시오.
6. Gradle multi-module project의 장점을 설명하시오.
7. dependency conflict가 발생했을 때 해결 방법을 설명하시오.
8. build profile 또는 environment별 설정 분리가 필요한 이유를 설명하시오.
9. jar 배포와 war 배포의 차이를 설명하시오.
10. 운영 배포 전 smoke test가 필요한 이유를 설명하시오.
11. rollback 가능한 배포 전략을 설명하시오.
12. application log와 access log를 분리해야 하는 이유를 설명하시오.
13. health check endpoint를 설계할 때 DB까지 확인할지 기준을 설명하시오.
14. graceful shutdown 시 처리 중인 요청을 어떻게 마무리할지 설명하시오.
15. 장애 시 빠르게 원인을 좁히기 위해 어떤 로그 필드를 남길지 설명하시오.

## 13. 보안

1. SQL Injection이 무엇이고 어떻게 방어하는지 설명하시오.
2. XSS와 CSRF의 차이를 설명하시오.
3. password를 평문 저장하면 안 되는 이유를 설명하시오.
4. bcrypt, scrypt, Argon2 같은 password hashing이 필요한 이유를 설명하시오.
5. 인증과 인가의 차이를 설명하시오.
6. least privilege 원칙을 설명하시오.
7. TLS를 사용해도 application level 보안이 필요한 이유를 설명하시오.
8. API key를 코드에 직접 넣으면 안 되는 이유를 설명하시오.
9. 로그에 개인정보나 토큰을 남기면 안 되는 이유를 설명하시오.
10. deserialization 취약점이 무엇인지 설명하시오.
11. file upload 기능에서 검증해야 할 항목을 설명하시오.
12. dependency vulnerability를 관리하는 방법을 설명하시오.
13. 통신 시스템에서 signaling message 위변조를 방지하기 위한 일반적인 보안 고려사항을 설명하시오.
14. 내부망 서비스라도 인증/인가가 필요한 이유를 설명하시오.
15. 운영 권한 계정과 개발 권한 계정을 분리해야 하는 이유를 설명하시오.

## 14. 통신 도메인 기초

1. 이동통신 Core Network가 하는 역할을 설명하시오.
2. IMS가 무엇이고 어떤 서비스를 위해 사용되는지 설명하시오.
3. HLR과 HSS의 역할을 설명하시오.
4. 5G Core에서 UDM과 UDR의 역할을 설명하시오.
5. NRF가 필요한 이유를 설명하시오.
6. UPF의 역할을 설명하시오.
7. SEPP가 필요한 상황을 설명하시오.
8. 가입자 정보와 세션 정보는 왜 정합성이 중요한지 설명하시오.
9. 통신망 서버가 일반 웹 서비스보다 고가용성을 강하게 요구하는 이유를 설명하시오.
10. signaling traffic과 user traffic의 차이를 설명하시오.
11. protocol stack이 무엇인지 설명하시오.
12. active-standby 이중화에서 failover 시 고려해야 할 점을 설명하시오.
13. 통신 시스템에서 O&M이 무엇을 의미하는지 설명하시오.
14. 대량 가입자 데이터를 조회하는 API에서 latency를 낮추는 방법을 설명하시오.
15. 장애 발생 시 통신망 서비스 영향 범위를 어떻게 좁혀 볼지 설명하시오.
16. VNF와 CNF의 차이를 설명하시오.
17. Kubernetes 환경에서 CNF를 운영할 때 readiness/liveness probe가 중요한 이유를 설명하시오.
18. MANO가 어떤 역할을 하는지 설명하시오.
19. 네트워크 기능을 cloud native하게 만들 때 어려운 점을 설명하시오.
20. 5G/LTE Core 솔루션 회사에서 Java 백엔드 개발자가 네트워크 지식을 알아야 하는 이유를 설명하시오.

## 15. 실무형 서술 문제

1. API 응답 시간이 갑자기 5초 이상으로 증가했다. 원인을 확인하는 순서를 쓰시오.
2. DB connection pool이 모두 사용 중인 상황에서 어떤 로그와 지표를 확인할지 쓰시오.
3. 특정 API에서 500 error가 증가했다. 배포, DB, 외부 연동, 트래픽 관점에서 확인 순서를 쓰시오.
4. 운영 서버 CPU가 95% 이상으로 유지된다. Java 애플리케이션 기준 분석 절차를 쓰시오.
5. 메모리 사용량이 계속 증가하다 OOM이 발생했다. 확인 절차를 쓰시오.
6. 배치 작업이 중복 실행되어 데이터가 두 번 적재됐다. 재발 방지 설계를 쓰시오.
7. 외부 시스템 호출이 느려져 전체 API가 느려졌다. timeout, retry, circuit breaker 관점에서 개선안을 쓰시오.
8. 대량 데이터 조회 API가 운영 DB에 부하를 준다. 개선 방안을 쓰시오.
9. 장애 발생 시 원인 추적을 위해 로그에 반드시 남겨야 할 값을 쓰시오.
10. 신규 기능 배포 후 장애가 발생했다. rollback과 hotfix 중 어떤 기준으로 선택할지 쓰시오.
11. 통신 Core 시스템의 subscriber 데이터 조회 API를 설계한다고 가정하고, 데이터 정합성과 성능을 모두 고려한 설계를 쓰시오.
12. Spring Boot 기반 Web Application을 Tomcat으로 운영할 때 thread pool, DB pool, timeout 설정을 어떻게 함께 볼지 쓰시오.
13. MSA 구조에서 한 서비스 장애가 전체 장애로 번지지 않게 하는 설계를 쓰시오.
14. PostgreSQL 또는 MariaDB에서 특정 쿼리가 느릴 때 실행 계획을 보고 어떤 항목을 확인할지 쓰시오.
15. Java 서버에서 동시 요청이 증가할 때 병목이 thread인지 DB인지 network인지 구분하는 방법을 쓰시오.
16. Spring Batch에서 Tasklet과 Chunk 방식의 차이를 설명하고, 각각 적합한 상황을 쓰시오.
17. Spring Batch에서 `REQUIRES_NEW`를 사용하는 이유와 주의할 점을 쓰시오.
18. MyBatis의 동작 원리와 JPA와의 차이를 설명하시오.
19. FeignClient를 사용할 때 timeout, retry, fallback을 어떻게 설계할지 쓰시오.
20. S3 업로드 성공 후 DB 저장이 실패하는 상황에서 정합성을 맞추는 방법을 쓰시오.
21. Parquet 파일 형식의 특징과 CSV/JSON 대비 장점을 설명하시오.
22. 운영 DB와 통계 DB를 분리한 경험을 성능, 장애 격리, 트랜잭션 관점에서 설명하시오.
23. Schema Validation 실패나 reset 로직 오류가 발생했을 때 원인 분석과 재발 방지 방법을 쓰시오.
24. 대량 배치 처리에서 service_id 단위로 실패를 격리하는 설계를 쓰시오.

## 16. 객관식으로 나올 수 있는 빠른 확인 문제

1. Java에서 모든 클래스의 최상위 클래스는 무엇인가?
2. `HashMap`의 평균 조회 시간 복잡도는 무엇인가?
3. TCP는 연결형 프로토콜인가 비연결형 프로토콜인가?
4. HTTP 201은 어떤 의미인가?
5. DB transaction의 원자성을 의미하는 ACID 항목은 무엇인가?
6. `SELECT ... FOR UPDATE`는 어떤 종류의 읽기인가?
7. Spring의 DI는 어떤 설계 원칙과 관련이 깊은가?
8. REST에서 GET 요청은 body를 통해 상태를 변경하는 데 사용해야 하는가?
9. Linux에서 현재 열려 있는 TCP listen port를 확인하는 명령어는 무엇인가?
10. Gradle에서 dependency graph를 확인하는 명령은 무엇인가?
11. Tomcat에서 요청 처리 thread가 부족하면 어떤 증상이 나타날 수 있는가?
12. JWT는 서버 세션을 완전히 대체할 수 있는가? 그렇지 않다면 이유는 무엇인가?
13. `volatile`은 atomic 연산을 보장하는가?
14. `READ COMMITTED`에서 non-repeatable read가 발생할 수 있는가?
15. Kubernetes readiness probe와 liveness probe는 각각 어떤 목적을 가지는가?

## 우선순위 높은 복습 키워드

- Java: equals/hashCode, Collection, ConcurrentHashMap, synchronized, volatile, ExecutorService, JVM/GC
- Spring: DI, Bean, AOP, Transaction, REST Controller, validation, exception handling
- DB: index, transaction isolation, lock, execution plan, connection pool, MariaDB/PostgreSQL
- 운영: Linux process, port, thread dump, heap dump, log, graceful shutdown
- Network: TCP, HTTP, timeout, keep-alive, load balancer, DNS, TLS
- Architecture: MSA, RESTful, circuit breaker, retry, queue, cache, HA
- Telecom: IMS, 5G Core, HSS/HLR, UDM/UDR, NRF, UPF, VNF/CNF, O&M
- Resume Based: Spring Batch, Chunk/Tasklet, REQUIRES_NEW, MyBatis, FeignClient, Parquet, S3, Aurora MySQL, 운영DB/통계DB 분리, 실패 격리
