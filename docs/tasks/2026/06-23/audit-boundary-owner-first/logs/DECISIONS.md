# Decisions

**2026-06-23**

- Background: playground 조사에서 현재 소유자 확인 지연과 읽기 전용 경계 약화가 반복 문제로 확인됐다.
- Decision: `source-owner-audit` 변경 여부는 새 세션에서 타당성 검토를 먼저 받은 뒤 결정한다.
- Why: 현재 스킬에도 관련 원칙이 이미 있어, 바로 수정하면 중복 방어문이 될 수 있다.
- Impact: 새 세션은 `SOURCE-OWNER-AUDIT-BOUNDARY-PROPOSAL.md`를 기준으로 수정 필요성만 판단하고 파일 수정은 하지 않는다.

**2026-07-24**
- 후속 실제 사건에서 owner 탐색은 유효했지만, 확인된 portable owner까지 parent가 사용자 승인 없이 수정해 read-only 감사와 쓰기 권한이 혼동됐다.
- 소스 소유권과 쓰기 권한을 별개로 두고, owner 근거가 사용자 승인 범위 밖으로 실행을 넓히지 못한다는 일반 원칙 한 문장만 스킬에 추가한다.
- 기존 read-only 경계를 중복 확대하거나 특정 저장소·runbook 사례를 넣지 않으면서 실제 실패 지점을 직접 막는다.
- 영문 기본 스킬과 한국어 pair만 의미 동기화하고, canonical 검증·push 뒤 Project Legibility bundle을 갱신한다.
