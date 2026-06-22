# Skill: Source Owner Audit (한국어 페어)

> 영문 기본 문서: `SKILL.md`

## 목적

구현, 마이그레이션, 라우팅 변경 전에 현재 권위 있는 source owner를 판정한다.

이 스킬은 감사 스킬이다. 기본값은 read-only 근거 수집과 disposition 분류다. 사용자가 명시적으로 범위를 넓히지 않았다면 감사 결과를 코드 수정, TODO 소유권, 문서 마이그레이션, 배포 단계, 넓은 정리 작업으로 바꾸지 않는다.

## 핵심 기준

- 현재 소스가 메모리, 이전 요약, 과거 작업 노트, stale 문서, 추론된 parity보다 우선한다.
- route, entrypoint, command, schema, API client, config, test, runbook, owner 문서, 사용자에게 보이는 동작 같은 구체적인 owner surface에서 시작한다.
- 소유권을 증명하는 데 필요한 가장 작은 소스 경로만 추적한다.
- 확인된 사실과 추론을 분리한다.
- 구현을 쉽게 만들려고 기존 제품 계약이나 UX를 새로 발명하거나 단순화하거나 축소하지 않는다.
- 소스가 정책/제품 선택을 열어두고 있다면 조용히 선택하지 말고 decision owner를 이름 붙인다.

## 실행 흐름

1. **감사 질문과 경계를 고정한다.**
   - 질문을 이름 붙인다: source owner, contract owner, static caller/UX contract owner, parity gap, stale-summary revalidation, migration owner, possible later implementation을 위한 evidence sufficiency.
   - 닫힌 범위를 이름 붙인다: no edits, no TODO conversion, no doc restructuring, no deploy, no live mutation, no broad cleanup.

2. **후보 surface를 좁게 수집한다.**
   - 사용자가 지목한 surface에서 먼저 시작한다.
   - repo-wide scan보다 path-specific read를 선호한다.
   - dirty worktree에서는 로컬 변경이 답에 영향을 줄 수 있으면 status와 작은 path-scoped diff부터 본다.
   - cross-repo 또는 cross-surface 작업에서는 각 후보 owner를 독립적으로 확인한다.

3. **소유권을 추적한다.**
   - 필요할 때 caller -> adapter/client/helper -> route/API -> command/service -> persistence/schema/test owner를 따라간다.
   - source owner, static caller/UX contract owner, write owner, read owner, doc owner, task owner, migration owner, decision owner를 구분한다.
   - current production owner와 legacy, fallback, compatibility, generated, copied, evidence-only surface를 구분한다.
   - backend capability나 command 존재를 caller intent, access policy, product approval로 취급하지 않는다.

4. **메모리가 아니라 owner와 비교한다.**
   - 후보 surface를 현재 owner source와 비교한다.
   - UX parity는 backend capability만 보지 말고 affordance, label, state transition, empty/error state, density, permission behavior까지 비교한다.
   - source evidence와 사용자 scope가 뒷받침할 때만 gap을 implementation work로 표시한다.

5. **각 finding을 분류한다.**
   - `Owner`
   - `Derived/Router`
   - `Legacy/Compatibility`
   - `Stale/Superseded`
   - `Evidence-only`
   - `Parity gap`
   - `Caller intent/access policy unconfirmed`
   - `Decision needed`
   - `Out of scope`
   - `Existing-skill handoff`

## 출력 계약

명확하다면 recommendation 또는 disposition을 먼저 말한다. finding은 severity 또는 impact 순서를 선호한다.

각 finding에는 다음을 포함한다.

- `Surface:` 질문 대상 파일, route, feature, API, doc, config, behavior
- `Owner path:` 현재 권위 있는 source
- `Candidate/caller path:` 경쟁하거나 소비하는 경로가 다를 때
- `Evidence:` 구체적인 source path, symbol, route, endpoint, schema, test, doc, command, observed behavior
- `Impact:` 동작 또는 소유권상의 결과
- `Disposition:` audit taxonomy 중 하나
- `Next:` 사용자 scope가 허용할 때만

근거가 부족하면 무엇을 확인했는지 말하고, 추론으로 빈칸을 채우지 말고 `Decision needed`, `Caller intent/access policy unconfirmed`, `Insufficient current evidence`로 분류한다.

## 위임 경계

- 코드 구현, refactor scope, verification planning은 감사 이후 change-execution layer가 맡는다.
- 코드 구조, decision/write-path redesign, contract test는 owner가 확인된 뒤 code-structure layer가 맡는다.
- 문서 패키지 재구성, current-canon 승격, task log, reference migration은 owner가 확인된 뒤 document/context layer가 맡는다.
- always-read instruction 편집, token-budget 전략, runtime UI freshness ownership, work-board selection은 사용자가 그것에 대한 source-owner audit을 요청한 경우가 아니면 별도 관심사다.

## 안티패턴

- 메모리나 과거 요약을 proof로 쓰기.
- 구체적인 surface가 있는데 broad grep부터 시작하기.
- command/API 존재를 implementation approval로 취급하기.
- copied, generated, fallback, evidence-only surface를 proof 없이 owner로 취급하기.
- audit-only finding으로 implementation TODO를 열기.
- read-only audit 중 code, docs, AGENTS file, task state, deployment config를 수정하기.
- 불확실성을 confident recommendation으로 숨기기.
