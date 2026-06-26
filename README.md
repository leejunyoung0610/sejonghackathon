# 세종대 공학인증(ABEEK) 졸업요건 판정 시스템

세종대학교 공과대학 **공학인증(ABEEK)** 졸업요건을 자동으로 판정하는 해커톤 프로젝트입니다.  
학과·입학년도별 교과과정·인증 규칙을 DB 시드로 관리하고, 이수 과목 목록을 입력하면 학점·필수과목·설계이수·교양 인증을 한 번에 검증합니다.

**개발 기간:** 2026 세종 해커톤  
**역할:** 백엔드(ABEEK 판정 엔진·시드 데이터)·인프라·프론트 API 연동

## 저장소

| 구분 | 저장소 | 스택 |
|------|--------|------|
| 백엔드 | [sejonghackathon-backend](https://github.com/leejunyoung0610/sejonghackathon-backend) | Spring Boot 3, JPA, MySQL |
| 프론트 | [sejonghackathon-front](https://github.com/leejunyoung0610/sejonghackathon-front) | React, Vite, TypeScript |
| 인프라 | [sejonghackathon-infra](https://github.com/leejunyoung0610/sejonghackathon-infra) | Docker Compose, MySQL 8 |

## 주요 기능

- **ABEEK 판정 API** — `POST /api/evaluate/abeek` (학점·전공필수·BSM/MSC·교양·설계이수)
- **학과별 시드** — 13+ 학과, 2021~2026 교과과정·인증 규칙 SQL 시드
- **과목명 매칭** — alias, fuzzy, 이수구분 fallback, 교양 인증선택(3영역 2영역)
- **유리한 규정** — 입학년도 vs 졸업년도 중 학생에게 유리한 학점 요건 적용
- **설계이수 검증** — basic → element → capstone 순서, capstone 택1 제한

## 로컬 실행

```bash
# DB
cd infra && docker compose up -d db

# 백엔드 (8001)
cd backend && ./gradlew bootRun

# 프론트 (5173)
cd front && npm install && npm run dev
```

## 기술 하이라이트

- Java로 ABEEK 판정 엔진 포팅 (과목 매칭, 설계 시퀀스, 교양 카탈로그)
- Docker initdb로 학과 시드 자동 적재 (utf8mb4)
- MSC/BSM 학과별 기필 fallback, CORS LAN 개발 지원

## 작성자

[leejunyoung0610](https://github.com/leejunyoung0610)
