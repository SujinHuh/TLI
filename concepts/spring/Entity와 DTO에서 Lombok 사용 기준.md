# Entity와 DTO에서 Lombok 사용 기준

## 한 줄 정의
Lombok은 보일러플레이트 코드를 줄여주지만, Entity와 DTO의 역할에 맞게 어노테이션 사용 범위를 조절해야 한다.

## 핵심 내용
- Lombok을 쓰면 안 되는 것이 아니라 객체 역할에 맞게 제한해서 써야 한다.
- Entity는 DB와 연결되는 도메인 객체이므로 아무 곳에서나 상태가 바뀌면 위험하다.
- Entity에 `@Setter`를 무분별하게 붙이면 값이 왜, 언제, 어떤 규칙으로 바뀌었는지 추적하기 어렵다.
- Entity에 `@AllArgsConstructor`를 열어두면 id, 생성일, 수정일처럼 시스템이 관리해야 하는 값까지 외부에서 넣을 수 있다.
- Entity 클래스 전체에 `@Builder`를 붙이면 모든 필드를 임의로 넣을 수 있어 객체 생성 규칙이 흐려질 수 있다.
- DTO는 요청과 응답 데이터를 전달하는 객체라 Entity보다 Lombok을 비교적 자유롭게 사용할 수 있다.
- 응답 DTO는 가능하면 불변에 가깝게 두는 것이 좋다.

## 예시
Entity에서는 전체 setter보다 의미 있는 변경 메서드를 두는 편이 좋다.

```java
public void changeNickname(String nickname) {
    this.nickname = nickname;
}

public void deactivate() {
    this.status = UserStatus.INACTIVE;
}
```

JPA Entity는 기본 생성자가 필요하지만, 외부에서 막 생성하지 못하도록 접근 범위를 제한할 수 있다.

```java
@NoArgsConstructor(access = AccessLevel.PROTECTED)
@Entity
public class User {
    @Id
    @GeneratedValue
    private Long id;

    private String email;
    private String password;
}
```

DTO에서는 요청/응답 목적에 맞게 Lombok이나 record를 사용할 수 있다.

```java
public record UserResponse(
    Long id,
    String email
) {}
```

## 주의할 점
- Entity의 `@Getter`는 많이 사용하지만, `@Setter`는 무분별하게 열지 않는 것이 좋다.
- Entity에서 Builder가 필요하다면 클래스 전체보다 필요한 필드만 받는 생성자에 제한적으로 붙이는 방식이 더 안전하다.
- 문제에서 Lombok 어노테이션을 직접 묻지 않았다면, 답안의 중심은 Entity/DTO 분리 이유에 두고 Lombok은 보조 설명으로 다루는 것이 좋다.

## 관련 Daily
- [2026-06-29(월) Spring Boot와 Entity DTO 개념 재정리](../../daily/2026/2026-06-29(월)%20Spring%20Boot와%20Entity%20DTO%20개념%20재정리.md)
