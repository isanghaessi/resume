# 홍승용 (Seungyong Hong)

## Contact
- **Email** : jesse1231@naver.com
- **GitHub** : [github.com/isanghaessi](https://github.com/isanghaessi)
- **Blog** : [blog.naver.com/isanghae_ssi](https://blog.naver.com/isanghae_ssi)

---

## Experience

### N Tech Service (네이버 계열사)
**풀스택 엔지니어** | 2022.02 ~ 현재

네이버 서비스를 이용하는 수천만 사용자의 고객 문의를 처리하는 **고객상담 플랫폼(콜·메일·채팅)**의 풀스택 개발과 운영을 담당하고 있습니다.

---

## Projects

### 1. 네이버 메일 고객 상담 시스템 리뉴얼 — 리버스 엔지니어링 기반 재구축

- **Result**:
  - 신규 아키텍처 및 MySQL 전환 완료로 IDC 이중화 운영 기반 확보.
  - 리버스 엔지니어링을 통한 스펙 문서화로 유지·보수 비용 절감 및 인수인계 용이성 확보.

- **Situation**: 
  - 네이버 메일 고객상담 시스템이 오랜 기간 운영되면서 시스템이 노후화된 상태. 
  - 스펙이 모호하고, 코드 베이스의 복잡도가 높아 유지·보수 비용이 지속적으로 증가.
  - IDC 이중화를 위해 DB를 Oracle에서 MySQL로 전환 필요.

- **Task**:
  - 노후화된 기술 스택 마이그레이션 및 기존 스펙의 **리버스 엔지니어링** 기반 분석.
  - 정의된 **스펙 문서화**를 위해 Service 레이어 TC **LineCoverage 100%** 달성.
  - 비용 효율화를 위한 Oracle → MySQL DB 전환.

- **Action**:
  - 기존 레거시 기능들을 화면 단위 서브 태스크로 나누어 분석하고, 운영측과 스펙 재정의 (화면 21개 중 10개 담당).
  - 기술 스택 현대화: Spring/Tomcat/Apache/JSP → **Spring Boot/Nginx/React/TypeScript**.
  - SQL 재작성: Oracle 문법 SQL 75개 중 33개를 MySQL 문법으로 재작성.
  - 품질 확보: Service 레이어 61개 클래스 중 26개에 대해 TC 작성 및 **Coverage 100%** 달성.

---

### 2. SMS 발송 시스템 성능 최적화 — 데드락 해소 및 배치 아키텍처 리팩토링

- **Result**:
  - 특정 시간대와 간헐적 장애(데드락/타임아웃) 0건 달성.
  - 중복 발송 문제를 해결하여 시스템 신뢰성 달성.

- **Situation**:
  - 신규 SMS 발송 서비스 전환 후 운영 중 **타임아웃·데드락** 오류가 특정 시간대에 빈번하게 발생.
  - 1건의 발송 실패 시 전체 배치가 롤백되어 **중복 발송**되는 구조적 결함 존재.

- **Task**: 
  - 특정 시간대 타임아웃·데드락 오류 근본 원인 해결.
  - 배치 아키텍처 개선을 통한 부분 실패 허용 및 중복 발송 방지.

- **Action**:
  - **데드락 해결**: `INSERT`(발송 요청)와 `UPDATE`(상태 갱신) 충돌 분석. 업데이트 컬럼에 인덱스를 추가하여 MySQL **InnoDB 갭 락(Gap Lock)** 범위를 최소화.
  - **아키텍처 리팩토링**: 트랜잭션 범위를 좁히기 위해 배치 스텝을 **Tasklet → Chunk** 기반으로 수정.
  - **트랜잭션 최적화**: 오용된 `@Transactional` 제거로 1건 실패 시 전체 롤백 방지 및 처리 성능 향상.

---

### 3. 웹서버 전환을 통한 인프라 최적화 - Apache → Nginx

- **Result**:
  - 인프라 보안 강화와 k8s 최적화.
  - 응답 속도 향상.
  - 디버깅 환경 개선.

- **Situation**: 
  - 10여 개 서비스의 Apache 기반 인프라가 보안 취약점 대응 및 운영 효율 면에서 한계 노출. 
  - 클라우드 네이티브(K8s) 환경에 적합한 가볍고 효율적인 웹서버 필요.

- **Task**: 웹서버 인프라 전면 현대화 및 Kubernetes 환경 최적화.

- **Action**:
  - **기술적 의사결정**: **빈번한 보안 취약점 패치**로 인한 운영 부담을 제거하고, **Event Driven** 방식으로 메모리 사용이 일정한 nginx가 **k8s** 환경에서 `OOM`발생을 줄일 수 있음.
  - **성능 개선**: 정적 자원 직접 서빙 설정으로 WAS(Tomcat) 부하 경감.
  - **디버깅 환경 개선**: 정적 자원의 경우 로그를 찍지 않도록 설정하여 디버깅에 용이하도록 설정.
  - **안정적 전환**: 전통적 VM의 경우, 중간에 롤백 가능한 단계를 `Ansible`로 관리하여 전환.

---

### 4. 배치 잡 중복 실행 방지 - 커스텀 JobExecutionListener

- **Result**:
  - **리스너가 적용된 Job은 더이상 중복 실행되지 않음**.

- **Situation**: 오래 걸리는 **Job이 중복으로 실행**되어 오류 발생.

- **Task**:
  - 중복 실행 방지가 필요한 비즈니스 로직을 가지고 있는 Job에 대하여 적용할 수 있는 `JobExecutionListener` 작성.

- **Action**:
  - **ConcurrentHashMap**: `ConcurrentHashMap`을 활용하여 중복 실행 방지하는 `JobExecutionListener` 작성.
  - **기술적 의사 결정**: 잡을 중지하는 세가지 방법(`JobOperator`, `Exception`, `JobStatus`) 중에서 `Exception`을 통해 잡을 중지하도록 결정.

---

### 5. 슬로우 쿼리 튜닝 - 통합모니터링 시스템 성능 최적화

- **Result**:
  - 통계 조회 SQL 실행 시간 **10s에서 3s로** 단축.

- **Situation**: 네이버 서비스(블로그·카페 등)의 어뷰징 탐지 플랫폼(uMON)에서 통계 조회 API의 **슬로우 쿼리** 발생.

- **Task**:
  - 통계 조회 SQL 실행 시간 단축.

- **Action**:
  - **SQL 실행 계획 분석**: `EXPLAIN` 분석을 통해 옵티마이저의 잘못된 쿼리 계획 식별.
  - **쿼리 튜닝**: **데이터가 상대적으로 적은 테이블을 드라이빙 테이블로 사용**하고, **인덱스가 적절히 사용되는지 실행 계획을 비교**하여 힌트를 주어 실행 계획 최적화.

## Open Source Contribution

### Micrometer — `@Observed` 애너테이션 기반 KeyValue 동적 태깅 기능 구현
**[PR #6667](https://github.com/micrometer-metrics/micrometer/pull/6667)** **([Issue #5826](https://github.com/micrometer-metrics/micrometer/issues/5826))** | Merged, 2025.10

- **Result**:
  - Micrometer 프로젝트에 머지(**코어 메인테이너 2인 승인**)되어 기능이 공식 API로 채택.
  - @Observed에서 파라미터 기반 태깅을 선언형으로 지원해 AOP 유지 + 보일러플레이트 제거를 동시에 달성.

- **Situation**: 
  - 메서드 파라미터를 기반으로 high·low cardinality key-value를 동적으로 추가하려면, **AOP 방식을 포기해야 함**. 
  - Micrometer의 `@Observed` 애너테이션은 low cardinality key-value만 상수로 지정 가능.

- **Task**: 
  - `@Observed` 애너테이션에 동적 key-value를 추가할 수 있도록 신규 애너테이션과 AOP 처리기를 설계·구현 필요.

- **Action**:
  - 신규 애너테이션(`@ObservedKeyValueTag`·`@ObservedKeyValueTags`)을 설계하여, **메서드 파라미터에 선언적으로 key-value를 바인딩**할 수 있도록 구현.
  - `ObservedKeyValueTagAnnotationHandler`를 구현하여, 신규 어노테이션을 처리하는 AOP 파이프라인을 구현.
  - `ObservedAspect`를 확장하여, **핸들러 주입 시에만 기능이 활성화되는 방식으로 기존 코드에 대한 하위 호환성을 보장**했습니다.
  - 다운캐스팅 vs 새로운 추상화(`validToAdd`) 도입에 대해 기술적 트레이드오프를 분석하고 **메인테이너와의 합의**.

---

## Skills

- **Language**: Java, JavaScript/TypeScript
- **Backend**: Spring Boot, Spring Web, Spring Batch, MyBatis
- **Infra · DevOps**: Kubernetes (CKA), Docker, GitHub Actions, Jenkins, Ansible, Nginx
- **Database**: MySQL, Oracle

---

## Certifications

| 자격증 | 발급기관 | 취득일 |
|---|---|---|
| **[CKA (Certified Kubernetes Administrator)](https://www.credly.com/badges/b494965e-8043-4381-b3a2-934ff9b72517/public_url)** | The Linux Foundation · CNCF | 2026.03 |

---

## Education


| 기간 | 학교 · 과정 | 전공 · 내용 |
|---|---|---|
| 2021 | 네이버 부스트캠프 6기 | 웹·모바일 |
| 2015 ~ 2021 | 인천대학교 | 임베디드시스템공학과 |
