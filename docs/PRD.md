# HaruDiary App - PRD
---

## 개요
---
본 앱은 사용자의 하루 일상을 자동으로 기록(녹음/녹화)하고, 이를 기반으로 AI가 요약된 일기 초안을 생성해주는 개인 기록 도우미입니다.  
사용자는 자동 수집된 자료를 바탕으로 직접 일기를 작성하거나, 자동 생성된 요약을 수정하여 저장할 수 있습니다.

---

## 문제 정의
---
- 바쁜 일상 속에서 일기를 꾸준히 쓰기 어렵다.
- 하루를 돌아보는 기록이 필요하지만, 기억이 흐려져 중요한 순간을 놓친다.
- 감정의 흐름이나 패턴을 객관적으로 인식하기 어렵다.

---

## 목표
---
- **하루 동안 있었던 일**을 자동으로 기록하고 정리
- **STT + 요약 모델**을 통해 **일기 초안 자동 생성**
- 사용자가 직접 **수정/편집하여 일기 완성**
- **감정 흐름**이나 **주요 사건 타임라인** 제공

---

## 핵심 기능 (MVP)
---
### 🎤 1. **백그라운드 음성 녹음**
- 일정 간격(예: 10분) 또는 이벤트 기반(대화 감지) 자동 녹음
- 무음 자동 감지 및 구간 분할

### 🧠 2. **음성 → 텍스트 (STT) 변환**
- Whisper 또는 Google STT를 활용해 각 오디오를 텍스트로 변환

### ✨ 3. **요약 및 일기 초안 생성**
- LLM 기반 요약: "오늘의 일" 요약문 생성
- 시간대별 키워드/행동 목록 자동 구성

### 📅 4. **일기 편집 및 저장**
- AI가 생성한 일기 초안 확인
- 직접 편집, 추가 후 저장
- 일자별 일기 조회 기능 포함

### 📈 5. **감정 분석 (텍스트 기반)**
- 하루 감정 흐름 시각화 (긍정/부정/중립)

---

## 사용자 흐름 (User Flow)
---
```mermaid
flowchart TD
    A[앱 실행] --> B[자동 녹음 시작]
    B --> C[무음 감지 후 구간 분할]
    C --> D[STT 변환]
    D --> E[AI 요약 → 일기 초안 생성]
    E --> F[사용자 일기 확인/편집]
    F --> G[일기 저장 및 감정 분석]
    G --> H[홈 화면 요약 표시]
