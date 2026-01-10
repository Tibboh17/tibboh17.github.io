---
title: "Intermediate SQL: Division"
slug: intermediate-sql-division
categories: [Database, SQL]
tags: [Database, SQL]
---

# Description

SQL에서 **나눗셈(Division)**은 산술 연산자 `/` 를 사용하여 두 값의 비율이나 평균, 단가 등을 계산할 때 사용된다. 정수형 컬럼끼리 나눗셈을 수행할 경우 소수점이 버려질 수 있으므로, 데이터 타입에 주의해야 한다.

# Syntax

피연산자 중 하나라도 실수형이면 결과는 실수형으로 반환된다. 정수 ÷ 정수 연산은 DBMS에 따라 정수 결과가 반환될 수 있다

```SQL
SELECT column1 / column2
FROM table_name;
```

```SQL
SELECT column1 / value
FROM table_name;
```

# Example

## Basic Division

`employees` 테이블에서 연봉을 12로 나누어 월급을 계산한다.

~~~SQL
SELECT employee_id,
       salary / 12 AS monthly_salary
FROM employees;
~~~

## Integer Division Issue

정수형 컬럼끼리 나눗셈을 수행하면 소수점이 제거될 수 있다.

```SQL
SELECT 5 / 2 AS result;
```

- 결과: `2` (DBMS에 따라 다를 수 있음)

## Force Decimal Division

정확한 소수 결과를 얻기 위해 실수형으로 변환한다.

```SQL
SELECT 5.0 / 2 AS result;
```

```SQL
SELECT CAST(5 AS DECIMAL) / 2 AS result;
```

- 결과: `2.5`

## Division with Column

`orders` 테이블에서 주문 총액을 수량으로 나누어 평균 단가를 계산한다.

```SQL
SELECT order_id,
       total_amount / quantity AS unit_price
FROM orders;
```

# Reference
- [DataLemur SQL Tutorial](https://datalemur.com/sql-tutorial/sql-division)