# 홍승용 (Seungyong Hong)

**Full-Stack Engineer** | jesse1231@naver.com | [GitHub](https://github.com/isanghaessi) | [Blog](https://blog.naver.com/isanghae_ssi)

---

## 🚀 Introduce
- **Java/Spring 기반 백엔드 엔지니어**로, 일 평균 약 3만 건의 고객 문의를 처리하는 네이버 고객상담 플랫폼의 시스템 개발 및 운영을 담당하고 있습니다.
- **성능 최적화 전문가**: 데드락 해결, 슬로우 쿼리 튜닝 등을 통해 시스템 안정성과 효율을 극대화한 경험이 있습니다.
- **인프라**: **CKA(Certified Kubernetes Administrator)** 자격을 보유하고 있으며, **Ansible**을 통한 전통적인 VM 서버 관리 경험이 있습니다. 
- **오픈소스 기여**: **Micrometer** 등 글로벌 오픈소스에 직접 기여하며 기술의 깊이를 더하고 있습니다.

---

## 🛠 Skills
- **Backend**: Java, Spring Boot, Spring Batch, JPA, MyBatis
- **Infra**: Kubernetes, Ansible, Nginx, Jenkins, GitHub Actions
- **Database**: MySQL, Oracle

---

## 💼 Experience
### N Tech Service (네이버 계열사) | 백엔드 엔지니어
*2022.02 ~ 현재*
- 네이버 전 서비스 고객 문의 처리 플랫폼 개발 및 운영
- 레거시 시스템 현대화 및 인프라 최적화 주도

---

## 🏆 Key Projects
### 1. 네이버 메일 고객 상담 시스템 리뉴얼
- **리버스 엔지니어링**을 통해 레거시 분석 스펙 확정과 최신 프레임워크와 코드로 새로 작성.
- IDC 이중화시 비용 절감을 위한 데이터베이스 전환 **Oracle → MySQL** 성공.
- Service 레이어 **TC Line Coverage 100%** 달성으로 코드 품질 및 유지보수성 확보.

### 2. SMS 발송 시스템 성능 최적화
- **데드락 및 타임아웃 문제 해결**: 인덱스 최적화 및 배치 아키텍처(Tasklet → Chunk) 개선.
- **중복 발송 문제 해결**: 트랜잭션 범위를 재정의하여 발송 신뢰성 확보.

### 3. 웹서버 전환을 통한 인프라 최적화
- **Apache → Nginx 전환**: Event-driven 아키텍처 기반 대용량 처리 성능 확보와 보안 취약점 패치 지옥 탈출.
- **k8s 사이드카 패턴 적용**: nginx의 로그 rotate를 위한 사이드카 컨테이너 구현.
- **성능 최적화**: 정적 자원 직접 서빙 설정과 액세스 로그 비활성화로 컨테이너 부하 경감.

### 4. 배치 잡 중복 실행 방지
- **비동기로 동작하는 Job**: 비동기로 동작하여 겹칠 수 있는 Job을 위한 `JobExecutionListener` 구현.

### 5. 슬로우 쿼리 튜닝
- **슬로우 쿼리 튜닝**: SQL 실행 계획 최적화를 통한 통계 조회 API 성능 대폭 향상.

---

## 🌐 Open Source

### 1. Micrometer — `@Observed` 애너테이션 기반 KeyValue 동적 태깅 기능 구현
- **신규 기능 추가**: `@Observed` 애너테이션에 동적 key-value를 추가할 수 있는 기능 개발. 

---

## 🪪Certification

- **Certified Kubernetes Administrator** (CKA)

---

## 🧩 Education

- 네이버 부스트캠프 6기 수료 (2021)
- 인천대학교 임베디시스템공학과 졸업 (2025 ~ 2021)
