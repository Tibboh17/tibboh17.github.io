---
title: "Instermediate SQL: Date Functions"
slug: intermediate-sql-date-functions
categories: [Database, SQL]
tags: [Database, SQL]
---

# Description

SQL의 **날짜 및 시간 함수(Date & Time Functions)**는 날짜와 시간 데이터를 생성, 추출, 계산, 변환할 때 사용되며, **시간 기반 데이터 처리**에 필수적인 기능이다. 데이터베이스마다 함수 이름이나 동작이 약간씩 다를 수 있지만, 기본적인 개념과 사용 방식은 공통적이다.

# Syntax

날짜 및 시간 함수는 `CURRENT_DATE`, `CURRENT_TIMESTAMP`, `EXTRACT`, `DATE_TRUNC` 등과 같이 날짜 및 시간 데이터를 처리하기 위한 함수들로 구성된다. 이러한 함수는 날짜 컬럼뿐 아니라 날짜 표현식에도 적용할 수 있으며, 사용 목적에 따라 날짜, 시간 또는 숫자 형태의 결과를 반환한다.


```SQL
SELECT DATE_FUNCTION(column_name)
FROM table_name;
```

```SQL
SELECT DATE_FUNCTION(expression)
FROM table_name;
```

# Example

## CURRENT_DATE / CURRENT_TIMESTAMP

현재 날짜 또는 현재 날짜와 시간을 반환한다.

```SQL
SELECT 
    CURRENT_DATE AS today,
    CURRENT_TIMESTAMP AS now;
```

## EXTRACT

날짜 또는 시간 값에서 특정 단위(연, 월, 일 등)를 추출한다.

```SQL
SELECT 
    EXTRACT(YEAR FROM order_date)  AS order_year,
    EXTRACT(MONTH FROM order_date) AS order_month
FROM orders;
```

## DATE_TRUNC

날짜를 지정한 단위 기준으로 잘라낸다.

```SQL
SELECT DATE_TRUNC('month', order_date) AS order_month
FROM orders;
```

## Date Filtering

특정 날짜 이후의 데이터만 조회한다.

```SQL
SELECT *
FROM reviews
WHERE submit_date >= '2025-01-01';
```

## Date Difference

두 날짜 간의 차이를 계산한다.  

```SQL
SELECT 
    order_id,
    shipped_date - order_date AS days_diff
FROM orders;
```

# Reference

- [DataLemur SQL Tutorial](https://datalemur.com/sql-tutorial/sql-date-time-function)