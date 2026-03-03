---
title: "Intermediate SQL: HAVING"
slug: intermediate-sql-having
categories: [Database, SQL]
tags: [Database, SQL]
---

# Description

`HAVING` 절은 `GROUP BY`로 그룹화된 결과에 조건을 적용할 때 사용된다. `WHERE` 절이 개별 행을 필터링하는 반면, HAVING은 집계 결과를 필터링한다는 점에서 차이가 있다. 집계 함수(`COUNT`, `SUM`, `AVG` 등)를 조건으로 사용할 때는 반드시 `HAVING` 절을 사용해야 한다.

# Syntax

집계 함수가 포함된 조건은 `WHERE`가 아닌 `HAVING`에 작성해야 한다. `HAVING` 절은 `GROUP BY` 절 뒤에 위치한다.

```SQL
SELECT column_name, AGGREGATE_FUNCTION(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

# Example

## Basic HAVING

`reviews` 테이블에서 리뷰 개수가 10개 이상인 `product_id`만 조회한다.

```SQL
SELECT product_id, COUNT(*) AS review_count
FROM reviews
GROUP BY product_id
HAVING COUNT(*) >= 10;
```

## HAVING vs WHERE

별점이 4점 이상인 리뷰 중에서, 리뷰 개수가 5개 이상인 상품을 조회한다.

```SQL
SELECT product_id, COUNT(*) AS review_count
FROM reviews
WHERE stars >= 4
GROUP BY product_id
HAVING COUNT(*) >= 5;
```

# Reference

- [DataLemur SQL Tutorial](https://datalemur.com/sql-tutorial/sql-having)