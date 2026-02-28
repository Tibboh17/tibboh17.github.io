---
title: "Advanced SQL: Ranking"
slug: advanced-sql-ranking
categories: [Database, SQL]
tags: [Database, SQL]
---

# Description
`RANK`, `DENSE_RANK`, `ROW_NUMBER`는 윈도우 함수로, 정렬 기준에 따라 각 행의 순위를 매길 때 사용한다.
세 함수의 핵심 차이는 동점 처리 방식이다.

- `ROW_NUMBER()`: 중복 없이 고유한 순번 부여
- `RANK()`: 동점이면 같은 순위, 다음 순위는 건너뜀
- `DENSE_RANK()`: 동점이면 같은 순위, 다음 순위는 건너뛰지 않음

# Syntax

순위 함수는 `OVER()` 안에서 계산 기준을 정한다. `ORDER BY`는 순위를 매길 기준 컬럼이고, `PARTITION BY`를 추가하면 그룹별로 순위를 따로 계산할 수 있다.

```SQL
SELECT column_name,
       ROW_NUMBER() OVER (ORDER BY column_name) AS row_num,
       RANK()       OVER (ORDER BY column_name) AS rank_num,
       DENSE_RANK() OVER (ORDER BY column_name) AS dense_rank_num
FROM table_name;
```

# Example

## ROW_NUMBER

매출 금액 기준으로 고유 번호를 부여한다.

```SQL
SELECT order_id,
       amount,
       ROW_NUMBER() OVER (ORDER BY amount DESC) AS row_num
FROM orders;
```

## RANK

매출 금액 기준으로 순위를 부여한다.

```SQL
SELECT order_id,
       amount,
       RANK() OVER (ORDER BY amount DESC) AS rank_num
FROM orders;
```

## DENSE_RANK

매출 금액 기준으로 순위를 부여한다.

```SQL
SELECT order_id,
       amount,
       DENSE_RANK() OVER (ORDER BY amount DESC) AS dense_rank_num
FROM orders;
```

## Partitioned Ranking

부서별 급여 순위를 계산한다.

```SQL
SELECT employee_id,
       department,
       salary,
       RANK() OVER (
           PARTITION BY department
           ORDER BY salary DESC
       ) AS dept_rank
FROM employees;
```

# Reference
- [DataLemur SQL Tutorial](https://datalemur.com/sql-tutorial/sql-rank-dense_rank-row_number-window-function)
