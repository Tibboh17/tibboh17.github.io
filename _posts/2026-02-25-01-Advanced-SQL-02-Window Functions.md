---
title: "Advanced SQL: Window Functions"
slug: advanced-sql-window-functions
categories: [Database, SQL]
tags: [Database, SQL]
---

# Description

**Window Function**은 행을 그룹으로 묶지 않고도, **현재 행을 유지한 채로 집계 계산을 수행**할 수 있는 기능이다. 일반적인 집계 함수(`GROUP BY`)는 여러 행을 하나의 결과 행으로 줄이지만, 윈도우 함수는 각 행마다 집계 결과를 함께 보여준다. 대표적으로 `SUM()`, `AVG()`, `COUNT()`, `MIN()`, `MAX()`등을 `OVER()` 절과 함께 사용한다.

# Syntax

윈도우 함수는 `OVER()` 안에 계산 기준을 적어 사용한다. `PARTITION BY`는 데이터를 그룹으로 나누고, `ORDER BY`는 그룹 안에서 계산 순서를 정한다. `GROUP BY`와 달리 원본 행을 줄이지 않고, 계산 결과를 각 행에 함께 보여준다는 점이 핵심이다.


```SQL
SELECT column_name,
       AGGREGATE_FUNCTION(column_name) OVER (
           PARTITION BY column_name
           ORDER BY column_name
       )
FROM table_name;
```

# Example

## Running Total

주문 날짜 기준으로 누적 매출을 계산한다.

```SQL
SELECT order_date,
       amount,
       SUM(amount) OVER (ORDER BY order_date) AS running_total
FROM orders;
```

## Partitioned Aggregate

고객별 총 주문 금액을 각 행에 함께 표시한다.

```SQL
SELECT customer_id,
       order_id,
       amount,
       SUM(amount) OVER (PARTITION BY customer_id) AS customer_total
FROM orders;
```

## Average by Group

부서별 평균 급여를 각 직원 행에 함께 표시한다.

```SQL
SELECT employee_id,
       department,
       salary,
       AVG(salary) OVER (PARTITION BY department) AS dept_avg_salary
FROM employees;
```

# Reference
- [DataLemur SQL Tutorial](https://datalemur.com/sql-tutorial/sql-aggregate-window-functions)
