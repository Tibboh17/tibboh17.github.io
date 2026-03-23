---
title: "Advanced SQL: String Functions"
slug: advanced-sql-string-functions
categories: [Database, SQL]
tags: [Database, SQL]
date: 2026-03-23 20:00:00 +0900
---

# Description

SQL의 **문자열 함수(String Functions)**는 텍스트 데이터를 변환, 추출, 결합, 정리할 때 사용된다. 대소문자 통일, 특정 문자열 추출, 공백 제거, 문자열 길이 확인 등 **문자열 전처리와 가공 작업**에 자주 활용된다.

대표적으로 `UPPER`, `LOWER`, `LEFT`, `RIGHT`, `LENGTH`, `POSITION`, `TRIM`, `CONCAT`, `SUBSTRING` 등의 함수가 있다.

# Syntax

문자열 함수는 텍스트 컬럼이나 문자열 표현식을 입력으로 받아, 목적에 따라 변환된 문자열이나 숫자 값을 반환한다.

```SQL
SELECT FUNCTION_NAME(column_name)
FROM table_name;
```

```SQL
SELECT FUNCTION_NAME(expression)
FROM table_name;
```

# Example

## UPPER / LOWER

문자열을 모두 대문자 또는 소문자로 변환한다.

```SQL
SELECT UPPER('Avenger') AS upper_text,
       LOWER('Avenger') AS lower_text;
```

## LEFT / RIGHT

문자열의 왼쪽 또는 오른쪽에서 지정한 개수만큼 문자를 추출한다.

```SQL
SELECT LEFT('Captain', 3) AS left_text,
       RIGHT('Widow', 3)  AS right_text;
```

## LENGTH

문자열의 길이를 반환한다.

```SQL
SELECT LENGTH('Iron Man') AS text_length;
```

## POSITION

문자열 안에서 특정 부분 문자열의 시작 위치를 찾는다.

```SQL
SELECT POSITION('man' IN 'Ironman') AS position_result;
```

## TRIM

문자열 양쪽의 공백을 제거한다.

```SQL
SELECT TRIM('  Spiderman  ') AS trimmed_text;
```

## CONCAT

여러 문자열을 하나로 연결한다.

```SQL
SELECT CONCAT('Peter', ' ', 'Quill') AS full_name;
```

## SUBSTRING

문자열의 일부를 잘라서 반환한다.

```SQL
SELECT SUBSTRING('Spiderman', 1, 6) AS substring_text;
```

## SPLIT_PART

구분자를 기준으로 문자열의 특정 부분을 추출한다.

```SQL
SELECT SPLIT_PART('Iron-Man-Hero', '-', 2) AS split_result;
```

# Reference

- [DataLemur SQL Tutorial](https://datalemur.com/sql-tutorial/sql-string-text)