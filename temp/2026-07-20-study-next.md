# 2026-07-20 공부 시작 메모

## 이어서 볼 내용
- 4장 처리율 제한 장치의 설계 이어서 공부하기
- 처리율 제한 장치를 서버 앞단 어디에 둘 수 있는지 다시 정리하기
  - CDN
  - WAF
  - Load Balancer
  - Reverse Proxy
  - API Gateway
  - Application Middleware
- 앞쪽 계층에 둘 때와 애플리케이션에 가까운 계층에 둘 때의 차이 정리하기
- API별, 사용자별, 요금제별로 정교하게 제한하려면 어떤 정보가 필요한지 정리하기

## 시작할 때 확인할 질문
- CDN/WAF에서 막는 요청과 API Gateway/Application Middleware에서 막는 요청은 기준이 어떻게 다른가?
- DoS 방어 목적의 제한과 비즈니스 정책 목적의 제한은 어디에 두는 것이 자연스러운가?
