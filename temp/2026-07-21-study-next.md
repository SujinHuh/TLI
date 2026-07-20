# 2026-07-21 공부 시작 메모

## 이어서 볼 내용
- 처리율 제한 위치를 크게 두 계층으로 나누어 다시 설명해보기
  - 인프라 앞단 계층: CDN, WAF, Load Balancer, Reverse Proxy
  - 애플리케이션에 가까운 계층: API Gateway, Application Middleware
- CDN, WAF, Load Balancer, Reverse Proxy가 애플리케이션에 요청이 도달하기 전에 막는다는 점 정리하기
- 인프라 앞단 계층의 장점과 한계 정리하기
  - 장점: 서버 자원 보호에 유리함
  - 한계: 사용자별 비즈니스 정책을 세밀하게 알기 어려움
- WAF가 잘 판단하는 기준 다시 보기
  - 특정 IP가 너무 많이 요청하는 경우
  - 요청 패턴이 공격처럼 보이는 경우
  - 특정 URL로 비정상 트래픽이 몰리는 경우
- WAF 같은 앞단 계층이 상대적으로 판단하기 어려운 기준 다시 보기
  - 사용자가 무료 요금제인지 유료 요금제인지
  - 특정 API를 사용자별로 하루 500번까지만 허용해야 하는지
  - 특정 회사 계정은 별도 계약으로 제한을 더 풀어줘야 하는지
- API Gateway와 Application Middleware가 인증 정보, 사용자 정보, API 경로, 서비스 정책을 더 잘 알 수 있다는 점 정리하기
- 사용자별, API별, 요금제별 제한 예시 다시 보기
  - 무료 사용자: 분당 100회
  - 유료 사용자: 분당 1000회
  - 로그인하지 않은 사용자: 분당 20회
  - `/order` API: 분당 50회
  - `/search` API: 분당 300회
- Reverse Proxy와 API Gateway 차이 다시 정리하기
  - Reverse Proxy: 요청 전달, SSL 종료, 압축, 캐싱, 기본 라우팅, 기본 제한
  - API Gateway: API 단위 라우팅, 인증, 인가, 로깅, 모니터링, 처리율 제한
- API Gateway와 Application Middleware 차이 다시 정리하기
  - API Gateway: 여러 서비스 앞의 공통 관문
  - Application Middleware: 특정 애플리케이션 내부의 Controller 이전 처리 흐름
- Spring 애플리케이션 기준 Application Middleware가 Filter, Interceptor 같은 Controller 이전 계층을 의미한다는 점 다시 보기
- DDoS 방어는 단순히 중복 API 호출을 막는 것이 아니라, 비정상적으로 많은 요청이나 공격성 트래픽이 서버 자원을 고갈시키지 못하도록 앞단에서 차단하거나 제한하는 정책이라는 점 정리하기

## 면접 설명 문장으로 연습할 내용
처리율 제한은 목적에 따라 위치가 달라진다.
DDoS나 비정상 대량 트래픽 방어처럼 서버 자원 보호가 목적이면 CDN, WAF, Reverse Proxy 같은 앞단 계층에서 먼저 막는 것이 유리하다.
반면 사용자별, API별, 요금제별 제한처럼 비즈니스 정책이 필요한 경우에는 인증 정보와 사용자 정보를 알 수 있는 API Gateway나 Application Middleware에서 처리하는 것이 적합하다.
Spring 애플리케이션 기준으로 Application Middleware는 Filter, Interceptor 같은 Controller 이전 계층을 의미한다.
