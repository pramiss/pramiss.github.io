---
title: 코테/알고리즘 Overview
date: 2024-12-30 12:00:00 +0900
image: https://github.com/user-attachments/assets/ebd27c0a-3785-4d88-8ae6-8f69237e63b8
categories: [알고리즘, 이론]
tags: [coding_test] # TAG names should always be lowercased
---

> [코딩 테스트 합격자 되기, 자바편 (김희성 지음)](https://www.yes24.com/Product/Goods/125183948){: target="_blank" } 을 토대로 공부하고 요약한 글입니다.
{: .prompt-info }

<br>





## **1. 문제분석**

> 무작정 코드를 작성하기 보다는 문제 분석에 50~60% 의 시간을 할애해야 합니다.

* **유닛 단위로 쪼개기**
  * 문제를 동작 단위로 쪼개서 분석하면 한번에 생각해야 하는 양을 줄일 수 있습니다.

* **Input 분석**
  * 문제에서 주어진 input 범위를 보고 알고리즘 후보군을 빠르게 추릴 수 있습니다.

* **Linear or Nonlinear 파악**
  * Linear steps ➔ *반복문(iteration)* 사용
  * Nonlinear steps ➔ *재귀(recursion)* 사용 - Recursion은 비효율성의 문제를 동반

* **Greedy는 제한적**
  * Greedy 알고리즘이 사용되는 경우는 잘 없습니다. 잘못된 greedy 사용은 시간낭비를 발생시키므로, 반드시 수학적, 논리적으로 정답이 나올 수 있을지 검토 후 사용해야합니다.



## **2. Pseudo Code**

> 문제 분석 및 알고리즘 선택 완료시 바로 코딩을 하지 않고 pseudo code로 먼저 로직을 작성합니다.

- **동작 위주 작성**
   - Pseudo code는 추상단계에서 **동작 중심으로 작성**합니다. 여기서 세부 구현은 필요 없습니다. 그건 실제 구현단계(코드작성)로 미룹니다.

- **Step-by-Step 작성**
   - Pseudo code는 문제 해결 순서대로 작성합니다. 실제 코드를 구현할 때 주석 역할이 됩니다.

- **오류 검증**
   - pseudo code 단계에서도 충분한 테스트가 필요합니다. 실제 구현 코드를 수정하는 것보다 pseudo code를 수정하는 것이 훨씬 효율적입니다.




## **3. 코드 작성**

> 작성한 pseudo code에 따라 실제로 코드를 구현합니다.




## **4. 기록, 정리**

-  **기록 <sup>LOG</sup>** ㅣ 문제를 끝까지 못 풀더라도 **어떤 알고리즘을 적용하려고 했는지, 근거는 무엇인지, 그것을 어떻게 코드로 작성하려 했는지 기록**합니다.

- **요약 <sup>SUMMARY</sup>** ㅣ 내가 정말 이해했는지 확인하기 위해 **공부한 것을 요약**해봅니다. 블로그를 작성하면서 공부한 것을 정리하고 요약합니다.

> '아는 것'과 '안다고 생각하는 것'을 명확히 구분하고 공부하기

