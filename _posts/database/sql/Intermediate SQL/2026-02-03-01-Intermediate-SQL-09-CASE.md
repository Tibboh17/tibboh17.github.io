---
title: "Instermediate SQL: CASE"
slug: intermediate-sql-case
categories: [Database, SQL]
tags: [Database, SQL]
---

# Description

`CASE` 문은 SQL에서 **조건에 따라 서로 다른 값을 반환**할 때 사용하는 조건문이다. 프로그래밍 언어의 `if-else` 문과 유사하며, 데이터 값을 분류하거나 새로운 파생 컬럼을 만들 때 자주 사용된다. `CASE` 문은 `SELECT`, `WHERE`, `ORDER BY` 등 다양한 절에서 사용할 수 있다.

# Syntax

`CASE` 문은 조건을 순서대로 평가한 뒤, **가장 먼저 참이 되는 조건의 결과를 반환**한다. 모든 조건이 거짓일 경우 `ELSE` 값이 반환되며, `ELSE` 가 없으면 결과는 `NULL` 이 된다.

```SQL
CASE
    WHEN condition1 THEN result1
    WHEN condition2 THEN result2
    ELSE result
END
```

# Example

## Basic CASE

`reviews` 테이블에서 별점(`stars`)에 따라 리뷰 등급을 분류한다.

```SQL
SELECT 
    review_id,
    stars,
    CASE
        WHEN stars >= 4 THEN 'Good'
        WHEN stars >= 2 THEN 'Average'
        ELSE 'Bad'
    END AS review_rating
FROM reviews;
```

## CASE with Numeric Result

주문 금액에 따라 할인율을 계산한다.

```SQL
SELECT 
    order_id,
    amount,
    CASE
        WHEN amount >= 100 THEN amount * 0.9
        WHEN amount >= 50  THEN amount * 0.95
        ELSE amount
    END AS discounted_amount
FROM orders;
```

## CASE in ORDER BY

별점이 높은 리뷰를 먼저 정렬한다.

```SQL
SELECT review_id, stars
FROM reviews
ORDER BY
    CASE
        WHEN stars = 5 THEN 1
        WHEN stars = 4 THEN 2
        ELSE 3
    END;
```

# Reference

- [DataLemur SQL Tutorial](https://datalemur.com/sql-tutorial/sql-case-statement)