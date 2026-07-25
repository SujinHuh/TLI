# 2026-07-25 공부 진행 메모

## 상태
- TLI 공부 진행 중
- 오늘 학습은 아직 완료하지 않음
- 오늘 공부 시간: 30분
- 내일 이어서 정리한 뒤 Git에 올릴 예정

## 오늘 공부한 주제
- Redis, Cache, Kafka 차이
- Redis가 캐시처럼 쓰인다는 말의 의미
- Redis와 Kafka가 시스템에서 놓이는 위치
- 처리율 제한에서 Redis를 사용하는 이유

## Redis, Cache, Kafka 차이

### 1. 쉬운 버전: 15살도 이해하는 설명

#### Cache

캐시는 자주 보는 걸 가까이에 잠깐 놔두는 것이다.

예를 들어 학교에서 자주 보는 프린트가 있다고 해보자.

매번 선생님한테 가서 다시 받으면 귀찮고 오래 걸린다.
그래서 내 책상 위에 복사본을 올려두면 바로 볼 수 있다.

이게 캐시다.

```text
원래 위치: 선생님 / DB
가까운 위치: 내 책상 / 캐시
```

즉 캐시는:

> 자주 쓰는 데이터를 가까운 곳에 잠깐 저장해서 빠르게 꺼내 쓰는 것

#### Redis

Redis는 엄청 빠른 메모장 같은 것이다.

이 메모장은 내용을 이렇게 저장한다.

```text
이름 -> 수진
나이 -> 15
상품번호100 -> 운동화 정보
```

이런 식으로 key와 value로 저장한다.

```text
key = 이름표
value = 실제 내용
```

Redis는 컴퓨터의 메모리에 저장하기 때문에 빠르다.
그래서 캐시로 많이 사용한다.

예를 들어 상품 정보를 보여줘야 할 때:

```text
1. 서버가 Redis를 먼저 확인한다.
2. Redis에 상품 정보가 있으면 바로 보여준다.
3. Redis에 없으면 DB에 가서 가져온다.
4. 가져온 정보를 Redis에 잠깐 저장한다.
5. 다음 사람은 Redis에서 빠르게 본다.
```

정리하면:

> Redis는 자주 쓰는 정보를 빠르게 꺼내기 위한 빠른 저장소다. 캐시 역할을 많이 한다.

#### Kafka

Kafka는 전달함 같은 것이다.

예를 들어 반장이 선생님한테 전달받은 일을 칠판에 써둔다.

```text
"3번 학생 숙제 제출함"
"5번 학생 급식 신청함"
"7번 학생 상담 신청함"
```

그러면 다른 선생님들이 그 내용을 보고 자기 할 일을 처리한다.

Kafka도 비슷하다.

어떤 일이 생기면 메시지로 적어두고, 다른 서비스들이 그 메시지를 읽어서 처리한다.

예를 들어 주문이 들어오면:

```text
주문 서비스: 주문 생성됨!
Kafka: 주문 생성됨 메시지를 저장
결제 서비스: 메시지를 읽고 결제 처리
재고 서비스: 메시지를 읽고 재고 차감
알림 서비스: 메시지를 읽고 알림 발송
```

정리하면:

> Kafka는 어떤 일이 생겼다는 메시지를 저장하고 다른 서비스들에게 전달하는 역할을 한다.

## 2. 개발자 버전

### Cache

Cache는 특정 기술명이 아니라 역할/전략이다.

> 원본 데이터 저장소보다 더 가까운 위치에 데이터를 임시 저장해서 조회 성능을 높이는 방식

캐시는 여러 계층에 존재할 수 있다.

```text
Browser Cache
CDN Cache
Application Local Cache
Redis Cache
DB Buffer Cache
```

대표적인 목적은 다음과 같다.

- DB 부하 감소
- 응답 속도 개선
- 반복 조회 최적화
- 외부 API 호출 비용 감소

일반적인 흐름은 다음과 같다.

```text
Client
 -> Application Server
 -> Cache 조회
    -> Cache Hit: 캐시 데이터 반환
    -> Cache Miss: DB 조회 후 캐시에 저장
 -> DB
```

### Redis

Redis는 in-memory key-value data store이다.

데이터를 메모리에 저장하기 때문에 매우 빠르고, 단순 문자열뿐 아니라 다양한 자료구조를 지원한다.

```text
String
Hash
List
Set
Sorted Set
Stream
```

대표적인 사용 사례:

- Cache
- Session Store
- Rate Limiting Counter
- Distributed Lock
- Pub/Sub
- Ranking
- Temporary Token Storage
- Queue-like Processing

Redis를 캐시로 사용할 때는 보통 TTL을 함께 설정한다.

```text
product:100 -> 상품 정보
TTL: 10분
```

즉 일정 시간이 지나면 Redis에서 데이터가 사라지고, 다음 요청 때 다시 DB에서 조회한다.

처리율 제한에서는 Redis가 중앙 카운터 역할을 한다.

```text
rate_limit:user:123:/search -> 42
TTL: 60초
```

서버가 여러 대여도 같은 Redis를 바라보면 요청 횟수를 공통으로 관리할 수 있다.

```text
API Server A
API Server B -> Redis
API Server C
```

### Kafka

Kafka는 distributed event streaming platform이다.

Redis처럼 빠르게 값을 조회하기 위한 캐시가 아니라, 이벤트를 저장하고 여러 소비자가 읽어가도록 하는 메시지 플랫폼이다.

핵심 개념은 다음과 같다.

```text
Producer: 메시지를 발행하는 쪽
Topic: 메시지가 쌓이는 논리적 공간
Consumer: 메시지를 읽는 쪽
Consumer Group: 같은 역할을 나눠 처리하는 소비자 묶음
```

예시:

```text
Order Service
 -> Kafka Topic: order-created
 -> Payment Service
 -> Stock Service
 -> Notification Service
```

Kafka를 사용하는 이유:

- 서비스 간 결합도 감소
- 비동기 처리
- 트래픽 버퍼링
- 이벤트 기반 아키텍처
- 장애 시 재처리 가능
- 여러 소비자가 같은 이벤트를 독립적으로 처리 가능

## 3. Redis vs Cache vs Kafka 한눈에 비교

| 구분 | Cache | Redis | Kafka |
|---|---|---|---|
| 정체 | 역할/전략 | 메모리 기반 저장소 | 메시지/이벤트 플랫폼 |
| 주요 목적 | 빠른 조회 | 빠른 저장/조회 | 이벤트 전달/비동기 처리 |
| 데이터 형태 | 다양함 | Key-Value | Message/Event |
| 위치 | 여러 계층 | 보통 서버와 DB 사이 | 보통 서비스와 서비스 사이 |
| 사용 예시 | 상품 정보 임시 저장 | 캐시, 세션, 카운터 | 주문 생성 이벤트 전달 |
| 핵심 질문 | 빨리 읽어야 하나? | 빠르게 공유 저장해야 하나? | 나중에/다른 서비스가 처리해야 하나? |

## 4. 위치로 보면

### Redis / Cache 위치

```text
Client
 -> API Server
 -> Redis Cache
 -> DB
```

주로 조회 속도 개선이나 공유 상태 저장에 사용한다.

예:

```text
상품 조회
로그인 세션 확인
요청 횟수 카운팅
인증번호 저장
```

### Kafka 위치

```text
Service A
 -> Kafka
 -> Service B
 -> Service C
```

주로 서비스 간 이벤트 전달이나 비동기 작업 처리에 사용한다.

예:

```text
주문 생성 후 결제 처리
주문 생성 후 재고 차감
주문 생성 후 알림 발송
로그 수집
이벤트 분석
```

## 5. 가장 중요한 정리

```text
Cache는 역할이다.
Redis는 캐시 역할을 할 수 있는 빠른 저장소다.
Kafka는 캐시가 아니라 이벤트를 전달하고 쌓아두는 메시지 플랫폼이다.
```

조금 더 개발자스럽게 말하면:

> Redis는 빠른 읽기/쓰기와 공유 상태 저장이 필요할 때 사용하고, Kafka는 서비스 간 이벤트를 비동기로 전달하고 처리 흐름을 분리하고 싶을 때 사용한다.

## 내일 이어서 볼 내용
- Redis가 처리율 제한에서 중앙 카운터로 쓰이는 흐름 다시 보기
- Redis 캐시와 DB 사이의 Cache Hit / Cache Miss 흐름 다시 설명해보기
- Kafka가 필요한 상황과 Redis로 충분한 상황 비교하기
- 위 내용을 daily 기록으로 옮기고 concepts 후보를 정리하기
