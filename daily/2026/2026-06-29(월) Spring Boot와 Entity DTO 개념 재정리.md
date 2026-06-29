# 📅 2026-06-29(월) Spring Boot와 Entity DTO 개념 재정리

## 🎯 목표
- Spring Boot의 장점을 필기 답안으로 설명할 수 있게 정리
- Controller에서 Entity를 그대로 반환하면 위험한 이유 이해
- Entity와 DTO에서 Lombok 어노테이션을 사용할 때의 기준 정리
- 필기 문제는 문제 의도에 맞춰 개념 중심으로 답해야 한다는 점 확인

## ✅ 완료
- Spring Boot의 장점을 자동 설정, starter 의존성, 내장 WAS, 쉬운 실행과 배포, 운영 기능 제공 관점에서 정리
- Controller에서 Entity를 그대로 반환하면 민감 정보 노출, API와 DB 구조의 결합, 순환 참조, Lazy Loading 문제가 생길 수 있다는 점 정리
- Entity를 직접 반환하지 않고 DTO로 필요한 필드만 응답하는 이유 정리
- Entity에 `@Setter`, `@AllArgsConstructor`, 클래스 레벨 `@Builder`를 무분별하게 쓰면 객체 상태 변경과 생성 규칙이 흐려질 수 있다는 점 정리
- DTO에서는 요청/응답 목적에 맞게 Lombok을 사용할 수 있지만, 응답 DTO는 가능하면 불변에 가깝게 두는 것이 좋다는 점 정리
- 필기 문제에서 어노테이션이 직접 언급되지 않았다면 Lombok 사용법보다 Entity/DTO 분리 이유를 먼저 설명하는 것이 답안 방향에 맞는다는 점 확인
- 예상 문제 검수 시 하나의 주제만 반복하지 않고, 여러 관점의 질문으로 분산해서 내야 한다는 점 확인

## ⏱️ 공부 시간
19:00 ~ 21:00 (총 2시간)

## ✍️ 회고
아는 개념이 머리로는 아는데, 설명이 참 어렵다.
다시 보면서 개념 정리를 하는 중.

## 🔗 관련 Concepts
- [Spring Boot 장점](../../concepts/spring/Spring%20Boot%20장점.md)
- [Entity와 DTO 분리](../../concepts/spring/Entity와%20DTO%20분리.md)
- [Entity와 DTO에서 Lombok 사용 기준](../../concepts/spring/Entity와%20DTO에서%20Lombok%20사용%20기준.md)
