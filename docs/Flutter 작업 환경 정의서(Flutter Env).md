# HaruDiary App - Flutter 기반 작업 환경 정의서 + Python 연동 구조 
---

## 1. 개발 환경 정의 (Flutter 중심)
---

### 시스템 요구 사항
- 운영체제: Windows 10/11 또는 macOS
- Flutter SDK: 3.16.0 이상 권장
- Dart 버전: Flutter와 함께 제공
- Android Studio 또는 VS Code 설치
- Android SDK + iOS Simulator (Xcode, macOS 전용)
- Git 설치

### 명령줄 도구 설치 예시
```bash
# Flutter 설치
git clone https://github.com/flutter/flutter.git -b stable
flutter doctor

# 필요한 플랫폼 지원 도구 설치
flutter config --enable-web
flutter config --enable-windows-desktop
flutter config --enable-macos-desktop
```

---

## 2. 프로젝트 기본 구조 예시
---

```plaintext
📁 haru_diary_app/
├── 📁 lib/                      # Dart 소스코드 (Flutter UI/로직)
│   ├── main.dart
│   ├── screens/
│   ├── services/               # API 호출, 로컬 처리 모듈
│   ├── models/
│   └── widgets/
├── 📁 android/                 # Android 네이티브 설정
├── 📁 ios/                     # iOS 네이티브 설정
├── 📁 web/                     # 웹 앱 설정
├── 📁 assets/                  # 이미지, 아이콘, 오디오 파일
├── 📁 python/                  # Python 백엔드 모듈 연동 (Whisper 등)
│   ├── whisper_worker.py
│   ├── summary_api.py
│   └── requirements.txt
├── 📁 test/                    # 유닛 테스트
├── pubspec.yaml               # Flutter 패키지 의존성
└── README.md
```

---

## 3. 추천 Flutter 패키지 (기능별)
---

### 🎙️ 오디오 녹음 & 재생
- [`flutter_sound`](https://pub.dev/packages/flutter_sound)
- `record`
- `just_audio`

### 🧠 STT 및 요약 연동 (Python 연동용)
- `http`
- `dio` (고급 API 통신용)

### 🧠 로컬 저장 / DB
- `shared_preferences`
- `hive` (가벼운 로컬 DB)
- `isar` (고성능 DB)

### 🎨 UI 구성
- `provider` 또는 `riverpod` (상태관리)
- `flutter_hooks` (React-like 느낌)
- `lottie`, `flutter_animate` (애니메이션)

### 📦 기타
- `permission_handler` (마이크, 저장소 권한)
- `path_provider` (로컬 저장 경로)
- `intl` (시간 포맷 처리)

---

## 4. Python 연동 전략
---

### ✅ 구조
- Flutter ↔️ Python 백엔드(API 형태)
- Python 서버는 FastAPI 또는 Flask로 구성
- Whisper, GPT 요약, 감정 분석은 Python에서 처리

### 📡 통신 방식
| 방향 | 방식 |
|------|------|
| Flutter → Python | HTTP POST (녹음 업로드, 요약 요청 등) |
| Python → Flutter | 응답으로 JSON 결과 반환 (요약, 감정 등) |

### 📁 예시 API 엔드포인트
```http
POST /stt/whisper
POST /summary/gpt
POST /emotion/analyze
GET  /diary/today
```

---

## 5. 예상 실행 흐름 예시
---

1. Flutter에서 녹음된 오디오를 저장
2. Python 서버로 `.wav` 파일 전송
3. Whisper → STT → GPT 요약 → 감정 분석 처리
4. 결과를 JSON으로 받아 Flutter UI에 표시

---

## 6. 보안 고려사항
---

- Python 서버는 로컬 테스트 → 이후 클라우드 배포 (EC2/Firebase Functions 등)
- HTTPS 통신 적용 필요
- 파일 업로드시 크기 제한 + 인증 처리 권장

---

