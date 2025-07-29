# HaruDiary App
---

## 📌 개요
하루 동안 사용자의 음성을 자동으로 녹음하고, AI를 통해 일기 초안을 생성하여 사용자가 쉽고 빠르게 하루를 정리할 수 있도록 돕는 개인 기록 앱입니다.

> “일기 쓰기보다, 일상을 기록하는 게 먼저다.”

---

## 🎯 핵심 기능 (MVP 기준)
- [ ] 백그라운드 음성 녹음 (주기적 또는 이벤트 기반)
- [ ] 무음 감지 및 구간 분할
- [ ] STT 변환 (Whisper or Google Speech-to-Text)
- [ ] AI 요약 기반 일기 초안 생성 (GPT API)
- [ ] 감정 분석 기능 (텍스트 기반)
- [ ] 일기 편집 및 저장 기능
- [ ] 일자별 기록 타임라인 및 감정 흐름 시각화

---

## 🧭 기능 흐름
1. 하루 동안 음성 자동 녹음
2. 무음 구간 제거 → 의미 있는 구간 추출
3. STT로 텍스트 변환
4. Gemini 모델로 요약 일기 초안 생성
5. 감정 분석 결과 추가
6. 사용자 확인 및 편집 후 일기 저장

---

## 🛠️ 기술 스택 (예정)
| 분류 | 도구 |
|------|------|
| 플랫폼 | Android (Kotlin), iOS (Swift) |
| 클라이언트 앱 | Flutter |
| 녹음 처리 | AudioRecord / AVFoundation |
| STT | Whisper API, Google Speech-to-Text |
| 요약 | OpenAI GPT API, HuggingFace Transformers |
| 감정 분석 | KoBERT / TextCNN |
| 백엔드 | FastAPI (Python) |
| 데이터 저장 | **Local 저장 우선 (파일 시스템 기반)**<br>선택적 클라우드 백업 옵션만 제공 (명시적 사용자 동의 필요) |

---

## 🚧 현재 진행 상황
- [x] [PRD](https://github.com/imsang27/HaruDiary/blob/main/docs/PRD.md)
- [x] [기능 사양서](https://github.com/imsang27/HaruDiary/blob/main/docs/%EA%B8%B0%EB%8A%A5%20%EC%82%AC%EC%96%91%EC%84%9C(Func%20Spec).md)
- [x] [Wireframe](https://github.com/imsang27/HaruDiary/blob/main/docs/%ED%99%94%EB%A9%B4%20%EA%B5%AC%EC%84%B1%EB%8F%84(Wireframe).md)
- [x] [API 설계 완료](https://github.com/imsang27/HaruDiary/blob/main/docs/API%20%EC%84%A4%EB%AA%85%EC%84%9C(API%20Spec).md)
- [ ] DB 구조 설계 예정
- [ ] MVP 기능 구현 진행 예정

---

## 🔐 개인정보 및 보안 정책
- 모든 일기/녹음 데이터는 **사용자 로컬 저장소**에만 저장됩니다.
- 클라우드 업로드는 **사용자 동의 시에만 선택적으로 활성화**됩니다.

---

## 🧪 향후 확장 기능 (계획 중)
- [ ] 영상 기록 기능
- [ ] 위치 기반 일기 자동 생성
- [ ] 주간/월간 회고 리포트
- [ ] 챗봇 기반 일기 코치 (대화형 일기 쓰기)
- [ ] 암호화 저장 (예정) 및 앱 내 잠금 기능 지원 예정
- [ ] AES-256 암호화 저장, TLS 기반 전송
- [ ] 사용자 데이터에 대한 접근/삭제 권한 제공

---

## 📝 라이선스
본 프로젝트는 추후 공개 라이선스(MIT/MPL-2.0 등) 채택을 검토 중입니다.

---

## 👤 개발자
[imsang27](https://github.com/imsang27)
