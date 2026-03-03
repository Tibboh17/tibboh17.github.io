---
title: "Instermediate SQL: JOIN"
slug: intermediate-sql-join
categories: [Database, SQL]
tags: [Database, SQL]
---

# Description

`JOIN`은 **둘 이상의 테이블을 공통 컬럼을 기준으로 결합**할 때 사용된다. 테이블 간의 관계를 기반으로 데이터를 확장하여 조회할 수 있으며, 조인 방식에 따라 **포함되는 행의 범위**가 달라진다. 대표적인 `JOIN` 유형에는 `INNER JOIN`, `LEFT JOIN`, `RIGHT JOIN`, `FULL OUTER JOIN` 이 있다.

# Syntax

`JOIN` 문에서는 사용할 조인 유형(`INNER`, `LEFT`, `RIGHT`, `FULL OUTER`)을 명시하여 결합 방식을 결정한다. `ON` 절에는 두 테이블을 연결할 조건을 작성하며, 이 조건을 기준으로 행이 매칭된다. 조건을 지정하지 않으면 모든 행이 서로 결합되는 **카티션 곱(cartesian product)**이 발생할 수 있으므로 주의해야 한다.

```SQL
SELECT column_list
FROM table1
JOIN_TYPE table2
ON table1.column = table2.column;
```

# Example

## INNER JOIN

두 테이블 모두에 **일치하는 값이 있는 행만** 반환한다.

```SQL
SELECT o.order_id, c.customer_name
FROM orders o
INNER JOIN customers c
ON o.customer_id = c.customer_id;
```

## LEFT JOIN

왼쪽 테이블의 **모든 행**과, 조건이 일치하는 오른쪽 테이블의 행을 반환한다. 일치하지 않는 경우 오른쪽 컬럼은 `NULL` 이 된다.

```SQL
SELECT c.customer_id, o.order_id
FROM customers c
LEFT JOIN orders o
ON c.customer_id = o.customer_id;
```

## RIGHT JOIN

오른쪽 테이블의 **모든 행**과, 조건이 일치하는 왼쪽 테이블의 행을 반환한다. 일치하지 않는 경우 왼쪽 컬럼은 `NULL` 이 된다.

```SQL
SELECT c.customer_id, o.order_id
FROM customers c
RIGHT JOIN orders o
ON c.customer_id = o.customer_id;
```

## FULL OUTER JOIN

양쪽 테이블의 **모든 행을 포함**하며, 일치하지 않는 컬럼은 `NULL` 로 채운다.

```SQL
SELECT c.customer_id, o.order_id
FROM customers c
FULL OUTER JOIN orders o
ON c.customer_id = o.customer_id;
```

# Reference

- [DataLemur SQL Tutorial](https://datalemur.com/sql-tutorial/sql-joins-inner-outer-left-right)