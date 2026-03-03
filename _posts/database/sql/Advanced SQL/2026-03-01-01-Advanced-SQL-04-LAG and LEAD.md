---
title: "Advanced SQL: LAG and LEAD"
slug: advanced-sql-lag-and-lead
categories: [Database, SQL]
tags: [Database, SQL]
---

# Description

`LAG()`와 `LEAD()`는 윈도우 함수로, 현재 행을 기준으로 이전 값과 다음 값을 가져올 때 사용한다. 행을 줄이지 않고 원본을 유지한 채 비교 값을 붙여서 볼 수 있어 시계열 분석에 자주 쓰인다.

`LAG()`는 이전 행 값을, `LEAD()`는 다음 행 값을 반환한다. 필요하면 몇 행 전후를 볼지(`offset`)와 값이 없을 때 대체할 값(`default`)도 지정할 수 있다.

# Syntax

`OVER()` 안에서 계산 기준을 정한다. `ORDER BY`는 이전/다음의 기준 순서를 만들고, `PARTITION BY`를 쓰면 그룹별로 나눠 계산한다.

```SQL
SELECT column_name,
       LAG(target_column, offset, default_value)
           OVER (PARTITION BY group_column ORDER BY order_column) AS prev_value,
       LEAD(target_column, offset, default_value)
           OVER (PARTITION BY group_column ORDER BY order_column) AS next_value
FROM table_name;
```

# Example

## LAG: Previous Value

주문 날짜 기준으로 이전 주문 금액을 함께 조회한다.

```SQL
SELECT order_date,
       amount,
       LAG(amount) OVER (ORDER BY order_date) AS prev_amount
FROM orders;
```

## LEAD: Next Value

주문 날짜 기준으로 다음 주문 금액을 함께 조회한다.

```SQL
SELECT order_date,
       amount,
       LEAD(amount) OVER (ORDER BY order_date) AS next_amount
FROM orders;
```

## Difference from Previous Row

현재 금액과 이전 금액의 차이를 계산한다.

```SQL
SELECT order_date,
       amount,
       amount - LAG(amount) OVER (ORDER BY order_date) AS diff_from_prev
FROM orders;
```

## Grouped LAG and LEAD

고객별 주문 흐름에서 이전/다음 주문 금액을 조회한다.

```SQL
SELECT customer_id,
       order_date,
       amount,
       LAG(amount)  OVER (PARTITION BY customer_id ORDER BY order_date) AS prev_amount,
       LEAD(amount) OVER (PARTITION BY customer_id ORDER BY order_date) AS next_amount
FROM orders;
```

# Reference
- [DataLemur SQL Tutorial](https://datalemur.com/sql-tutorial/sql-time-series-window-function-lead-lag)
