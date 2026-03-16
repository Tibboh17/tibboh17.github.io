---
title: "Advanced SQL: UNION, INTERSECT, EXCEPT"
slug: advanced-sql-union-intersect-except
categories: [Database, SQL]
tags: [Database, SQL]
date: 2026-03-12 20:00:00 +0900
---

# Description

`UNION`, `INTERSECT`, `EXCEPT`는 **독립적인 여러 `SELECT` 쿼리 결과를 하나의 결과 셋(Result Set)으로 결합**하는 집합 연산자(Set Operators)다. 공통 키를 기준으로 열을 확장하는 `JOIN`과 달리, 동일한 구조의 데이터를 **행 방향(세로)으로 병합하거나 비교**할 때 사용된다.

- `UNION`: 두 결과를 합치되 **중복된 행은 제거**
- `UNION ALL`: 두 결과를 합치되 **중복을 제거하지 않고 모두 포함**하여 `UNION`보다 상대적으로 연산이 빠름
- `INTERSECT`: 두 결과에 **공통으로 존재하는 교집합 행**만 반환
- `EXCEPT`: 첫 번째 결과에는 있고 두 번째 결과에는 **없는 차집합 행**만 반환

# Syntax

각 `SELECT` 문을 결합하기 위해서는 **컬럼의 개수가 동일**해야 하고, 대응하는 위치의 **데이터 타입이 호환**되어야 하며, **컬럼의 순서**가 같아야 한다. 데이터를 정렬하기 위한 `ORDER BY` 절은 각 하위 쿼리가 아닌 **결합된 최종 결과의 맨 마지막**에 단 한 번만 작성해야 한다.

```SQL
SELECT column1, column2, ...
FROM table_name1

UNION
SELECT column1, column2, ...
FROM table_name2;
```

```SQL
SELECT column1, column2, ...
FROM table_name1

INTERSECT
SELECT column1, column2, ...
FROM table_name2;
```

```SQL
SELECT column1, column2, ...
FROM table_name1

EXCEPT
SELECT column1, column2, ...
FROM table_name2;
```

# Example

## UNION

두 테이블의 결과를 하나로 합칠 때 사용하며, 양쪽 결과에 모두 존재하는 **중복된 행은 하나만 남기고 제거**한다. 예를 들어 두 지점의 전체 고객 명단을 중복 없이 통합하여 조회할 때 유용하다.

```SQL
SELECT ingredient
FROM recipe_1

UNION

SELECT ingredient
FROM recipe_2;
```

## UNION ALL

`UNION`과 동일하게 데이터를 합치지만, **중복된 행을 제거하지 않고 모두 포함**한다. 중복 검사 과정이 생략되므로 데이터베이스의 부하가 적고 속도가 빠르며, 단순한 데이터 전체 트래픽이나 누적 카운트를 조회할 때 효율적이다.

```SQL
SELECT ingredient
FROM recipe_1

UNION ALL

SELECT ingredient
FROM recipe_2;
```

## INTERSECT

두 쿼리 결과에 **공통으로 존재하는 교집합 행**만 반환한다. 예를 들어, 첫 번째 이벤트와 두 번째 이벤트에 모두 참여한 핵심 대상자를 추출하여 분석할 때 활용할 수 있다.

```SQL
SELECT ingredient
FROM recipe_1

INTERSECT

SELECT ingredient
FROM recipe_2;
```

## EXCEPT

첫 번째 쿼리 결과에는 존재하지만, 두 번째 쿼리 결과에는 **존재하지 않는 차집합 행**만 반환한다. 특정 기능을 사용한 유저 중 결제는 하지 않은 유저를 걸러내는 등 A조건은 만족하되 B조건은 피해야 하는 데이터를 찾을 때 적합하다.

```SQL
SELECT ingredient
FROM recipe_1

EXCEPT

SELECT ingredient
FROM recipe_2;
```

# Reference

- [DataLemur SQL Tutorial](https://datalemur.com/sql-tutorial/sql-union-intercept-except)