---
title: "Advanced SQL: Query Order of Execution"
slug: advanced-sql-query-order-of-execution
categories: [Database, SQL]
tags: [Database, SQL]
date: 2026-03-24 20:00:00 +0900
---

# Description

SQL 쿼리는 작성한 순서대로 실행되지 않고, **DBMS가 정해진 논리적 실행 순서**에 따라 처리된다. 이 실행 순서를 이해하면 `WHERE`, `GROUP BY`, `HAVING`, `SELECT`, `ORDER BY` 가 **언제 적용되는지** 명확히 알 수 있어, 더 정확한 쿼리를 작성할 수 있다.

# Syntax

SQL은 보통 다음 순서로 처리된다.  
`FROM` → `WHERE` → `GROUP BY` → `HAVING` → `SELECT` → `ORDER BY` → `LIMIT/OFFSET` 순으로 실행된다.

```SQL
SELECT column_name, AGGREGATE_FUNCTION(column_name)
FROM table_name
WHERE condition
GROUP BY column_name
HAVING condition
ORDER BY column_name
LIMIT n;
```

# Example

## Basic Execution Order
아래 쿼리는 상품별 평균 가격이 100 이상인 상품군을 조회하고, 평균 가격이 높은 순으로 정렬한 뒤 상위 5개만 반환한다.

```SQL
SELECT category, AVG(price) AS avg_price
FROM products
WHERE price > 0
GROUP BY category
HAVING AVG(price) >= 100
ORDER BY avg_price DESC
LIMIT 5;
```

이 쿼리는 다음 순서로 처리된다.

1. `FROM` : `products` 테이블에서 데이터를 가져온다  
2. `WHERE` : `price > 0` 조건에 맞는 행만 남긴다  
3. `GROUP BY` : `category` 기준으로 그룹화한다  
4. `HAVING` : 평균 가격이 100 이상인 그룹만 남긴다  
5. `SELECT` : 최종적으로 `category` 와 `AVG(price)` 를 선택한다  
6. `ORDER BY` : 평균 가격 기준으로 내림차순 정렬한다  
7. `LIMIT` : 상위 5개 행만 반환한다

# Reference

- [DataLemur SQL Tutorial](https://datalemur.com/sql-tutorial/query-order-of-execution)