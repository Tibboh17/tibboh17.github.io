---
title: Introduction to Mathematical Statistics - Chapter 1
categories: [Study, Mathematical Statistics]
tags: [Mathematical Statistics, Probability, Hogg]
math: true
---

# Introduction

## Random Experiment and Sample Space
어떤 실험에서 가능한 모든 결과의 집합을 표본공간이라 하고, 각각의 결과(사건)를 표본점이라 한다. 예를 들어, 동전 던지기의 표본공간은 {H, T}가 되고, 주사위 던지기의 경우 {(1,1), (1,2), … , (6,6)} 같은 식으로 기술할 수 있다.

## Probability
실험을 여러 번 반복했을 때 어떤 사건 A가 발생한 빈도(상대도수)가 장기적으로 어떤 값 p에 안정되면, 그 값을 사건 A의 확률로 정의할 수 있다.

# Sets

## Set and Event
표본공간 C의 부분집합을 사건이라고 부른다. 집합 연산(여집합, 합집합, 교집합, 분할 등)을 이용해 사건들을 다룰 수 있습니다.

## σ-field
확률론에서, 사건들의 모임이 적절한 연산(여집합, 가산 합집합 등)에 대해 닫혀 있어야 하는데, 이를 만족하는 부분집합들의 모임을 $σ$-필드라 힌디.

# Probability Set Function

## Definition and Features

표본공간 $C$, 사건들의 집합 $B$, 확률함수 $P$로 이루어진 삼중쌍을 말한다. 확률함수 $P$는 다음 조건을 만족한다.

- $\forall A\in B,P(A)\ge 0$
- $P(c) = 1$
- $\left\{ A_n \right\}$은 $B$에 있는 사건열이고 $\forall m\neq n, A_m\cap A_n=\emptyset$이면
$$ P\left(\bigcup_{n=1}^{\infty }A_n \right)=\sum_{n=1}^{\infty }P(A_n). $$