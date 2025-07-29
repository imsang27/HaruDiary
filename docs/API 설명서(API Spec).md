# HaruDiary App – API 명세서 (v0.1)
---

## ✅ API 기본 정보
- API 통신: RESTful (JSON 기반)
- 인증 방식: (향후) 토큰 기반 인증 또는 사용자 UUID
- 응답 형식: `application/json`
- 에러 코드: HTTP 상태 코드 + 메시지

---

## 🎙️ [POST] /stt/whisper
### 설명
녹음된 오디오 파일을 Whisper로 STT 처리

### 요청
- Content-Type: multipart/form-data
- 필드:
  - `audio`: `.wav` or `.mp3` 파일 업로드

### 응답
```json
{
  "text": "오늘은 회의가 많았다.",
  "segments": [
    {"start": "00:00:00", "end": "00:00:30", "text": "회의 시작 전..."}
  ]
}
```

### 응답 코드
- 200 OK
- 400 Bad Request (파일 누락)
- 500 Internal Server Error

---

## ✨ [POST] /summary/gpt
### 설명
STT 결과 텍스트를 기반으로 요약 생성

### 요청
```json
{
  "text": "회의 시작 전 우리는..."
}
```

### 응답
```json
{
  "summary": "오늘은 오전 회의와 점심 약속이 있었다.",
  "key_events": ["회의", "점심"]
}
```

---

## 😡 [POST] /emotion/analyze
### 설명
텍스트 내용을 감정 분석하여 시간대별 감정 추출

### 요청
```json
{
  "segments": [
    {"time": "09:00", "text": "회의 전 짜증났다."},
    {"time": "13:00", "text": "점심이 즐거웠다."}
  ]
}
```

### 응답
```json
{
  "overall": "mixed",
  "timeline": [
    {"time": "09:00", "emotion": "negative"},
    {"time": "13:00", "emotion": "positive"}
  ]
}
```

---

## 💾 [POST] /diary/save
### 설명
요약 + 사용자 편집 내용 저장

### 요청
```json
{
  "date": "2025-07-29",
  "ai_summary": "오늘은 회의가 있었다.",
  "user_edit": "회의 내용은 비밀 유지 필요.",
  "segments": [],
  "emotion": {}
}
```

### 응답
```json
{
  "status": "saved",
  "path": "diary/2025-07-29.json"
}
```

---

## 📅 [GET] /diary?date=YYYY-MM-DD
### 설명
해당 날짜의 일기 데이터 조회

### 응답
```json
{
  "date": "2025-07-29",
  "ai_summary": "...",
  "user_edit": "...",
  "segments": [],
  "emotion": {}
}
```

---
