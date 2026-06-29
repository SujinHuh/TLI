# Entity와 DTO 분리

## 한 줄 정의
Entity는 DB와 도메인 모델을 표현하고, DTO는 API 요청과 응답에 필요한 데이터를 전달하기 위해 분리해서 사용하는 객체다.

## 핵심 내용
- Controller에서 Entity를 그대로 반환하면 DB 구조와 내부 도메인 모델이 API 응답으로 노출될 수 있다.
- Entity에는 password, role 같은 민감한 필드가 포함될 수 있어 그대로 반환하면 정보 노출 위험이 있다.
- Entity 구조가 바뀌면 API 응답 구조도 함께 바뀔 수 있어 클라이언트에 영향을 줄 수 있다.
- JPA 양방향 연관관계가 있으면 JSON 직렬화 과정에서 순환 참조가 발생할 수 있다.
- Lazy Loading 관계가 JSON 변환 중 접근되면 예외나 예상하지 못한 추가 쿼리가 발생할 수 있다.
- DTO를 사용하면 API마다 필요한 필드만 명확하게 응답할 수 있다.

## 예시
Entity에는 API 응답에 필요 없는 필드가 있을 수 있다.

```java
public class User {
    private Long id;
    private String email;
    private String password;
    private String role;
}
```

Controller에서 Entity를 그대로 반환하면 `password`, `role` 같은 필드가 응답에 포함될 위험이 있다.

응답 DTO를 사용하면 필요한 필드만 외부로 보낼 수 있다.

```java
public record UserResponse(
    Long id,
    String email
) {
    public static UserResponse from(User user) {
        return new UserResponse(user.getId(), user.getEmail());
    }
}
```

## 주의할 점
- `@JsonIgnore` 같은 어노테이션으로 일부 필드를 숨길 수는 있지만, Entity가 API 응답 정책까지 책임지게 되는 문제가 생길 수 있다.
- API마다 필요한 응답 필드가 다를 수 있으므로 Entity 하나에 JSON 어노테이션을 붙여 해결하려는 방식은 유연하지 않다.
- 필기 답안에서는 Entity 직접 반환의 위험성과 DTO로 분리해야 하는 이유를 먼저 설명하는 것이 좋다.

## 관련 Daily
- [2026-06-29(월) Spring Boot와 Entity DTO 개념 재정리](../../daily/2026/2026-06-29(월)%20Spring%20Boot와%20Entity%20DTO%20개념%20재정리.md)
