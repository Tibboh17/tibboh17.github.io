---
title: "Basic SQL: SELECT"
categories: [Database, SQL]
tags: [Database, SQL]
pin: true
---

# Description
`SELECT` 문은 데이터베이스 테이블에서 조회할 컬럼과 데이터를 지정하는 **SQL**의 기본 구문이다. 어떤 데이터를 결과로 반환할지 정의하며, 대부분의 **SQL** 쿼리는 `SELECT` 문을 중심으로 작성된다.

# Syntax
컬럼은 쉼표(,)로 구분하며, 작성한 순서대로 결과가 출력된다.

```SQL
SELECT column1, column2, ...
FROM table_name;
```

- `SELECT`: 조회할 컬럼을 지정
- `FROM`: 데이터를 가져올 테이블을 지정

# Example
## Specific Columns
`reviews` 테이블에서 `review_id`, `submit_date`, `stars` 컬럼만 선택하여 조회한다. 결과는 세 컬럼만 포함한 테이블 형태로 반환된다.

```SQL
SELECT review_id, submit_date, stars
FROM reviews;
```

## All Columns
`*` 는 테이블에 존재하는 모든 컬럼을 의미한다. 테이블 구조를 빠르게 확인할 때 유용하다.

```SQL
SELECT *
FROM reviews;
```

# Referece
- [DataLemur SQL Tutorial](https://datalemur.com/sql-tutorial/sql-select)