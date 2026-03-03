---
title: "Intermediate SQL: Mathematical Functions"
slug: intermediate-sql-mathematical-functions
categories: [Database, SQL]
tags: [Database, SQL]
---

# Description

SQL의 **수학 함수(Mathematical Functions)**는 숫자 데이터를 대상으로 계산, 반올림, 절댓값, 거듭제곱 등 다양한 수학 연산을 수행할 때 사용된다. 산술 연산자와 달리, 함수 형태로 복잡한 계산을 표현할 수 있어 데이터 분석 및 가공에 자주 활용된다. 데이터베이스마다 지원 함수는 조금씩 다르지만, 기본적인 수학 함수는 대부분 공통적으로 제공된다.

# Syntax

함수(`ABS`, `ROUND`, `CEILING`, `FLOOR`, `POWER` 등)는 컬럼 값뿐 아니라 계산식에도 적용 가능하며 결과는 새로운 컬럼으로 반환된다.

```SQL
SELECT FUNCTION_NAME(column_name)
FROM table_name;
```

```SQL
SELECT FUNCTION_NAME(expression)
FROM table_name;
```

# Example

## ABS (Absolute Value)

값의 절댓값을 반환한다.

```SQL
SELECT ABS(-10) AS absolute_value;
```

## ROUND

숫자를 지정한 자리에서 반올림한다. 두 번째 인자는 소수점 자리 수를 의미한다.

```SQL
SELECT ROUND(123.456, 2) AS rounded_value;
```

## CEILING / FLOOR

숫자를 올림하거나 내림한다.

```SQL
SELECT CEILING(4.2) AS ceil_value,
       FLOOR(4.8) AS floor_value;
```

## POWER

거듭제곱 값을 계산한다.

```SQL
SELECT POWER(2, 3) AS power_value;
```

- `POWER(2, 3)` → 2³ = 8

## Mathematical Function with Column

`orders` 테이블에서 주문 금액을 반올림하여 조회한다.

```SQL
SELECT order_id,
       ROUND(amount) AS rounded_amount
FROM orders;
```

# Reference
- [DataLemur SQL Tutorial](https://datalemur.com/sql-tutorial/sql-tutorial-mathematical-functions)