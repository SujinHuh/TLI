# 비동기 처리와 Queue 기반 작업 분리

## 한 줄 정의
즉시 응답할 필요가 없는 작업은 Queue에 넣고 Worker가 나중에 처리하게 분리하면, REST API 응답 지연과 서버 부하를 줄일 수 있다.

## 핵심 내용
REST API는 기본적으로 동기 요청/응답 구조다.  
하지만 모든 작업을 요청 안에서 끝낼 필요는 없다.

즉시 응답하지 않아도 되는 작업은 비동기로 분리할 수 있다.

예시:

- 이메일 발송
- 알림 전송
- 이미지 처리
- 통계 집계
- 로그 적재
- 대용량 리포트 생성

기본 구조는 다음과 같다.

```text
Client
  -> API Server
    -> Queue
      -> Worker
```

API Server는 요청을 받은 뒤 작업을 Queue에 넣고 빠르게 응답한다.  
Worker는 Queue에서 작업을 꺼내 실제 처리를 수행한다.

## REST에서의 비동기 응답
REST API에서는 `202 Accepted`를 사용할 수 있다.

```http
POST /reports

202 Accepted
{
  "jobId": "abc-123",
  "status": "PENDING"
}
```

클라이언트는 이후 상태 조회 API로 작업 결과를 확인한다.

```http
GET /reports/abc-123/status
```

## Kotlin Channel과 외부 Queue 차이
Kotlin Channel은 단일 애플리케이션 내부에서 producer와 consumer를 연결하는 데 사용할 수 있다.

```text
Producer -> Kotlin Channel -> Consumer
```

하지만 서버가 여러 대가 되면 각 서버의 Channel은 각 프로세스 메모리 안에만 존재한다.  
즉, 여러 서버가 같은 작업 큐를 공유하기 어렵다.

운영 환경에서 여러 서버가 함께 작업을 처리해야 한다면 외부 메시지 큐를 고려한다.

- Kafka
- RabbitMQ
- AWS SQS
- Redis Streams

## 주의할 점
- 비동기 처리는 즉시 처리하지 않아도 되는 작업에 적합하다.
- 사용자는 작업이 끝났는지 확인할 수 있는 상태 조회 방법이 필요하다.
- 작업 실패 시 재시도 전략이 필요하다.
- 중복 처리 방지와 멱등성을 고려해야 한다.
- Queue가 쌓이면 Worker 확장이나 처리량 조정이 필요하다.
- 단일 서버 내부 비동기와 분산 환경의 Queue 기반 비동기는 구분해야 한다.

## 관련 Daily
- `daily/2026/2026-05-25(월) 문서화를 위한 하네스 프로그래밍과 REST API 요청 증가 해결 전략 정리.md`
