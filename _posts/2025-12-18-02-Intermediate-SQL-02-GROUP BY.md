---
title: "Intermediate SQL: GROUP BY"
slug: intermediate-sql-group-by
categories: [Database, SQL]
tags: [Database, SQL]
---

# Description

`GROUP BY` 절은 같은 값을 가진 행들을 하나의 그룹으로 묶어 **집계 함수(Aggregate Functions)**를 적용할 때 사용된다. 단일 행 단위가 아니라 그룹 단위의 요약 결과를 얻고자 할 때 필수적으로 사용된다.

# Syntax

`SELECT` 절에 포함된 집계 함수가 아닌 컬럼은 반드시 `GROUP BY`에 포함되어야 하고 하나 이상의 컬럼으로 그룹화할 수도 있다

```SQL
SELECT column_name, AGGREGATE_FUNCTION(column_name)
FROM table_name
GROUP BY column_name;
```

# Example

## Basic GROUP BY

`reviews` 테이블에서 `product_id`별 리뷰 개수를 계산한다.

```SQL
SELECT product_id, COUNT(*) AS review_count
FROM reviews
GROUP BY product_id;
```

## GROUP BY with Multiple Columns

`reviews` 테이블에서 `product_id`와 `stars`별 리뷰 개수를 계산한다.

```SQL
SELECT product_id, stars, COUNT(*) AS review_count
FROM reviews
GROUP BY product_id, stars;
```

## GROUP BY with Aggregate Function

`orders` 테이블에서 고객별 총 주문 금액을 계산한다.

```SQL
SELECT customer_id, SUM(amount) AS total_amount
FROM orders
GROUP BY customer_id;
```

# Referece

- [DataLemur SQL Tutorial](https://datalemur.com/sql-tutorial/sql-group-by)