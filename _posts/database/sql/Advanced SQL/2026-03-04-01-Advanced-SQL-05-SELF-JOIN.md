---
title: "Advanced SQL: SELF-JOIN"
slug: advanced-sql-self-join
categories: [Database, SQL]
tags: [Database, SQL]
date: 2026-03-04 01:00:00 +0900
---

# Description

**Self-Join**은 일반적인 `JOIN`과 동일한 메커니즘을 사용하지만, **하나의 테이블을 자기 자신과 결합**하는 특수한 방식이다. 주로 테이블 내의 행끼리 서로 비교해야 하거나, 직원-매니저 관계와 같은 **계층적 구조(Hierarchical Data)**를 쿼리할 때 필수적으로 사용된다. 자기 자신을 참조하기 때문에 동일한 테이블을 구분하기 위한 **별칭(Alias) 사용이 필수적**이다.

# Syntax

동일한 테이블을 두 번 불러오므로, 각 참조에 서로 다른 별칭(`AS`)을 부여하여 컬럼 이름의 충돌을 방지한다. 같은 테이블 내에서 서로 다른 행을 매칭시키기 위한 조건을 `ON` 절에 명시한다.

```SQL
SELECT t1.column_name, 
       t2.column_name
FROM table_name AS t1
JOIN table_name AS t2 
  ON t1.common_col = t2.common_col;
```

# Example

## Employee-Manager Relationship

`employees` 테이블에서 각 직원의 이름과 그 직원의 매니저 이름을 함께 조회한다. 매니저도 결국 직원 테이블의 한 행이므로 `Self-Join`을 통해 연결한다. `e`는 일반 직원 정보를, `m`은 해당 직원의 매니저 정보를 나타낸다.

```SQL
SELECT e.employee_name AS staff, 
       m.employee_name AS manager
FROM employees AS e
INNER JOIN employees AS m 
  ON e.manager_id = m.employee_id;
```

## Comparing Rows

동일한 테이블 내에서 특정 조건은 같지만 식별자가 다른 행들을 비교하여 중복 데이터나 특정 패턴을 찾는다. 예를 들어, 동일한 `user_id`를 가졌지만 서로 다른 `event_id`를 가진 데이터를 조회할 때 유용하다. `<>` 연산자를 사용하여 자기 자신과 조인되는 것을 방지하고 서로 다른 행을 매칭시킨다.

```SQL
SELECT a.user_id,
       a.event_type AS first_event,
       b.event_type AS second_event
FROM events AS a
JOIN events AS b 
  ON a.user_id = b.user_id
  AND a.event_id <> b.event_id;
```

# Reference

- [DataLemur SQL Tutorial](https://datalemur.com/sql-tutorial/sql-self-join)