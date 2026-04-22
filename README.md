# 비행교육원 가동률 극대화를 위한 항공 정비 자재 최적 구매 설정 시스템
---
## 프로젝트 소개
비행교육원의 가동률 극대화를 위한 항공 정비 자재 관리 및 최적 구매 설정 시스템입니다.
기체 4대의 비행시간 및 정비 주기를 관리하고 재고 부족 및 정비 임박 시 자동으로 알림을 생성합니다.

---
## 👥 팀원 및 역할
| 이름 | 역할 | 담당 업무 |
|-----|-----|---------|
| 김재림 | DB | 스키마 설계 및 구축, 외부 시스템 데이터 연동, 데이터 정합성 관리, 쿼리 최적화 |
| 박세은 | 백엔드 | REST API 설계 및 구현, 정비 주기 자동 계산 로직, 알림 자동 생성 로직, 외부 시스템 연동 API |
| 박소진 | 프론트엔드 | UI/UX 설계 (와이어프레임 → 디자인), React 컴포넌트 구현, 백엔드 API 연동, 반응형 및 사용성 최적화 |
<br>
<br>

## 🛠️ 기술 스택
| 구분 | 기술 |
|------|------|
| Frontend | React, JavaScript, Axios |
| Backend | Python, FastAPI |
| Database | MySQL |
| 협업 도구 | Git, GitHub |
---


## 📱 주요 기능
| 기능 | 설명 |
|------|------|
| 메인 대시보드 | 재고현황 / 기체 / 알림판 한눈에 확인 |
| 재고 현황 | 전체 부품 재고 조회 및 상태 확인 |
| 재고 입출고 | 부품 입고 / 출고 처리 및 이력 관리 |
| 기체 관리 | 기체 4대 상태 및 정비 주기 확인 |
| 비행시간 입력 | 비행 후 시간 기록 및 정비주기 자동 계산 |
| 알림판 | 재고 부족 / 정비 임박 자동 알림 생성 |
---

## 📁 프로젝트 구조
```
aviation-maintenance-system/
├── frontend/
│   ├── src/
│   │   ├── components/       ← 재사용 컴포넌트
│   │   ├── pages/            ← 각 페이지 화면
│   │   ├── models/           ← 데이터 구조 정의
│   │   ├── services/         ← API 호출 함수
│   │   └── App.jsx           ← 앱 시작점
│   └── package.json
│
├── backend/
│   ├── routers/              ← API 엔드포인트
│   ├── schemas/              ← 요청/응답 데이터 구조
│   ├── services/             ← 비즈니스 로직
│   ├── models/               ← DB 모델
│   └── main.py               ← 서버 시작점
│
├── database/
│   ├── schema.sql            ← 테이블 생성 스크립트
│   └── seed.sql              ← 초기 데이터 스크립트
│
└── README.md
```

---

## 🗂️ 데이터베이스 구조
| 테이블 | 설명 |
|--------|------|
| aircraft | 기체 정보 |
| flight_logs | 비행시간 기록 |
| parts | 부품 마스터 |
| inventory | 재고 현황 |
| inventory_transactions | 입출고 이력 |
| maintenance_schedule | 정비 주기 |
| alerts | 알림 데이터 |
---

## 🔗 API 목록
| Method | URL | 설명 |
|--------|-----|------|
| GET | /api/aircraft | 기체 목록 조회 |
| GET | /api/aircraft/{id} | 기체 상세 조회 |
| POST | /api/aircraft/{id}/flight-log | 비행시간 입력 |
| GET | /api/inventory | 재고 목록 조회 |
| POST | /api/inventory/transaction 
| 입출고 처리 |
| GET | /api/alerts | 알림 목록 조회 |
| PATCH | /api/alerts/{id}/status 
| 알림 상태 변경 |
---

## ⚙️ 설치 및 실행 방법

### 사전 준비
- Python 3.10 이상
- Node.js 18 이상
- MySQL 8.0 이상

### 1. 저장소 클론
```bash
git clone https://github.com/팀계정/aviation-maintenance-system.git
cd aviation-maintenance-system
```

### 2. 데이터베이스 설정
```bash
mysql -u root -p
source database/schema.sql
source database/seed.sql
```

### 3. 백엔드 실행
```bash
cd backend
pip install -r requirements.txt
uvicorn main:app --reload --port 8000
```

### 4. 프론트엔드 실행
```bash
cd frontend
npm install
npm start
```

### 5. 접속
```
프론트엔드 : http://localhost:3000
백엔드 API : http://localhost:8000
API 문서   : http://localhost:8000/docs
```

---

## 🔒 환경변수 설정
backend 폴더 안에 .env 파일 생성 후 아래 내용 입력
```
DB_HOST=localhost
DB_PORT=3306
DB_USER=root
DB_PASSWORD=비밀번호입력
DB_NAME=aviation_db
```

---

## 🌿 브랜치 전략
```
main                          ← 최종 배포용
└── develop                   ← 통합 개발용
    ├── feature/db-schema     ← DB 담당 작업
    ├── feature/backend-api   ← 백엔드 담당 작업
    └── feature/frontend-ui   ← 프론트엔드 담당 작업
```

---

## ✅ 커밋 메시지 규칙
```
feat     : 새로운 기능 추가
fix      : 버그 수정
design   : UI 변경
refactor : 코드 리팩토링
docs     : 문서 수정
db       : DB 관련 변경

예시)
feat: 재고 부족 알림 자동 생성 기능 추가
fix: 비행시간 입력 시 총합 계산 오류 수정
design: 메인 대시보드 레이아웃 수정
db: inventory 테이블 인덱스 추가
```

---


## 📌 참고사항
- 외부 항공 정비 자재 관리 프로그램 접근 권한 필요
- MySQL 서버 실행 상태에서 백엔드 실행할 것
- API 문서는 백엔드 실행 후 /docs 에서 확인 가능
- .env 파일은 GitHub에 올리지 않음 (보안)
<br>
<br>

## 📅 회의 진행 현황
### 2026-04-22 회의
- 팀원 역할 재분배 확정 (피드백 반영)
  - DB / 백엔드 / 프론트엔드 역할 배분
- 예상 UI/UX 구현 방향 및 활용 데이터 논의 → PPT에 예상 구현도 추가 완료
- README 초안 작성 완료
