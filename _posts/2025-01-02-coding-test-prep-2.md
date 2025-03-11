---
title: Algorithm - 시간복잡도
date: 2025-01-02 12:00:00 +0900
image: https://github.com/user-attachments/assets/03505bff-823f-48a5-94e3-aecd864767b2
categories: [Coding Test, Coding test with JAVA]
tags: [coding_test] # TAG names should always be lowercased
math: true
---

> [코딩 테스트 합격자 되기, 자바편 (김희성 지음)](https://www.yes24.com/Product/Goods/125183948){: target="_blank" } 을 토대로 공부하고 요약한 글입니다. 입력값과 시간복잡도의 관계에 대해서 알아봅니다. 그리고 시간복잡도에 따른 알고리즘 선택방법을 생각해봅니다.
{: .prompt-info }

<br>

## **1. 시간 복잡도<sup>Time Complexity</sup>**

### Concept

* 알고리즘의 성능을 나타내는 지표
* 입력 크기에 대한 연산 횟수의 상한을 의미
* 낮을수록 좋은 성능

> 문제에서 입력값은 데이터 범위로 주어지는데, 이를 '처리해야 할 데이터 양'으로 생각하면 편합니다.
{: .prompt-tip }

### 점근적 표기법

* 입력 크기(범위)를 N으로 일반화하여 연산 횟수의 추이를 나타내는 방법
* 입력 크기(N)에 따른 연산 횟수의 추이를 활용해 시간 복잡도를 표현하는 방법

### 빅오<sup>big-O</sup> 표기법

* 연산 횟수 식에서 최고차항을 남기고 계수를 지워서 표기합니다.

<img src="https://github.com/user-attachments/assets/0d395433-526b-4fde-8e66-86db6045fbf9" width="400">

* 최고차항만 남기는 작업에서 우선순위는 다음과 같습니다.

<img src="https://github.com/user-attachments/assets/b835ddcc-8a66-45ff-b6d6-14fcc4c3203e" width="500">

* 문제당 허용 연산 횟수를 1초에 1,000~3,000만 정도로 고려해서 시간 복잡도를 생각했을 때, 시간 복잡도에 따른 N의 가용 범위는 다음과 같습니다.

|  시간 복잡도   | N의 가용 범위 |
| :------------: | :-----------: |
|  $$ O(N!) $$   |      10       |
|  $$ O(2^N) $$  |     20~25     |
|  $$ O(N^3) $$  |    200~300    |
|  $$ O(N^2) $$  |  3,000~5,000  |
| $$ O(NlogN) $$ |     100만     |
|   $$ O(N) $$   | 1,000~2,000만 |
| $$ O(logN) $$  |     10억      |
|   $$ O(1) $$   | $$ \infty $$  |

> (제한시간이 1초 일 때) N과 시간 복잡도를 고려한 연산 횟수가 3,000만이 넘으면 잘못된 알고리즘 사용입니다.
{: .prompt-danger }



<br>

## **2. 시간 복잡도를 고려한 Problem Solve**

1. <u>문제 분석 및 정의하기</u>
   * 문제 요구사항(input, output) 및 제약사항을 정확히 파악합니다.
   * 필요하다면 edge case로 testcase를 작성합니다.

2. <u>Input 범위(N)에 따라 알고리즘 걸러내기</u>

   * 문제에서 주어진 입력값(N)으로 불필요한 알고리즘들을 걸러냅니다.
   * 예를 들어, $$ N ≥ 100,000 $$ 이면, $$ O(N^2) $$ 시간 복잡도를 가진 알고리즘은 자동으로 배제됩니다.
3. <u>Problem Solution</u>

   * Algorithm과 Data Structure를 선택해서 문제를 해결합니다.
   * 이 단계에서 정확성 테스트가 통과되어야 합니다.
4. <u>Solution의 연산 횟수 및 시간 복잡도 분석</u>

   * Solution 알고리즘의 시간 복잡도가 N을 가용범위에 두는지 분석합니다.
   * 이 단계에서 효율성 테스트가 통과되어야 합니다.

> 최대한 위의 과정을 생각하며 문제 풀기
{: .prompt-tip }