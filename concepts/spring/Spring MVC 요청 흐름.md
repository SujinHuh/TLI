# Spring MVC 요청 흐름

## 한 줄 정의
Spring MVC 요청 흐름은 클라이언트 요청을 DispatcherServlet이 중심에서 받아 적절한 컨트롤러로 연결하고, 처리 결과를 응답으로 반환하는 과정이다.

## 핵심 내용
- 클라이언트 요청은 먼저 서블릿 컨테이너의 Filter를 거친다.
- DispatcherServlet은 Spring MVC의 프론트 컨트롤러로, 요청 처리 흐름의 중심 역할을 한다.
- HandlerMapping은 요청 URL과 HTTP Method 등을 기준으로 실행할 컨트롤러를 찾는다.
- HandlerAdapter는 찾은 컨트롤러 메서드를 실제로 실행한다.
- Controller는 요청을 받고, 필요한 비즈니스 로직은 보통 Service에 위임한다.
- Service는 핵심 비즈니스 로직을 처리한다.
- Repository는 DB 접근과 관련된 작업을 담당한다.
- 화면 응답은 ViewResolver와 View를 거칠 수 있고, JSON 응답은 HttpMessageConverter를 통해 변환될 수 있다.

## 예시
```text
클라이언트 요청
 → Filter
 → DispatcherServlet
 → HandlerMapping
 → HandlerAdapter
 → Controller
 → Service
 → Repository
 → Controller
 → 응답
```

화면을 반환하는 경우에는 컨트롤러가 View 이름과 Model 데이터를 반환하고, ViewResolver가 실제 View를 찾아 HTML 응답을 만든다.

```text
Controller
 → ModelAndView
 → ViewResolver
 → View
 → DispatcherServlet
 → 클라이언트 응답
```

JSON을 반환하는 경우에는 `@ResponseBody`나 `@RestController`를 통해 ViewResolver를 거치지 않고, HttpMessageConverter가 객체를 JSON으로 변환해 응답한다.

```text
Controller
 → HttpMessageConverter
 → JSON 응답
 → 클라이언트
```

## 주의할 점
- Spring MVC 요청 흐름의 중심은 DispatcherServlet이다.
- HandlerMapping은 컨트롤러를 찾는 역할이고, HandlerAdapter는 컨트롤러를 실행하는 역할이다.
- 모든 응답이 ViewResolver를 거치는 것은 아니다. JSON 응답은 보통 HttpMessageConverter를 통해 처리된다.
- Filter는 DispatcherServlet 앞단에서 동작하므로 Spring MVC 내부 구성요소와 구분해서 이해해야 한다.

## 관련 Daily
- [2026-06-28(일) Spring MVC 요청 흐름과 공통 처리 위치 정리](../../daily/2026/2026-06-28(일)%20Spring%20MVC%20요청%20흐름과%20공통%20처리%20위치%20정리.md)
