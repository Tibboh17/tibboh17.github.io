---
title: "Basic SQL: BETWEEN"
slug: basic-sql-between
categories: [Database, SQL]
tags: [Database, SQL]
---

# Description
`BETWEEN` 연산자는 `WHERE` 절과 함께 사용되어 특정 범위 내에 포함되는 값을 가진 행만 조회할 때 사용된다. 숫자, 날짜와 같은 값에 사용할 수 있으며, 시작 값과 끝 값을 모두 포함하는 범위 조건을 의미한다.

# Syntax
시작 값과 끝 값은 모두 결과에 포함된다.

```SQL
SELECT column1, column2, ...
FROM table_name
WHERE column_name BETWEEN value1 AND value2;

```
- `BETWEEN`: 범위 조건을 지정하는 연산자
- `value1`: 범위의 시작 값
- `value2`: 범위의 끝 값

# Example
## Numeric Range
`orders` 테이블에서 `amount` 값이 100 이상 500 이하인 모든 주문을 조회한다.

```SQL
SELECT *
FROM orders
WHERE amount BETWEEN 100 AND 500;
```

## Date Range
`reviews` 테이블에서 `submit_date`가 2025-01-01부터 2025-06-30까지인 리뷰를 조회한다.

```SQL
SELECT review_id, user_id, stars, submit_date
FROM reviews
WHERE submit_date BETWEEN '2025-01-01' AND '2025-06-30';
```

# Referece
- [DataLemur SQL Tutorial](https://datalemur.com/sql-tutorial/sql-between)