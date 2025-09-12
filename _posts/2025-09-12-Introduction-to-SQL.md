---
title: Introduction to SQL
categories: [Database, SQL]
tags: [Database, SQL]
---

# What is SQL?
**SQL**(Structured Query Language)은 관계형 데이터베이스에서 데이터를 질의하고, 조작하며, 변환할 수 있도록 설계된 언어이다. 기술적인 사용자뿐만 아니라 비전문가도 사용할 수 있도록 설계되었으며, 그 단순함 덕분에 SQL 데이터베이스는 수많은 웹사이트와 모바일 애플리케이션에서 안전하고 확장 가능한 저장소로 널리 사용되고 있다.

> SQLite, MySQL, Postgres, Oracle, Microsoft SQL Server 등 널리 쓰이는 SQL 데이터베이스가 많다. 이들 모두는 이 사이트에서 다룰 공통 SQL 언어 표준을 지원하지만, 각각 지원하는 추가 기능과 저장 유형이 서로 다를 수 있다.

# Relational Databases
SQL 문법을 배우기 전에, **관계형 데이터베이스**가 실제로 무엇인지에 대한 모델을 갖는 것이 중요하다. **관계형 데이터베이스**는 서로 관련된 (2차원) 테이블들의 모음이다. 각 테이블은 엑셀 스프레드시트와 비슷하며, 이름이 붙은 고정된 개수의 열(테이블의 속성 또는 특성)과 임의의 개수의 행으로 이루어진다.

예를 들어 차량관리국(DMV)에 데이터베이스가 있다면, 사람들이 운전하는 것으로 알려진 모든 차량을 담은 테이블이 있을 것이다. 어떤 테이블이 존재하여 각 차량의 모델명, 유형, 바퀴 수, 문 수 등을 저장한다면 아래와 같은 형태일 것이다.

| Id | Make/Model         | # Wheels | # Doors | Type       |
|---:|--------------------|---------:|--------:|------------|
|  1 | Ford Focus         |        4 |       4 | Sedan      |
|  2 | Tesla Roadster     |        4 |       2 | Sports     |
|  3 | Kawakasi Ninja     |        2 |       0 | Motorcycle |
|  4 | McLaren Formula 1  |        4 |       0 | Race       |
|  5 | Tesla S            |        4 |       4 | Sedan      |

이러한 데이터베이스에는 등록된 운전자의 목록, 발급 가능한 운전면허의 종류, 심지어 각 운전자의 교통 위반 내역과 같은 정보를 담은 추가적인 관련 테이블이 있을 수 있다.

SQL을 배우는 목적은 이 데이터에 대해 “도로 위에 바퀴가 네 개 미만인 차량 유형은 무엇인가?”, “테슬라는 자동차 모델을 몇 가지 생산하는가?”와 같은 구체적인 질문에 답하는 방법을 익혀, 앞으로 더 나은 의사결정을 내리도록 돕는 것이다.

# Referece
- [SQLBolt: Introduction to SQL](https://sqlbolt.com)