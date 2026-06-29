# Spring Boot 장점

## 한 줄 정의
Spring Boot는 Spring 기반 애플리케이션을 빠르게 만들고 실행할 수 있도록 자동 설정, starter 의존성, 내장 서버, 운영 기능을 제공하는 프레임워크다.

## 핵심 내용
- 자동 설정을 제공해 반복적인 Spring 설정을 줄여준다.
- starter 의존성을 제공해 필요한 라이브러리 조합을 쉽게 가져올 수 있다.
- Tomcat 같은 내장 WAS를 제공해 `java -jar` 방식으로 애플리케이션을 실행할 수 있다.
- Actuator를 통해 헬스 체크, 메트릭 같은 운영 기능을 쉽게 붙일 수 있다.
- 초기 개발과 배포가 단순해져 빠르게 애플리케이션을 만들 수 있다.

## 예시
`spring-boot-starter-web`을 추가하면 Spring MVC, 내장 Tomcat, JSON 처리에 필요한 기본 구성이 함께 잡힌다.

```text
기존 Spring
 → 필요한 설정과 의존성을 직접 많이 구성

Spring Boot
 → starter와 auto configuration으로 기본 구성을 빠르게 제공
```

실행도 별도 WAS 배포 없이 아래처럼 할 수 있다.

```text
java -jar app.jar
```

## 주의할 점
- Spring Boot가 Spring Framework를 대체하는 별개의 기술이라기보다는, Spring 기반 개발을 편하게 해주는 도구라고 이해해야 한다.
- 자동 설정이 편하더라도 실제 운영에서는 어떤 설정이 적용되는지 확인할 수 있어야 한다.
- 필기 답안에서는 "자동 설정, starter, 내장 WAS, 쉬운 배포, 운영 기능"을 중심으로 쓰면 좋다.

## 관련 Daily
- [2026-06-29(월) Spring Boot와 Entity DTO 개념 재정리](../../daily/2026/2026-06-29(월)%20Spring%20Boot와%20Entity%20DTO%20개념%20재정리.md)
