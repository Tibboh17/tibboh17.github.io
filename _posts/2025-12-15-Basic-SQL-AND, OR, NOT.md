---
title: "Basic SQL: AND, OR, NOT"
categories: [Database, SQL]
tags: [Database, SQL]
order: 3
---

# Description
SQL에서 `AND`, `OR`, `NOT`은 **논리 연산자(Logical Operators)**로, `WHERE` 절과 함께 여러 조건을 조합하여 데이터를 필터링할 때 사용된다.

# Syntax
```SQL
SELECT column1, column2, ...
FROM table_name
WHERE condition1 AND condition2;
```

```SQL
SELECT column1, column2, ...
FROM table_name
WHERE condition1 OR condition2;
```

```SQL
SELECT column1, column2, ...
FROM table_name
WHERE NOT condition;
```

- `AND`: 여러 조건을 모두 만족해야 하는 경우
- `OR`: 하나 이상의 조건을 만족하면 되는 경우
- `NOT`: 조건을 부정하는 경우

# Example
## AND Operator
`reviews` 테이블에서 `product_id`가 50001이고 `stars`가 4 이상인 행을 조회한다.

```SQL
SELECT *
FROM reviews
WHERE product_id = 50001 AND stars >= 4;
```

## OR Operator
`reviews` 테이블에서 `stars` 값이 3이거나 4인 행을 조회한다.

```SQL
SELECT *
FROM reviews
WHERE stars = 3 OR stars = 4;
```

## NOT Operator
`reviews` 테이블에서 `stars` 값이 5가 모든 아닌 모든 행을 조회한다.

```SQL
SELECT *
FROM reviews
WHERE NOT stars = 5;
```

# Referece
- [DataLemur SQL Tutorial](https://datalemur.com/sql-tutorial/sql-and-or-not)