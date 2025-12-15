---
title: "Basic SQL: WHERE"
categories: [Database, SQL]
tags: [Database, SQL]
---

# Description
`WHERE` 절은 `SELECT` 문과 함께 사용되어 특정 조건을 만족하는 행만 필터링하여 조회할 때 쓰이는 **SQL** 절이다. 단순히 테이블 전체를 조회하는 것이 아니라, 조건식으로 원하는 조건을 명시함으로써 조회 결과를 좁히는 데 사용한다.

# Syntax
조건식은 비교 연산자(=, <, >, <=, >=, != 등)를 포함할 수 있다.

```SQL
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```

- `WHERE`: 조건식 작성

# Example
## Basic Example
`reviews` 테이블에서 `stars` 값이 4보다 작은 행만 출력한다. 조건을 만족하는 행만 결과에 포함된다.

```SQL
SELECT *
FROM reviews
WHERE stars < 4;
```

## with Equality
`product_id`가 12580과 일치하는 행만 선택한다. 특정 값과 같은 레코드를 찾을 때 주로 사용된다.

```SQL
SELECT review_id, user_id, stars
FROM reviews
WHERE product_id = 12580;
```

# Referece
- [DataLemur SQL Tutorial](https://datalemur.com/sql-tutorial/sql-where)