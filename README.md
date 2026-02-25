## 📌 프로젝트 소개

- 팀스파르타 내일배움캠프의 실무형 Kotlin & Spring 개발자 양성과정 중 진행된 팀 프로젝트

- 기간 : 2025년 12월 31일(수) ~ 2026년 01월 09일(금) (총 7일)
  
- 주제 : 동시성 이슈 제어를 핵심 과제로, 안정적인 티켓 예매 흐름을 설계하고, 구현한 프로젝트

- 프로젝트 회고 : [✍️ velog](https://velog.io/@bella0/%ED%8B%B0%EC%BC%93%ED%8C%85-%EC%84%9C%EB%B9%84%EC%8A%A4-%ED%8C%80-%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8-%ED%9A%8C%EA%B3%A0)

- 프로젝트 정리본 : [📢 발표 자료](https://www.canva.com/design/DAG9sHM7aI8/3wWEBOgKrxzAWkauwf2PEQ/edit?utm_content=DAG9sHM7aI8&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton)


## 🎯 프로젝트 목표
- 동시성 제어
- Cache을 이용한 조회 성능 개선
- 인덱스를 통한 성능 최적화
- 배포와 CI/CD

## ✅ 주요 기능

<details>
  <summary><strong>1️⃣ 사용자 & 인증</strong></summary>
  
  - 회원 가입 / 로그인
  - JWT 토큰
  - 권한 기반 접근 제어 (ADMIN/USER)
</details>
<details>
  <summary><strong>2️⃣ 공연</strong></summary>
  
  - 공연 생성 및 삭제
  - 공연 목록 조회 / 상세 조회
  - 공연별 좌석 금액 등록
  - 인기 검색어 조회
</details>
<details>
  <summary><strong>3️⃣ 예매</strong></summary>
  
  - 공연 예매
  - 예매 취소
  - 회원별 예매 정보
  - 예매 상세 정보
</details>
<details>
  <summary><strong>4️⃣ 좋아요</strong></summary>
    
  - 공연 좋아요 및 취소
  - 공연 좋아요 수 조회
</details>
<details>
  <summary><strong>5️⃣ 좌석</strong></summary>
    
  - 예매 가능한 좌석 목록 조회
  - 좌석 등급별 남은 좌석 수 조회
  - 공연별 좌석 금액 목록 조회
  - 공연별 좌석 금액 단건 조회
</details>


## 👩🏻‍💻 담당 기능

### ① 좋아요

기능:
- 공연 좋아요 및 취소
- 공연 좋아요 수 조회

구현 포인트:
- unique 제약을 통한 중복 좋아요 방지

### ② 자리 예매 기능 동시성 제어

기능 설명:
- Redisson 분산 락을 통한 동시성 제어
- DB 비관적 락을 통한 최종 정합성 보장

구현 포인트:
- 분산 락을 통한 부하 감소와 비관적 락을 통한 정합성 보장으로 성능과 안정성을 동시에 확보

### ③ 조회 성능 개선

개선 포인트:
- `show_id, seat_type, seat_number` 복합 인덱스를 통한 특정 좌석 조회 최적화
- `show_id, seat_status, seat_type` 복합 인덱스를 통한 좌석 상태 조회 최적화
- `payment_status, is_canceled, created_at` 복합 인덱스를 통한 만료된 예매 조회 최적화

성능 개선 자료 문서:
- [좌석 조회 개선](https://www.notion.so/teamsparta/2e22dc3ef51480ae9e3fd15ba3a0f40e?source=copy_link)
- [만료 예매 조회 개선](https://www.notion.so/teamsparta/2e22dc3ef51480bb9b3bdb1e2ae9f708?source=copy_link)


## ⚙️ 설계 문서

### ✏️ 와이어 프레임

https://www.figma.com/board/4TIZPWwvOBLWN8NkqFvX5j/%EC%B9%A0%EC%B9%A0%ED%95%98%EC%A1%B0_7%EC%A1%B0?node-id=0-1&t=RWTxFMCGbn9iuI9n-1

### 🗂 데이터베이스 ERD

<img width="2049" height="727" alt="image" src="https://github.com/user-attachments/assets/2f6a250c-eff1-4be2-9e13-a3e127bffe74" />

[테이블 명세서 By Notion](https://www.notion.so/teamsparta/2cb2dc3ef514816a8546d268e904f755)

### 📡 API 명세서

[API 명세서 By Notion](https://www.notion.so/teamsparta/2cb2dc3ef51481568c75c154542b6637?v=2cb2dc3ef514816fa8bb000c5bdd0511)

### 🏗️ 아키텍처 구조

<img width="795" height="538" alt="아키텍쳐(다크모드)" src="https://github.com/user-attachments/assets/a4a6c05f-bf08-4072-91c3-4a9bf64bdf39 #gh-dark-mode-only" />

<img width="795" height="555" alt="아키텍쳐" src="https://github.com/user-attachments/assets/224094c0-a735-41d5-bce4-62d3ef91e6cf #gh-light-mode-only" />


## 기술 스택
- Language : Java 17
- SpringBoot v3.5.9
- Postman
- DB : MySQL
- ORM : Spring Data JPA
- Docker
- AWS
- POSTMAN
- 단위 테스트 (JUnit)
