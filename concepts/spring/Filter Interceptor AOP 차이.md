# Filter Interceptor AOP 차이

## 한 줄 정의
Filter, Interceptor, AOP는 모두 공통 기능을 중간에 적용하는 방법이지만, 동작하는 위치와 적용 대상이 다르다.

## 핵심 내용
- Filter는 서블릿 컨테이너 영역에서 동작한다.
- Filter는 Spring MVC에 요청이 들어가기 전과 응답이 나가기 전에 요청/응답을 처리한다.
- Interceptor는 Spring MVC 내부에서 동작한다.
- Interceptor는 컨트롤러 실행 전후의 흐름을 가로채 공통 로직을 처리한다.
- AOP는 Spring Bean의 메서드 실행 전후에 공통 기능을 적용한다.
- Filter는 가장 바깥쪽, Interceptor는 컨트롤러 주변, AOP는 메서드 실행 주변에서 동작한다고 정리할 수 있다.

## 예시
```text
Client
 → Filter
 → DispatcherServlet
 → Interceptor
 → Controller
 → Service
 → Repository
```

Filter는 요청이 Spring MVC에 들어가기 전 단계에서 동작하므로 인코딩, CORS, 인증, 로깅처럼 웹 요청 전반에 적용되는 작업에 사용할 수 있다.

Interceptor는 DispatcherServlet 이후 컨트롤러가 실행되기 전후에 동작하므로 로그인 체크, 권한 검사, 컨트롤러 공통 로깅 등에 사용할 수 있다.

AOP는 웹 요청 흐름에만 한정되지 않고 Service나 Repository 같은 Spring Bean의 메서드 실행 전후에 적용할 수 있다. 트랜잭션, 로깅, 성능 측정처럼 여러 계층에 흩어진 공통 관심사를 분리할 때 사용한다.

## 주의할 점
- Filter를 "Spring 바깥쪽"이라고 표현할 수 있지만, 더 정확한 표현은 "서블릿 컨테이너 영역"이다.
- Interceptor는 Spring MVC 내부에서 컨트롤러 호출 전후에 동작한다.
- AOP는 URL 요청 흐름 자체를 가로채는 것이 아니라 Spring Bean의 메서드 실행 지점에 부가 기능을 적용한다.

## 관련 Daily
- [2026-06-28(일) Spring MVC 요청 흐름과 공통 처리 위치 정리](../../daily/2026/2026-06-28(일)%20Spring%20MVC%20요청%20흐름과%20공통%20처리%20위치%20정리.md)
