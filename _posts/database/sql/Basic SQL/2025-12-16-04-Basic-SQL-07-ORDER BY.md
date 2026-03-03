---
title: "Basic SQL: ORDER BY"
slug: basic-sql-order-by
categories: [Database, SQL]
tags: [Database, SQL]
---

# Description
`ORDER BY` 절은 `SELECT` 문과 함께 사용되어 조회 결과를 특정 컬럼 기준으로 정렬할 때 사용된다. **SQL**의 기본 동작은 결과에 고정된 정렬 순서가 보장되지 않기 때문에, 원하는 순서로 결과를 출력하려면 `ORDER BY`를 명시해야 한다.

# Syntax
정렬은 오름차순(ASC), 내림차순(DESC) 으로 지정할 수 있으며 하나 이상의 컬럼을 기준으로 다단계 정렬도 가능하다.

```SQL
SELECT column1, column2, ...
FROM table_name
ORDER BY column1 [ASC | DESC], column2 [ASC | DESC], ...;
```
- `ORDER BY`: 정렬 기준을 지정하는 절
- `column1, column2, ...`: 정렬하려는 컬럼 목록
- `ASC`: 오름차순 정렬 (기본값)
- `DESC`: 내림차순 정렬

# Example
## Sort by One Column (Ascending)
`products` 테이블에서 모든 상품을 `price` 오름차순으로 정렬하여 조회한다.

```SQL
SELECT product_id, product_name, price
FROM products
ORDER BY price ASC;
```

## Sort by One Column (Descending)
`products` 테이블에서 상품을 `units_sold` 기준 내림차순으로 정렬한다.

```SQL
SELECT product_id, product_name, units_sold
FROM products
ORDER BY units_sold DESC;
```

## Sort by Multiple Columns
`employees` 테이블에서 먼저 `department` 오름차순, 같은 부서 내에서는 `salary` 내림차순으로 정렬한다.

```SQL
SELECT employee_id, department, salary
FROM employees
ORDER BY department ASC, salary DESC;
```

# Referece
- [DataLemur SQL Tutorial](https://datalemur.com/sql-tutorial/sql-order-by)