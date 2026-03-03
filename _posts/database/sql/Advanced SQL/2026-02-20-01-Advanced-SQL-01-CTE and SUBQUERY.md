---
title: "Adavnced SQL: CTE and SUBQUERY"
slug: advanced-sql-cte-subquery
categories: [Database, SQL]
tags: [Database, SQL]
---

# Description

`SUBQUERY`는 **하나의 SQL 쿼리 안에 포함된 또 다른 쿼리**를 의미한다. 메인 쿼리가 실행되기 전에 먼저 실행되며, 그 결과를 기반으로 조건 비교나 데이터 조회를 수행한다.

`CTE`(Common Table Expression)는 `WITH` 키워드를 사용하여 **임시 결과 집합을 정의한 뒤**, 이를 메인 쿼리에서 참조하는 방식이다. 복잡한 쿼리를 구조적으로 나누어 가독성과 유지보수성을 높일 수 있다.

# Syntax

## SUBQUERY

괄호 안에 `SUBQUERY`를 작성하며 `WHERE`, `FROM`, `SELECT` 절 등 다양한 위치에서 사용 가능하다.

```SQL
SELECT column_name
FROM table_name
WHERE column_name IN (
    SELECT column_name
    FROM table_name
);
```

## CTE

`WITH`을 사용하요 `CTE` 작성을 시작하고 `cte_name`란에 해당 임시 결과 집합의 이름을 지정합니다. `CTE`를 통해 얻은 결과는 메인 쿼리에서 일반 테이블처럼 참조 가능하다.

```SQL
WITH cte_name AS (
    SELECT column_name
    FROM table_name
)
SELECT *
FROM cte_name;
```

# Example

## Subquery in WHERE
평균 주문 금액보다 큰 주문만 조회한다.

```SQL
SELECT order_id, amount
FROM orders
WHERE amount > (
    SELECT AVG(amount)
    FROM orders
);
```

## Subquery in FROM
상품별 평균 가격을 계산한 뒤 조회한다.

```SQL
SELECT avg_price
FROM (
    SELECT AVG(price) AS avg_price
    FROM products
) AS sub;
```

## CTE Example
고객별 총 주문 금액을 먼저 계산한 뒤, 1000 이상인 고객만 조회한다.

```SQL
WITH customer_totals AS (
    SELECT customer_id, SUM(amount) AS total_amount
    FROM orders
    GROUP BY customer_id
)
SELECT *
FROM customer_totals
WHERE total_amount >= 1000;
```

# Reference
- [DataLemur SQL Tutorial](https://datalemur.com/sql-tutorial/sql-cte-subquery)