---
title: "Instermediate SQL: NULL"
slug: intermediate-sql-null
categories: [Database, SQL]
tags: [Database, SQL]
---

# Description

`NULL` 은 SQL에서 **값이 없거나 알 수 없는 상태**를 의미한다. 숫자 0, 빈 문자열(`''`)과는 전혀 다른 개념이며, 아직 값이 저장되지 않았거나 정의되지 않은 상태를 나타낸다. `NULL` 값은 일반적인 비교 연산자(`=`, `!=`, `<`, `>`)로 비교할 수 없으며, 전용 연산자인 `IS NULL`, `IS NOT NULL` 을 사용해야 한다.

# Syntax

`IS NULL`은 컬럼 값이 NULL 인 행을 선택하고 `IS NOT NULL`은 컬럼 값이 NULL 이 아닌 행을 선택한다.

```SQL
SELECT column1, column2
FROM table_name
WHERE column_name IS NULL;
```

```SQL
SELECT column1, column2
FROM table_name
WHERE column_name IS NOT NULL;
```

# Example

## IS NULL
`users` 테이블에서 전화번호가 등록되지 않은 사용자만 조회한다.

```SQL
SELECT user_id, phone_number
FROM users
WHERE phone_number IS NULL;
```

## IS NOT NULL
`users` 테이블에서 이메일이 존재하는 사용자만 조회한다.

```SQL
SELECT user_id, email
FROM users
WHERE email IS NOT NULL;
```

## NULL Comparison Pitfall

다음 쿼리는 의도한 결과를 반환하지 않는다. `NULL` 은 값이 아니기 때문에 `=` 비교가 불가능하다. 따라서, 반드시 `IS NULL` 을 사용해야 한다.

```SQL
SELECT *
FROM users
WHERE phone_number = NULL;
```

## NULL with Aggregate Functions

집계 함수는 기본적으로 `NULL` 값을 자동으로 제외한다.

```SQL
SELECT AVG(stars)
FROM reviews;
```

# Reference

- [DataLemur SQL Tutorial](https://datalemur.com/sql-tutorial/sql-null)