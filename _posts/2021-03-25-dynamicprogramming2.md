---
title: "Dynamic Programming 개념"
categories: 
  - Algorithm
  - Dynamic Programming
last_modified_at: 2021-03-25
toc: false #Table of Contents
comments: true
use_math: true # MathJax On
---

## 1로 만들기

정수가 X가 주어질 때 정수 X에 사용할 수 있는 연산은 다음 4가지 이다.
- X가 5로 나누어 떨어지면, 5로 나눈다.
- X가 3으로 나누어 떨어지면, 3으로 나눈다.
- X가 2로 나누어 떨어지면, 2로 나눈다.
- X에서 1을 뺀다.

정수 X가 주어졌을 때, 연산 4개를 적절히 사용해서 1을 만들려고 한다. 연산을 사용하는 횟수의 최솟값을 출력하시오.

#### 문제

- 첫째 줄에 정수 X가 주어진다.(1 <= X <= 30,000)

#### 접근 방법

다이나믹 프로그래밍 문제이다. 그림으로 이해하면 좋은데, 다음은 X=6일 때, 함수가 호출되는 과정이다.

<br>
<center><img src="/assets/images/dynamicprogramming2_1.jpg" width="500" ></center>
<br>

해당 내용을 점화식으로 표현하면 다음 식과 같고, 점화식 끝에 1을 더해주는 이유는 함수의 호출 횟수를 구해야 하기 때문이다.
$$a_i = min(a_{i-1},a_{i/2},a_{i/3},a_{i/5}) + 1$$
