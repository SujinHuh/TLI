# Rate Limiting과 Throttling

## 한 줄 정의
Rate Limiting과 Throttling은 API 요청이 과도하게 들어올 때 요청 수나 요청 속도를 제한해 시스템을 보호하는 방식이다.

## 핵심 내용
API 요청이 너무 많으면 모든 요청을 다 처리하려고 하기보다 시스템을 보호하기 위해 제한을 둘 수 있다.

예를 들어 한 사용자에게 아래와 같은 제한을 걸 수 있다.

```text
1분에 100회 요청 허용
초과 시 429 Too Many Requests 응답
```

Rate Limiting은 일정 시간 동안 허용할 요청 개수를 제한하는 것이다.

```text
사용자 A
- 1분에 100회까지 허용
```

Throttling은 요청 속도를 늦추거나 일정 수준으로 조절하는 것에 가깝다.

## 적용 위치
Rate Limiting과 Throttling은 보통 프론트엔드가 아니라 백엔드나 인프라 계층에서 적용한다.

- API Gateway
- Nginx
- Load Balancer
- Backend Application
- Redis 기반 Rate Limiter

프론트엔드에서도 버튼 중복 클릭 방지나 debounce를 할 수는 있다.  
하지만 사용자가 프론트엔드를 우회해서 직접 API를 호출할 수 있기 때문에, 시스템 보호는 백엔드나 인프라 계층에서 해야 한다.

## 예시
```http
HTTP/1.1 429 Too Many Requests
Retry-After: 60
```

응답 의미:

```text
요청이 너무 많으니 60초 후 다시 시도하라
```

## 주의할 점
- 정상 사용자와 비정상 요청을 구분할 수 있어야 한다.
- 사용자별, IP별, API Key별 제한 기준을 정할 수 있다.
- 너무 강한 제한은 정상 사용자 경험을 해칠 수 있다.
- 너무 약한 제한은 시스템 보호 효과가 떨어질 수 있다.
- Rate Limiting은 시스템을 보호하는 장치이지, 근본적인 성능 개선책은 아니다.

## 관련 Daily
- `daily/2026/2026-05-25(월) 문서화를 위한 하네스 프로그래밍과 REST API 요청 증가 해결 전략 정리.md`
