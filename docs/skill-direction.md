# 스킬 방향

## 목적

- 구현이나 마이그레이션 전에 현재 권위 있는 source owner와 계약 근거를 read-only로 판정한다.

## 유지할 것

- 현재 source evidence를 최종 근거로 둔다.
- 메모리, 이전 요약, task doc, audit note는 routing hint로만 둔다.
- source owner, static caller/UX contract owner, write owner, read owner, doc owner, task owner, migration owner, decision owner를 구분한다.
- backend capability나 command 존재만으로 implementation TODO를 열지 않는다.
- 기존 제품 계약과 UX를 임의로 축소하거나 새로 발명하지 않는다.
- audit-only scope에서는 파일 수정, TODO 전환, 배포 제안, 문서 재구성을 하지 않는다.

## 피할 것

- 일반 코드 변경 scope discipline을 흡수하는 방향. 그 영역은 `justified-change`가 맡는다.
- 코드 구조나 contract test 설계를 흡수하는 방향. 그 영역은 `structure-first`가 맡는다.
- 문서 패키지 재구성이나 current-canon promotion을 흡수하는 방향. 그 영역은 문서/컨텍스트 계열 스킬이 맡는다.
- runtime UI freshness/source-state ownership까지 포함하는 방향. 그 영역은 interactive state 계열 스킬이 맡는다.
- 특정 회사/repo, 이슈 번호, 배포 flow, 브랜치 정책을 shipped skill 본문에 넣는 방향.

## sibling skill 궁합

- `source-owner-audit`: 변경 전에 현재 owner와 evidence를 분류한다.
- `justified-change`: 변경할 때 목표, 직접 영향 범위, 검증 기준을 맞춘다.
- `structure-first`: 코드의 primary flow, decision/write-path owner, contract-focused tests를 정리한다.
- `structure-first-docs`: 문서 패키지의 reader flow, current canon, evidence/history 분리를 정리한다.
- `project-context`: 장기 작업 상태, reference, logs, handoff를 저장소 문서로 유지한다.
- `codex-token-discipline`: 넓은 읽기, 서브에이전트, always-read 지시문 비용을 관리한다.
- `interactive-state-flow`: interactive runtime에서 source state, freshness, async/presentation commit owner를 다룬다.

## 수정 기준

- 반복해서 오해되는 audit 판단 기준만 shipped skill에 추가한다.
- 출력 taxonomy는 유지하되, 특정 조직이나 repo 사례로 좁히지 않는다.
- 예시가 꼭 필요하면 `SKILL.md`에 아주 짧게 넣거나, 조건부로 읽을 수 있는 스킬 패키지 내부 reference로 분리한다.
- 한국어 문서는 영문 base skill의 의미를 보존하되 자연스럽고 직접적으로 쓴다.
- 저장소 운영 문서는 스킬 사용 계약을 대신하지 않는다.
