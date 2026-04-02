# 홍승용 (Seungyong Hong)

**Introduce**

Java/Spring 기반 백엔드 엔지니어로서 일 평균 약 3만 건의 고객 문의를 처리하는 네이버의 고객상담 플랫폼의 운영과 개발을 담당했습니다. 레거시 개선, 배치 안정화, 인프라 전환을 성공적으로 이끈 경험이 있습니다.   
전통적인 VM 방식(Ansible)과 Managed Kubernetes로 구성된 인프라를 운영했습니다. CKA(Certified Kubernetes Administrator) 자격을 보유하고 있으며, Kubernetes 환경에서의 애플리케이션 배포·운영·트러블슈팅에 대한 탄탄한 인프라 이해도를 가지고 있습니다.   
사용하고 있는 오픈소스(Spring, Micrometer)에 직접 기여함으로써 사용하는 언어와 기술의 이해도를 높이고 있습니다.   

---

## Contact

- **Email** : jesse1231@naver.com
- **GitHub** : [github.com/isanghaessi](https://github.com/isanghaessi)
- **Blog** : [blog.naver.com/isanghae_ssi](https://blog.naver.com/isanghae_ssi)

---

## Skills

| 분류 | 기술 |
|---|---|
| **Language** | Java, JavaScript/TypeScript |
| **Backend** | Spring Boot, Spring Web, Spring Batch, MyBatis |
| **Frontend** | React, Vue |
| **Infra · DevOps** | Kubernetes, Docker, GitHub Actions, Jenkins, Ansible, Apache, Nginx |
| **Database** | MySQL, Oracle |

---

## Experience

### N Tech Service (네이버 계열사)

**백엔드 엔지니어** | 2022.02 ~ 현재

네이버 서비스를 이용하는 수천만 사용자의 고객 문의를 처리하는 **고객상담 플랫폼(콜·메일·채팅)**의 풀스택 개발과 운영을 담당하고 있습니다.

---

## Projects

### 1. 네이버 메일 고객 상담 시스템 리뉴얼 — 리버스 엔지니어링 기반 재구축

- **Situation**: 네이버 메일 고객상담 시스템이 오랜 기간 운영되면서 시스템이 노후화된 상태였습니다. 시스템이 오랫동안 유지·보수되면서 별도의 스펙이 모호하고, 코드 베이스의 복잡도가 높아 기능 추가·수정 시 사이드 이펙트 파악이 어려워서 유지·보수 비용이 지속적으로 증가하고 있었습니다. 코드 베이스를 처음부터 새로 만들어 리뉴얼하면서 IDC 이중화를 위해 DB를 Oracle에서 MySQL로 전환하는 작업도 병행했습니다.

- **Task**:
  - 노후화된 기술 스택을 최신 기술로 마이그레이션해야 했습니다.
  - 기존 스펙을 **리버스 엔지니어링**을 통해 분석하고 운영측과 협의하여 새로운 스펙을 확정해야 했습니다.
  - 정의된 **스펙 문서화**를 위하여 Service 레이어의 TC를 **LineCoverage 100%**로 작성해야 했습니다.
  - 비용이 높아 IDC 이중화가 어려운 Oracle을 MySQL로 전환해야 했습니다.

- **Action**:
  - 기존 레거시 기능들을 화면 단위 서브 태스크로 나누어 **리버스 엔지니어링**을 통해 분석하고, Zeppelin을 통해서 운영측과 스펙을 정의하였습니다.
    - 총 화면 21개 중 **10개(약 48%)**를 담당했습니다.
  - 노후화된 기술 스택을 최신 기술로 마이그레이션 했습니다.
    - 레거시: Spring, Tomcat, Apache, JSP
    - 재구축: **Spring Boot**, **Embedded Tomcat**, **Nginx**, **React**, **TypeScript**
  - Oracle 문법으로 작성된 SQL들을 모두 MySQL로 재작성했습니다.
    - 총 SQL 파일 75개 중 **33개(약 44%)**를 담당했습니다.
  - Service 레이어 클래스들에 한해 TC를 모두 작성하고 **Line Coverage 100%**를 달성했습니다.
    - 총 61개의 클래스 중 **26개(약 43%)**를 담당했습니다.

- **Result**:
  - 레거시 시스템을 신규 아키텍처로 전환하고, Oracle → MySQL DB 전환까지 완료해 IDC 이중화 가능한 운영 기반을 확보했습니다.
  - 리버스 엔지니어링을 통한 스펙 정의와 TC를 통한 문서화로 프로젝트 유지·보수 용이성을 확보했습니다.

---

### 2. SMS 발송 시스템 전면 개편 — 사내 SMS 발송 서비스 전환 및 배치 아키텍처 리팩토링

- **Situation**:
  - 기존에 사용하던 사내 SMS 발송 서비스가 deprecated되어 신규 서비스로의 전환이 필요했습니다.
  - 전환 후 운영 중에 **타임아웃·데드락** 오류가 특정 시간대에 발생하고, **1건의 발송 실패 시 전체 배치가 롤백되어 처음부터 다시 발송**되는 치명적인 구조적 결함이 있어서 핫픽스가 필요했습니다.

- **Task**: 
  - deprecated된 사내 SMS 발송 서비스를 리뉴얼된 SMS 발송 서비스로 전환해야 했습니다.
  - 발송 요청 책임만 가지고 있던 스펙이 발송 확인 책임이 추가되어 발송 확인 여부를 확인해야 했습니다.
  - 운영 중 발생한 특정 시간대에 타임아웃·데드락 오류가 나는 버그를 수정해야 했습니다.
  - 운영 중 발생한 1건의 오류 발생 시 처리 중인 데이터가 롤백되어 SMS가 여러 번 다시 발송되는 버그를 수정해야 했습니다.

- **Action**:
  - 새로 리뉴얼된 SMS 발송 서비스의 API 스펙을 분석하여 기존 프로젝트 내의 스펙에 맞도록 설계하였습니다.
  - SMS 발송 여부를 확인하는 **발송 확인** 잡을 추가하였습니다.
  - 특정 시간에 발생하는 **타임아웃·데드락** 버그를 해결하였습니다.
    - **SMS 발송 요청(INSERT)**과 **SMS 발송 상태 업데이트(UPDATE)**이 동시에 실행되면서 데드락이 발생하였습니다.
    - 트랜잭션 시간을 짧게 가지기 위해서 배치 스텝 기반을 **Tasklet** → **Chunk**으로 수정하였습니다.
    - SMS 발송 상태 업데이트 시 사용된 컬럼에 인덱스를 추가하여 MySQL **InnoDB의 락을 적게** 잡도록 수정하였습니다.
  - 잘못 사용된 `@Transactional` 어노테이션을 제거하여 1건 실패 시 SMS가 모두 재발송되는 오류를 해결하였습니다.

- **Result**:
  - deprecated된 사내 SMS 서비스에서 신규 서비스로 전환을 완료했습니다.
  - 전환 후 발생한 오류(타임아웃, 전체 실패와 재시도)를 해결하였습니다.

---

### 3. 고객상담시스템 웹서버 인프라 전환 (Apache → Nginx)

- **Situation**: 네이버 고객상담시스템을 구성하는 **10개 이상의 컴포넌트**가 Apache HTTP Server를 웹서버로 사용하고 있었습니다. Apache에서 빈번하게 발생하는 보안 취약점(CVE)으로 인해 긴급 패치가 반복되었고, 이에 대한 운영 부담이 지속적으로 증가하고 있었습니다.

- **Task**: 고객상담시스템 전체 서비스의 웹서버를 Apache에서 Nginx 최신 버전으로 일괄 전환해야 했습니다.

- **Action**:
  - **10개** 이상의 컴포넌트의 Apache 설정을 분석하고, Nginx 설정으로 1:1 변환하여 작성했습니다.
  - **Kubernetes**를 사용하는 컴포넌트의 **베이스 이미지**를 Apache에서 Nginx 기반으로 변경하여 빌드했습니다.
  - 각 프로젝트별로 **Ansible**로 관리되는 서버 환경을 Nginx 기반으로 변경하여 적용했습니다. 문제가 발생할 시를 대비하여 **롤백이 가능한 구조**를 중간에 두어 대비했습니다.
  - Tomcat 연동을 **AJP**에서 **HTTP**로 변경하였습니다.
  - 컴포넌트별 순차적 전환 및 롤백 전략을 수립했습니다.

- **Result**:
  - **10개** 이상의 서비스에 대해 Nginx 전환을 완료했습니다.
  - Apache 관련 CVE 긴급 패치 운영 부담을 제거했습니다.

---

## Open Source Contribution

### Micrometer — `@Observed` 애너테이션 기반 KeyValue 태깅 기능 구현

**[PR #6667](https://github.com/micrometer-metrics/micrometer/pull/6667)** | Merged, 2025.10 | +1,323 / -12, 15 files changed

- **Situation**: Micrometer의 `@Observed` 애너테이션은 low cardinality key-value만 상수로 지정할 수 있었습니다. 메서드 파라미터를 기반으로 high·low cardinality key-value를 동적으로 추가하려면, AOP 방식을 포기하고 `Observation.createNotStarted()`를 직접 호출하는 장황한 보일러플레이트 코드를 작성해야 했습니다. ([Issue #5826](https://github.com/micrometer-metrics/micrometer/issues/5826))

- **Task**: `@Timed`·`@Counted`에서 `@MeterTag`가 제공하는 파라미터 기반 태깅 경험을, `@Observed` 애너테이션에서도 동일하게 사용할 수 있도록 신규 애너테이션과 AOP 처리기를 설계·구현해야 했습니다.

- **Action**:
  - `@ObservedKeyValueTag`·`@ObservedKeyValueTags` 애너테이션을 설계하여, 메서드 파라미터에 선언적으로 key-value를 바인딩할 수 있도록 구현했습니다.
  - `ObservedKeyValueTagAnnotationHandler`를 구현하여, 파라미터 스캔 → 값 평가(static·`ValueResolver`·`ValueExpressionResolver`) → `Observation.Context`에 key-value 주입까지의 전체 파이프라인을 AOP로 처리하도록 했습니다.
  - `ObservedAspect`를 확장하여, 핸들러 주입 시에만 기능이 활성화되는 방식으로 기존 코드에 대한 하위 호환성을 보장했습니다.
  - Micrometer 핵심 메인테이너(@jonatan-ivanov, @shakuzen)와의 설계 논의에서, `AnnotationHandler`의 타입 파라미터 한계로 인한 다운캐스팅 vs 새로운 추상화(`validToAdd`) 도입에 대해 기술적 트레이드오프를 분석하고 합의를 이끌어냈습니다.

- **Result**:
  - Micrometer 메인 브랜치 머지(**코어 메인테이너 2인 승인**)로 기능이 공식 API로 채택되었습니다.
  - @Observed에서 파라미터 기반 태깅을 선언형으로 지원해 AOP 유지 + 보일러플레이트 제거를 동시에 달성했습니다.
  - 해당 기능의 설계 과정과 기술적 의사결정을 [기술 블로그](https://blog.naver.com/isanghae_ssi)에 상세히 기록했습니다.

---

## Certification

| 자격증 | 발급기관 | 취득일 |
|---|---|---|
| **[CKA (Certified Kubernetes Administrator)](https://www.credly.com/badges/b494965e-8043-4381-b3a2-934ff9b72517/public_url)** | The Linux Foundation · CNCF | 2026.03 |

---

## Education

| 기간 | 학교 · 과정 | 전공 · 내용 |
|---|---|---|
| 2021 | 네이버 부스트캠프 6기 | 웹·모바일 |
| 2015 ~ 2021 | 인천대학교 | 임베디드시스템공학과 |
