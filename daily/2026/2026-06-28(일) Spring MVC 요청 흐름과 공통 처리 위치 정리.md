# 📅 2026-06-28(일) Spring MVC 요청 흐름과 공통 처리 위치 정리

## 🎯 목표
- Filter, Interceptor, AOP의 동작 위치와 차이 이해
- Spring MVC 요청 흐름을 필기 시험 답안으로 쓸 수 있게 정리

## ✅ 완료
- Filter는 서블릿 컨테이너 영역에서 동작하며, Spring MVC에 요청이 들어가기 전과 응답이 나가기 전에 요청/응답을 처리한다는 점 정리
- Interceptor는 Spring MVC 내부에서 동작하며, 컨트롤러 실행 전후의 흐름을 가로채 공통 로직을 처리한다는 점 정리
- AOP는 Spring Bean의 메서드 실행 전후에 공통 기능을 적용하는 방식이라는 점 정리
- Spring MVC 요청 흐름을 `요청 → Filter → DispatcherServlet → HandlerMapping → HandlerAdapter → Controller → Service → Repository → 응답` 순서로 정리
- 화면 응답은 ViewResolver/View를 거치고, JSON 응답은 HttpMessageConverter를 거친다는 차이 정리

## ⏱️ 공부 시간
16:00 ~ 18:00 (총 2시간)

## ✍️ 회고
면접 준비하면서 알고 있는 개념들을 정리하는데, 이렇게 공부할 것이 많은지 다시 느꼈다.
CS가 항상 기본이라는 걸 잊지 말고, 꼭 이직을 해서라도 CS 공부는 무조건 꾸준히 하자. 제발.

## 🔗 관련 Concepts
- [Filter Interceptor AOP 차이](../../concepts/spring/Filter%20Interceptor%20AOP%20차이.md)
- [Spring MVC 요청 흐름](../../concepts/spring/Spring%20MVC%20요청%20흐름.md)
