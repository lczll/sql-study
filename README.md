# SQL 쿼리 학습 플랫폼

<p align="center">
  <img src="docs/screenshot-learning.png" alt="학습 모드" width="100%">
</p>

53만 건 이상의 실제 상가(상권) 데이터를 활용한 **인터랙티브 SQL 학습 웹 애플리케이션**입니다.

---

## 주요 특징

| 특징 | 설명 |
|------|------|
| **완전한 브라우저 실행** | 서버 없이 브라우저에서 SQL 실행 (sql.js WebAssembly) |
| **실제 데이터** | 소상공인시장진흥공단 상가정보 536,115건 |
| **단계별 학습** | 16개 실무 문제를 6단계 난이도로 제공 |
| **VS Code 에디터** | Monaco Editor 기반 SQL 편집 환경 |

---

## 스크린샷

### 학습 모드
<p align="center">
  <img src="docs/screenshot-learning.png" alt="학습 모드" width="100%">
</p>

### 연습 모드
<p align="center">
  <img src="docs/screenshot-practice.png" alt="연습 모드" width="100%">
</p>

---

## 빠른 시작

### 방법 1: 브라우저 DB 모드 (가장 간단)

```bash
git clone https://github.com/Cloud-Linuxer/sql-study.git
cd sql-study
npm install
npm run dev
```

> **Note**: `public/data/store_data.csv` 파일 필요 ([공공데이터포털](https://www.data.go.kr/data/15083033/fileData.do)에서 다운로드)

### 방법 2: Docker Compose (권장)

```bash
git clone https://github.com/Cloud-Linuxer/sql-study.git
cd sql-study
docker-compose up -d
```

- Frontend: http://localhost:5173
- API: http://localhost:3001
- MySQL: localhost:3306 (root/practice123)

### 방법 3: MySQL API 모드

```bash
# 1. MySQL 데이터베이스 생성
mysql -u root -p -e "CREATE DATABASE naver_financial CHARACTER SET utf8mb4;"

# 2. 환경 설정
cd server && cp .env.example .env
# .env 파일에서 DB_PASSWORD 설정

# 3. 서버 실행
npm install && npm start

# 4. 프론트엔드 (새 터미널)
cd .. && npm install && npm run dev
```

---

## 기술 스택

| 영역 | 기술 |
|------|------|
| Frontend | React 18, Vite, Tailwind CSS, Monaco Editor |
| Backend | Express.js, MySQL, Passport (Google OAuth) |
| Browser DB | sql.js (WebAssembly SQLite), PapaParse |

---

## 프로젝트 구조

```
sql-study/
├── src/
│   ├── components/     # React 컴포넌트
│   ├── hooks/          # 커스텀 훅 (useDatabase, useDatabaseAPI)
│   ├── data/           # 예제 쿼리, 퀴즈 문제
│   └── utils/          # 유틸리티 함수
├── server/             # Express API 서버
├── docker/             # Docker 초기화 스크립트
├── docs/               # 스크린샷
└── public/data/        # CSV 데이터 (별도 다운로드)
```

---

## 코드 품질 분석

| 영역 | 평가 | 비고 |
|------|------|------|
| 코드 품질 | B+ | 구조 좋음, console.log 정리 필요 |
| 보안 | B+ | SQL Injection 방어 우수 |
| 성능 | B | 기본 최적화 적용됨 |
| 아키텍처 | A- | 명확한 분리, 확장 가능 |

### 보안 특징
- SELECT/WITH/DESC/SHOW 쿼리만 허용
- 시스템 테이블 접근 차단
- 위험 키워드 (DROP, DELETE 등) 차단
- 자동 LIMIT 100 적용

---

## 라이선스

MIT License

---

## 기여

버그 리포트, 기능 제안, PR 환영합니다!

[GitHub Issues](https://github.com/Cloud-Linuxer/sql-study/issues)
