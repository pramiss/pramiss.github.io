---
title: 코딩테스트 시작하기
date: 2024-12-30 12:00:00 +0900
image: https://github.com/user-attachments/assets/ebd27c0a-3785-4d88-8ae6-8f69237e63b8
categories: [Coding Test, Coding test with JAVA]
tags: [coding_test] # TAG names should always be lowercased
---

> [코딩 테스트 합격자 되기, 자바편 (김희성 지음)](https://www.yes24.com/Product/Goods/125183948){: target="_blank" } 을 토대로 공부하고 요약한 글입니다. 본격적으로 코딩 테스트 공부를 시작하기 전 공부방법과 마인드셋을 정리합니다.
{: .prompt-info }

<br>



## **Before You Code**

### *Use Coding Test Sites*

1. <u>Learn from Other Solutions</u>
   * 문제를 푸는 데 사용한 **알고리즘, I/O 처리 방식, Exception 처리 방식**을 학습하는데 유용합니다.  
   * 단, **숏코딩(short coding)**이 항상 좋은 것은 아니므로 매몰되지 않도록 주의합니다.

2. <u>Create Your Own Testcases</u>
   * 문제에서 제공하는 테스트케이스와 채점 시 사용되는 테스트케이스는 다릅니다.
     * 문제의 `testcase` - 문제를 설명하는 수준에서 제공됩니다.
     * 채점 시 `testcase` - 여러 실수와 예외 처리 상황이 포함됩니다.
   * 이때, 나만의 테스트케이스를 만들어 문제를 명확히 이해할 수 있습니다.

> 프로그래머스, 백준 등을 통해 코테 연습을 할 때 사이트의 장점을 잘 이용하면 좋습니다.


### *Log & Summary*

1. <u>Log Your Ideas</u>
   * 문제를 끝까지 못 풀더라도 **어떤 알고리즘을 적용하려고 했는지, 근거는 무엇인지, 그것을 어떻게 코드로 작성하려 했는지 기록**합니다.

2. <u>Regular Timed Practice</u>
   * 실전 코딩테스트에는 시간 제한이 있습니다. 당연히 평소에 시간 배분 전략을 연습해둔 사람과 그렇지 않은 사람의 결과는 다릅니다. 주기적인 자체 시험을 봅니다.

3. <u>In Your Own Words</u>
   * 내가 정말 이해했는지 확인하기 위해 **공부한 것을 요약**해봅니다.
   * 저는 이 블로그를 작성하면서 공부한 것을 정리하고 요약하고자 합니다.

> '내가 아는 것'과 '내가 안다고 생각하는 것'을 명확히 구분하고 공부해야 합니다.

<br>

## **Ace Your Code**

#### *Java Language*

* 변수 선언하기
* 함수 정의하기
* 컬렉션 자료형 다루기
* 조건문, 반복문 사용하기

> 코딩 테스트에서 언어는 크게 중요한 요소는 아닙니다. 어떤 언어를 선택하든 위 4가지에 대해 자신있게 사용할 수 있도록 연습합니다. 저는 백엔드 공부를 하며 Java를 사용했으므로 코딩테스트도 Java로 공부할 예정입니다.

#### *Analyze the Problem*

1. <u>Divide the Problem to Analyze</u>
   * 문제를 동작 단위로 쪼개서 분석하면 한번에 생각해야 하는 양을 줄일 수 있습니다.
2. <u>Check Limits, Write Testcases</u>
   * 제약 사항에 기반한 Own Testcase를 추가하는 연습을 합니다.
3. <u>Analyze Inputs</u>
   * **입력값의 크기와 A&DS 시간복잡도**를 이용해 후보의 알고리즘을 빠르게 추려낼 수 있습니다.
4. <u>If Greedy, Justify</u>
   * 잘못된 Greedy 사용은 시간낭비를 크게 발생시키므로, Greedy는 반드시 수학적, 논리적으로 정답이 나올 수 있을지 **검토 후 사용**해야합니다.
5. <u>Understand Data Flow</u>
   * Input 뿐만 아니라 **Data flow도 A&DS 결정**에 중요합니다. 예를 들어, 데이터 삽입/삭제가 빈번하고 최댓값/최솟값을 반복적으로 구하는 환경에서는 힙(heap) 자료구조를 고려하는게 좋습니다.

> 코딩 테스트는 '코딩 능력'이 아니라 '문제 풀이 능력'을 테스트하는 시험입니다. 따라서, 무작정 코드를 작성하기 보다는 문제 분석에 50~60% 의 시간을 할애해야 합니다.

#### *Design in Pseudo Code*

1. <u>Focus on Behavior, Not Details</u>
   * Pseudo code는 추상단계에서 **동작 중심으로 작성**합니다. 여기서 세부 구현은 필요 없습니다. 그것은 실제 구현단계(코드작성)로 미룹니다.
2. <u>Write in Solution Order</u>
   * Pseudo code는 문제 해결 순서대로 작성합니다. 실제 코드를 구현할 때 주석 역할이 됩니다.
3. <u>Test Thoroughly</u>
   * 코드 작성 뿐만 아니라 **pseudo code 단계에서도 충분한 테스트**가 필요합니다. 실제 구현 코드를 수정하는 것보다 pseudo code를 수정하는 것이 훨씬 효율적입니다.



> Pseudo code는 프로그램의 논리를 설명하고 알고리즘을 표현하기 위해 작성된 일종의 지침입니다. 실제 구현 단계가 아닌 추상 단계에서 설계를 진행할 수 있어 설계 아이디어에 집중하고, 오류 수정이 용이합니다.