---
title: "Intermediate SQL: DISTINCT"
slug: intermediate-sql-distinct
categories: [Database, SQL]
tags: [Database, SQL]
---

# Description

`DISTINCT`는 `SELECT` 결과에서 중복된 값(행)을 제거하고 유일한 값만 반환할 때 사용한다. 단일 컬럼뿐 아니라 여러 컬럼 조합 기준으로 중복 제거도 가능하다.

# Syntax

`DISTINCT`는 `SELECT` 바로 뒤에 위치해야 하고 여러 컬럼을 지정하면 컬럼 조합 전체가 동일한 행을 중복으로 판단한다.

```SQL
SELECT DISTINCT column_name
FROM table_name;
```

```SQL
SELECT DISTINCT column1, column2, ...
FROM table_name;
```

# Example

## DISTINCT on Single Column

`reviews` 테이블에서 중복되지 않는 별점 값만 조회한다.

```SQL
SELECT DISTINCT stars
FROM reviews;
```

## DISTINCT on Multiple Columns

`reviews` 테이블에서 `product_id`와 `stars` 조합 기준으로 중복을 제거한다.

```SQL
SELECT DISTINCT product_id, stars
FROM reviews;
```

## DISTINCT with COUNT

`reviews` 테이블에서 중복을 제거한 사용자 수를 계산한다.

```SQL
SELECT COUNT(DISTINCT user_id) AS user_count
FROM reviews;
```

# Reference

- [DataLemur SQL Tutorial](https://datalemur.com/sql-tutorial/sql-distinct)