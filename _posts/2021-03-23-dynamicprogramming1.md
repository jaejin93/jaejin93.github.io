---
title: "Dynamic Programming 개념"
categories: 
  - Algorithm
  - Dynamic Programming
last_modified_at: 2021-03-23
toc: false #Table of Contents
comments: true
use_math: true # MathJax On
---

## 다이나믹 프로그래밍

#### 중복되는 연산을 줄이자

컴퓨터는 연산 속도에 한계가 있고, 메모리 공간을 사용할 수 있는 데이터의 개수도 한정적이다. 그래서 효율적인 알고리즘을 작성해야 한다.  다이나믹 프로그래밍(동적 프로그래밍, Dynamic Prgramming)의 경우 메모리 공간을 약간 더 사용해 연산 속도를 비약적으로 상승시킨다. 다이나믹 프로그래밍으로 해결할 수 있는 대표적인 예시로 피보나치 수열이 있다. 피보나치의 점화식은 다음과 같이 표현할 수 있다. 

$$a_{n+2} = f(a_{n+1}, a_n) = a_{n+1} + a_n $$
