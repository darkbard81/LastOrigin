# LastOrigin Continuity Schema v2.0

이 문서는 `LastOrigin` 캠페인의 연속성 관리 파일 구조를 정의한 최신 버전 스키마다. 기존 `LastOrigin_Continuity_schema.md`를 기반으로 실제 사용 사례와 자동화 적용을 고려해 다음 항목들이 추가되었다:

---

## 🧭 캠페인 정보
```json
"campaign": "string",          // 캠페인 식별자 또는 제목
"location": "string"           // 현재 진행 지역 (던전/도시 등)
```

## 🧑‍🤝‍🧑 파티 정보
```json
"party": {
  "leader": "string",          // 파티 리더 이름
  "members": [
    {
      "name": "string",
      "level": number,
      "gear": {
        "weapon": "string",
        "armor": "string",
        "items": ["string"]
      },
      "spells": {
        "1": { "slots_total": number, "slots_used": number, "prepared": ["string"] },
        "2": { "slots_total": number, "slots_used": number, "prepared": ["string"] },
        "focus_points": number
      }
    }
  ]
}
```

## ⏰ 시간 기록
```json
"time": {
  "current_day": number,
  "clock": "HH:MM",          // 현재 시각
  "activity_hours": number,   // 활동 시간 누적
  "utility_hours": number,    // 식사/기도/정비 시간 누적
  "sleep_hours": number,      // 수면 시간 누적
  "last_meal": "HH:MM",
  "last_sleep": "HH:MM"
}
```

## 🌍 세계 상태
```json
"world_state": {
  "dungeon_floor": number,
  "frontier_warp_marker": boolean,
  "passport_events": ["string"],
  "last_checkpoint": "string",
  "last_checkpoint_desc": "string"
}
```

## ❤️ 감정 관계
```json
"relationships": {
  "캐릭터이름": {
    "상대이름": 감정단계(0~5)
  }
}
```

## 🎬 장면 로그
```json
"scene_log": [
  {
    "timestamp": "Day N - HH:MM",
    "location": "string",
    "description": "string",
    "time_spent": "string"
  }
]
```

## 🎒 인벤토리
```json
"inventory": {
  "shared_items": [
    { "name": "string", "quantity": number }
  ],
  "party_gold": number
}
```

## 💞 감정 로그
```json
"emotion_log": [
  {
    "log_id": number,
    "timestamp": "Day N - HH:MM",
    "scene_id": number,
    "from": "string",
    "to": "string",
    "change": "+1" 또는 "-1",
    "new_stage": number,
    "trigger": "string",
    "note": "string"
  }
]
```

## 🆙 레벨업 로그
```json
"levelup_log": [
  {
    "character": "string",
    "level": number,
    "status": "planned" | "confirmed",
    "timestamp": "Day N - HH:MM",
    "changes": {
      "hp_increase": number,
      "trained_skills_added": ["string"],
      "class_feat_gained": "string",
      "general_feat_gained": "string",
      "skill_increases": ["string"],
      "spells_added": ["string"],
      "notes": "string"
    }
  }
]
```

---

> 본 스키마는 `LastOrigin` 캠페인의 연속성과 자동화를 보장하기 위해 v2.0으로 확장되었으며,
> 이전 버전(`LastOrigin_Continuity_schema.md`)과 호환되지 않는 구조 변경을 포함합니다.
