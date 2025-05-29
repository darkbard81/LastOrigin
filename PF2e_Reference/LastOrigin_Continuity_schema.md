# LastOrigin 연속성 문서 스키마 설명

이 문서는 LastOrigin 캠페인의 연속성 문서(JSON)의 구조와 각 항목의 의미를 명시합니다.

---

## 🧭 campaign (string)

- 캠페인 이름 (예: "LastOrigin")

## 🗺️ location (string)

- 현재 파티가 위치한 지역 또는 도시 이름 (예: "Passport")

---

## 🧑‍🤝‍🧑 party (object)

### leader (string)
- 파티 리더의 이름

### members (array[object])
각 캐릭터에 대한 기본 정보:

| 필드명 | 타입 | 설명 |
|--------|------|------|
| name | string | 캐릭터 이름 |
| class | string | 클래스와 옵션 (예: "Cleric (Warpriest)") |
| level | integer | 현재 레벨 |
| alignment | string | 성향 (예: "Chaotic Good") |
| role | string | "Player" 또는 "NPC" |
| gear | object | 장비 정보 (아래 참조) |

#### gear (object)

| 필드명 | 타입 | 설명 |
|--------|------|------|
| weapon | string | 주요 무기 이름 |
| armor | string | 착용 방어구 이름 |
| items | array[string] | 기타 장비 또는 도구 목록 |

---

## 🕒 time (object)

파티 하루 시간 경과 상태를 기록합니다.

| 필드명 | 타입 | 설명 |
|--------|------|------|
| current_day | integer | 탐색 시작 이후 경과 일수 |
| clock | string | 현재 시간 (24h 표기, 예: "13:00") |
| activity_hours | number | 활동 시간 누적 (전투, 탐색 등) |
| utility_hours | number | 유동 시간 누적 (식사, 회복 등) |
| sleep_hours | number | 수면 시간 누적 |
| last_meal | string | 마지막 식사 기록 (예: "Day 1 - 09:00") |
| last_sleep | string | 마지막 수면 기록 (예: "Day 0 - 22:00") |

---

## 🌍 world_state (object)

캠페인 세계의 진행 상태를 나타냅니다.

| 필드명 | 타입 | 설명 |
|--------|------|------|
| dungeon_floor | integer/null | 현재 탐색 중인 무한의 프론티어 층수 |
| frontier_warp_marker | boolean | 워프마커 사용 여부 |
| passport_events | array[string] | 패스포트에서 발생한 주요 사건들 |

---

## 💞 relationships (object)

각 캐릭터 간의 감정 단계 (0~5)를 기록합니다.  
예:

{
  "슬라몬": {
    "리산드라": 2,
    "키티": 3
  }
}

---

## 🎬 scene_log (array[object])

각 장면별 요약 및 시간 소비 기록.

| 필드명 | 타입 | 설명 |
|--------|------|------|
| scene_id | integer | 장면 고유 번호 |
| title | string | 장면 제목 |
| timestamp | string | 장면 시작 시점 (예: "Day 1 - 08:00") |
| location | string | 장면 발생 위치 |
| summary | string | 간단한 요약 |
| time_spent_hours | number | 소비된 시간 (단위: 시간) |

---

## 🎒 inventory (object)

파티 공유 자산 기록.

| 필드명 | 타입 | 설명 |
|--------|------|------|
| party_gold | integer | 파티 금화량 |
| shared_items | array[object] | 공유 아이템 |

#### shared_items 구조:

| 필드명 | 타입 | 설명 |
|--------|------|------|
| name | string | 아이템 이름 |
| quantity | integer | 개수 |

---

## 💓 emotion_log (array[object])

감정 단계 변화나 감정 이벤트 이력.

| 필드명 | 타입 | 설명 |
|--------|------|------|
| log_id | integer | 고유 감정 로그 번호 |
| timestamp | string | 시간 (예: "Day 1 - 08:00") |
| scene_id | integer | 발생 장면 번호 |
| from | string | 감정을 느낀 캐릭터 |
| to | string | 대상 캐릭터 |
| change | string | 단계 변화 수치 ("+1", "-1") |
| new_stage | integer | 변화 후 단계 (0~5) |
| trigger | string | 유발한 대사, 행동, 사건 |
| note | string | 서술적 설명, 반응 등

---

## 🧬 levelup_log (array[object])

캐릭터의 레벨업 기록

| 필드명 | 타입 | 설명 |
|--------|------|------|
| character | string | 캐릭터 이름 |
| level | integer | 도달한 레벨 |
| status | string | "planned" 또는 "confirmed" |
| timestamp | string/null | 레벨업 시점 |
| changes | object | 상세 변경 내용 (아래 참조) |

#### changes 구조:

| 필드명 | 타입 | 설명 |
|--------|------|------|
| hp_increase | integer/null | 증가한 HP |
| trained_skills_added | array[string] | 새로 습득한 스킬 |
| class_feat_gained | string/null | 획득한 클래스 피트 |
| spells_added | array[string] | 추가된 주문 |
| notes | string | 빌드 방향, 서사 메모 등
