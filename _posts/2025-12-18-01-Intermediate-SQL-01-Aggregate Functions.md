---
title: "Intermediate SQL: Aggregate Functions"
slug: intermediate-sql-aggregate-functions
categories: [Database, SQL]
tags: [Database, SQL]
---

# Description

**집계 함수(Aggregate Functions)**는 여러 행의 값을 하나의 결과 값으로 계산할 때 사용된다. 주로 데이터의 요약, 통계 계산, 분석 목적의 쿼리에서 사용되며, `GROUP BY` 절과 함께 자주 활용된다.

# Syntax

대표적인 집계 함수로는 `COUNT`, `SUM`, `AVG`, `MIN`, `MAX` 가 있고 여러 행을 하나의 결과 행으로 반환한다. 또한, `GROUP BY` 와 함께 사용하면 그룹별 집계가 가능하다.

```SQL
SELECT AGGREGATE_FUNCTION(column_name)
FROM table_name;
```

```SQL
SELECT AGGREGATE_FUNCTION(column_name)
FROM table_name
GROUP BY column_name;
```

# Example

## COUNT

`reviews` 테이블의 전체 행 개수를 조회한다. `COUNT(*)`는 NULL 여부와 관계없이 모든 행을 센다.

```SQL
SELECT COUNT(*)
FROM reviews;
```

## SUM

`orders` 테이블에서 모든 주문의 총 금액을 계산한다.

```SQL
SELECT SUM(amount)
FROM orders;
```

## AVG

`reviews` 테이블에서 평균 별점을 계산한다. NULL 값은 평균 계산에서 자동으로 제외된다

```SQL
SELECT AVG(stars)
FROM reviews;
```

## MIN, MAX

`products` 테이블에서 가장 낮은 가격과 가장 높은 가격을 조회한다.

```SQL
SELECT MIN(price), MAX(price)
FROM products;
```

## Aggregate with GROUP BY

`product_id`별 리뷰 개수를 계산한다. `GROUP BY` 절을 사용하면 각 `product_id` 그룹별로 집계 결과가 반환된다.

```SQL
SELECT product_id, COUNT(*) AS review_count
FROM reviews
GROUP BY product_id;
```

# Referece

- [DataLemur SQL Tutorial](https://datalemur.com/sql-tutorial/sql-aggregate-functions)