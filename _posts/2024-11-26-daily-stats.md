---
title: Daily Stats API Logic 설계
description: 날짜별 개별 운동에 대한 tempo를 기록하고 뿌려주는 API입니다.
date: 2024-11-26 13:18:00 +0900
categories: [Project, PhysicalTrack]
tags: [physical_track_api] # TAG names should always be lowercased
---

<br>

## <span style="background-color:#BBE1FA; padding: 1px 10px 1px 1px;">1. Daily Stats Web UI 예시</span>

---

![image-20241126131726650](../assets/img/contents/2024-11-26-daily-stats/image-20241126131726650.png){: width="300px" style="border-radius:8px;"}
_해당 날짜의 운동 페이스를 그래프로 나타냅니다._



![image-20241126132004940](../assets/img/contents/2024-11-26-daily-stats/image-20241126132004940.png){: width="300px" style="border-radius:8px;"}
_해당 날짜에 운동을 하지 않은 경우 UI 디자인입니다._

<br>



## <span style="background-color:#BBE1FA; padding: 1px 10px 1px 1px;">2. Daily Stats 전체 로직 설계</span>

---

### 1) `workout_detail`에  `tempo` 속성으로 기록

```mermaid
flowchart LR
    A(iOS App) --> |workoutDetail JSON에<br>tempo 데이터 포함|B[Record 서비스]
    B --> |JSON 파싱 및<br>tempo 유효성 검증|C{검증}
    C -->|Yes| D[(RECORDS)]
    C -->|No| E[에러 응답]
```

- **`tempo`** 속성
  - 타입: `ArrayList<Double>`
  - Null이 아닐 경우 유효성 검사 필요 (Nullable)

<br>



### 2) Daily Stats API 구현

```mermaid
flowchart LR
	A(Web) --> |userId, date|B[Statistics 서비스]
	B --> |userId, date|C[Record 서비스]
	C --> |userId, date| D[(RECORDS)]
	D --> |Record|C
	C --> |RecordDto|B
	B --> |DailyStatsDto|A
```
<br>
- Statistics 서비스 레이어에서 Record 데이터에 있는 `workoutDetail - tempo`를 추출해서 `dto` 에 담습니다.
  - **CASE1:** 해당 날짜에 운동을 안한 경우 or 운동은 했지만 `tempo` 는 기록하지 않은 경우
    - **RETURN:** 빈 배열 `[ ]` 
  - **CASE2:** 해당 날짜에 운동을 하고 `tempo` 도 기록된 경우
    - **RETURN:** [1.34, 2.43, 3.42, 5.1, ... ]
  - **CASE3:** `tempo` 가 잘못된 형식으로 저장된 경우 {Exception 발생}
    - **RETURN:** error code & error message
    - 하지만 기록할 때 유효성 검사를 하므로 이런 경우는 없어야합니다.



