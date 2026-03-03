---
title: "Intermediate SQL: Arithmetic Operators"
slug: intermediate-sql-arithmetic-operators
categories: [Database, SQL]
tags: [Database, SQL]
---

# Description

SQL의 **산술 연산자(Arithmetic Operators)** 는 컬럼 값이나 숫자 리터럴을 대상으로 수학적 계산을 수행할 때 사용된다. 주로 금액 계산, 비율 산출, 파생 컬럼 생성 등 계산된 결과를 조회할 때 활용된다. SQL에서 지원하는 대표적인 산술 연산자는 다음과 같다.

- `+` : 덧셈
- `-` : 뺄셈
- `*` : 곱셈
- `/` : 나눗셈

# Syntax

산술 연산자는 `SELECT` 절과 `WHERE` 절 모두에서 사용할 수 있다. 계산 결과는 **새로운 컬럼 형태로 반환**되고 필요에 따라 `AS` 키워드로 컬럼 별칭을 지정할 수 있다.

```SQL
SELECT column1 + column2
FROM table_name;
```

```SQL
SELECT column1 * value
FROM table_name;
```

# Example

## Addition

`orders` 테이블에서 상품 가격과 세금을 더한 총 금액을 계산한다.

```SQL
SELECT order_id,
       price + tax AS total_price
FROM orders;
```

## Subtraction

`products` 테이블에서 정가에서 할인 금액을 뺀 실제 판매가를 계산한다.

```SQL
SELECT product_id,
       list_price - discount AS final_price
FROM products;
```

## Multiplication

`order_items` 테이블에서 단가와 수량을 곱해 총 주문 금액을 계산한다.

```SQL
SELECT order_id,
       unit_price * quantity AS total_amount
FROM order_items;
```

## Division

`employees` 테이블에서 연봉을 12로 나누어 월급을 계산한다.

```SQL
SELECT employee_id,
       salary / 12 AS monthly_salary
FROM employees;
```

# Reference
- [DataLemur SQL Tutorial](https://datalemur.com/sql-tutorial/sql-arithmetic)