# SQL 조인(Join)의 종류와 이해

조인(Join)은 두 개 이상의 테이블을 연결하여 데이터를 검색하는 방법입니다. 관계형 데이터베이스(RDB)의 핵심 기능 중 하나입니다.

---

## 1. 조인의 종류 한눈에 보기

### 1) INNER JOIN (내부 조인)
* **정의**: 두 테이블에서 조인 조건이 **모두 일치하는 행**만 결합하여 반환합니다.
* **특징**: 교집합과 같습니다. 한쪽에만 존재하는 데이터는 결과에서 제외됩니다.
* **SQL 예시**:
  ```sql
  SELECT *
  FROM Users U
  INNER JOIN Orders O ON U.id = O.user_id;
  ```

### 2) LEFT (OUTER) JOIN (왼쪽 외부 조인)
* **정의**: **왼쪽 테이블의 모든 행**을 가져오고, 오른쪽 테이블에서 조인 조건이 일치하는 행을 결합합니다.
* **특징**: 오른쪽 테이블에 매칭되는 데이터가 없으면 오른쪽 테이블의 컬럼들은 `NULL`로 표시됩니다.
* **SQL 예시**:
  ```sql
  SELECT *
  FROM Users U
  LEFT JOIN Orders O ON U.id = O.user_id;
  ```

### 3) RIGHT (OUTER) JOIN (오른쪽 외부 조인)
* **정의**: **오른쪽 테이블의 모든 행**을 가져오고, 왼쪽 테이블에서 조인 조건이 일치하는 행을 결합합니다.
* **특징**: LEFT JOIN과 방향만 반대입니다. 왼쪽 테이블에 매칭되는 데이터가 없으면 `NULL`로 표시됩니다.
* **SQL 예시**:
  ```sql
  SELECT *
  FROM Users U
  RIGHT JOIN Orders O ON U.id = O.user_id;
  ```

### 4) FULL (OUTER) JOIN (전체 외부 조인)
* **정의**: 양쪽 테이블에서 **조건이 일치하는 행뿐만 아니라, 일치하지 않는 행까지 모두** 포함하여 반환합니다.
* **특징**: 합집합과 같습니다. 서로 매칭되지 않는 부분은 모두 `NULL`로 채워집니다.
* **참고**: MySQL은 `FULL OUTER JOIN` 문법을 직접 지원하지 않으므로, `LEFT JOIN`과 `RIGHT JOIN`을 `UNION`으로 합쳐서 구현해야 합니다.
* **SQL 예시 (Oracle/PostgreSQL)**:
  ```sql
  SELECT *
  FROM Users U
  FULL OUTER JOIN Orders O ON U.id = O.user_id;
  ```

### 5) CROSS JOIN (교차 조인 / 카테시안 곱)
* **정의**: 두 테이블의 **모든 가능한 조합(Cartesian Product)**을 반환합니다.
* **특징**: 조인 조건이 필요 없으며, 결과 행의 수는 `A 테이블 행 수 × B 테이블 행 수`가 됩니다. 대용량 테이블 간의 CROSS JOIN은 성능에 치명적일 수 있습니다.
* **SQL 예시**:
  ```sql
  SELECT *
  FROM Products
  CROSS JOIN Colors;
  ```

### 6) SELF JOIN (자체 조인)
* **정의**: **동일한 하나의 테이블**을 자기 자신과 조인하는 형태입니다.
* **특징**: 조직도(사원-관리자 관계), 카테고리 계층 구조(상위 카테고리-하위 카테고리) 등을 조회할 때 사용합니다. 반드시 테이블에 서로 다른 별칭(Alias)을 지정해야 합니다.
* **SQL 예시**:
  ```sql
  SELECT E.name AS 사원명, M.name AS 관리자명
  FROM Employee E
  INNER JOIN Employee M ON E.manager_id = M.id;
  ```

---

## 2. 벤 다이어그램으로 이해하는 조인

```
       [Users]                 [Orders]
    ┌───────────┐           ┌───────────┐
    │  Only A   │ ┌───────┐ │  Only B   │
    │  (LEFT    │ │ INNER │ │  (RIGHT   │
    │   OUTER)  │ │ JOIN  │ │   OUTER)  │
    └───────────┘ └───────┘ └───────────┘
    └───────────────────────────────────┘
                FULL OUTER JOIN
```

---

## ✍️ 요약 노트 (노션 복사용)

1. **INNER JOIN**: 교집합 (공통된 것만)
2. **LEFT JOIN**: 왼쪽 테이블 기준 (오른쪽 없으면 NULL)
3. **RIGHT JOIN**: 오른쪽 테이블 기준 (왼쪽 없으면 NULL)
4. **FULL JOIN**: 합집합 (양쪽 다 가져옴, 없으면 NULL)
5. **CROSS JOIN**: 곱집합 (모든 조합)
6. **SELF JOIN**: 한 테이블 내의 관계 매핑 (동일 테이블 조인)
