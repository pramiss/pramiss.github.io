---
title: Consistency Logic 추가
description: Consistency 랭킹을 산정해야 합니다. 운동 랭킹 산정과 달리 계산 과정이 많아 API 요청마다 해결하기에는 비효율적입니다. 따라서 새로운 Consistency 테이블과 레이어를 만들고 추가하는 과정을 기록했습니다.
date: 2024-11-15 09:21:00 +0900
categories: [PhysicalTrack, API Logics]
tags: [physical_track, logic_diagram] # TAG names should always be lowercased
---

## &#8226; Consistency Logic 추가하기

>  문제사항: 운동 기록(record)을 저장할 때 해당 유저의 `CONSISTENCY` 테이블의 마지막 운동 날짜(`last_workout_date`)를 업데이트 해주어야 함

<br>



### 1. Record - 기존 로직

```mermaid
flowchart LR
    A(Front) --> |request Record API|B[Record 서비스]
    B --> |Record 저장|C[(RECORDS)]
  
```

<br>



### 2. Record - 변경 로직

```mermaid
flowchart TB
    A(Front) --> |request Record API|B[Record 서비스]
    B --> |1-1. Record 저장|C[(RECORDS)]
    B --> |2-1. 유저/날짜 정보|D[Consistency 서비스]
    D --> |2-2. update 'last_workout_date' by 'user_id'|E[(CONSISTENCY)]
  
```

<br>



## &#8226; Consistency - 전체 로직

> `CONSISTENCY` 테이블 명세 (created_at, updated_at 생략)

```mermaid
erDiagram
    CONSISTENCY {
        int id PK
        int user_id FK
        int streak_count
        LocalDate last_workout_date
    }
```

<br>



### 1. 운동 기록 시 마지막 운동 날짜(`last_workout_date`) 업데이트

```mermaid
flowchart LR
    A(Front) --> |request Record API|B[Record 서비스]
    B --> |user_id, date|C[Consistency 서비스]
    C --> |update <br> 'last_workout_date'|D[(CONSISTENCY)]
```



<br>



### 2. 매일 자정 `streak_count` 업데이트

```mermaid
flowchart LR
    A[Consistency 스케줄러] -.-> |매일 자정 자동실행|C[Consistency 서비스]
    C --> |update <br> 'streak_count'|D[(CONSISTENCY)]
```

<small>`streak_count`업데이트는 오늘 날짜와 `last_workout_date` 를 비교해 진행하며, 모든 유저에 대해 진행합니다.</small>

<br>



### 3. Consistency Ranking API 호출

```mermaid
flowchart LR
    A(Front) --> |Consistency Ranking <br> API 요청|B[Ranking 서비스]
    B --> |Consistency 요청|C[Consistency 서비스]
    C --> |Get Query|D[(CONSISTENCY)]
    D --> |Consistency|C
    C --> |ConsistencyDto|B
    B --> |ConsistencyRankingDto|A
```



<small>Ranking 레이어에서 직접 `CONSISTENCY` 테이블에서 데이터를 조회하지 않고  Consistency 레이어를 이용합니다.</small>
<small>마찬가지로 Consistency 레이어에서는 데이터만 조회해서 전달할 뿐, 실제 랭킹 책정은 Ranking 레이어를 이용합니다.</small>

> 단일 책임 원칙((Single Responsibility Principle) 생각하기
{: .prompt-info}

