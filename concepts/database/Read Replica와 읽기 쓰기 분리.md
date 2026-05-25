# Read Replica와 읽기 쓰기 분리

## 한 줄 정의
Read Replica는 Primary DB의 데이터를 복제한 읽기 전용 DB로, 읽기 요청을 분산해 Primary DB의 부하를 줄이는 방식이다.

## 핵심 내용
Primary DB는 쓰기 작업을 담당한다.

```text
Primary DB
- insert
- update
- delete
```

Read Replica는 읽기 작업을 담당한다.

```text
Read Replica
- select
- primary와 거의 같은 데이터 복제
```

기본 구조는 다음과 같다.

```text
쓰기 요청 -> Primary DB
읽기 요청 -> Read Replica
```

Read Replica는 데이터를 나눠 가지는 구조가 아니다.

```text
Replica 1: 1~100
Replica 2: 101~200
```

이런 방식은 Read Replica가 아니라 샤딩에 가깝다.

Read Replica는 보통 Primary DB와 거의 같은 데이터를 복제한다.

```text
Primary DB
Read Replica 1
Read Replica 2
```

## Read Replica와 CQRS 차이
Read Replica는 CQRS와 비슷해 보일 수 있지만 정확히는 다르다.

Read Replica는 같은 데이터 모델을 복제해서 읽기 부하를 분산하는 인프라 전략에 가깝다.

CQRS는 Command와 Query의 책임을 분리하는 아키텍처 패턴이다.

```text
Command
- 쓰기 책임

Query
- 읽기 책임
```

CQRS에서는 읽기 모델과 쓰기 모델이 다를 수 있다.

```text
Command DB
- orders
- order_items
- payments

Query DB
- order_summary_view
- user_order_history
- admin_order_dashboard
```

따라서 Primary DB와 Read Replica로 읽기/쓰기를 나누는 것은 CQRS라기보다는 Read/Write Splitting에 가깝다.  
다만 CQRS를 구현할 때 Query Side 저장소로 Read Replica를 사용할 수는 있다.

## 예시
주문 생성은 Primary DB로 보낸다.

```text
POST /orders -> Primary DB
```

주문 목록 조회는 Read Replica로 보낸다.

```text
GET /orders -> Read Replica
```

## 주의할 점
- Read Replica는 읽기 부하를 줄이는 데 효과적이다.
- 복제 지연이 생길 수 있다.
- 방금 저장한 데이터가 Read Replica에서 바로 조회되지 않을 수 있다.
- 강한 일관성이 필요한 조회는 Primary DB를 읽어야 할 수도 있다.
- Read Replica와 샤딩을 혼동하지 않아야 한다.
- Read Replica와 CQRS는 비슷해 보이지만 목적과 범위가 다르다.

## 관련 Daily
- `daily/2026/2026-05-25(월) 문서화를 위한 하네스 프로그래밍과 REST API 요청 증가 해결 전략 정리.md`
