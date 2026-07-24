# Goal

`source-owner-audit`가 소스 소유권 확인과 쓰기 권한을 분리하고, 감사 근거가 사용자 승인 범위를 넓히지 않도록 실행 경계를 보강한다.

## Scope

- `skills/source-owner-audit/SKILL.md` 검토
- 필요 시 `skills/source-owner-audit/SKILL.ko.md` 의미 동기화 후보까지 검토
- README, direction, AGENTS 변경은 이번 검토 범위 밖

## Current Understanding

- owner를 찾아 읽기 전용으로 확인하는 것은 정상 감사이며, owner 확인 자체가 쓰기 권한을 부여하지 않는다.
- 기존 스킬은 감사 결과만으로 수정을 허가하지 않지만, source ownership과 surface-scoped write authorization의 관계를 한 문장으로 더 직접 고정할 가치가 있다.
- 보강은 특정 저장소나 runbook 사례를 넣지 않고 일반 원칙 한 문장으로 제한한다.

## Current State

- 영문 기본 스킬과 한국어 pair에 동일한 권한 경계 문장을 반영했다.
- skill 구조, task runtime shape와 diff 검증이 통과했다.
- Project Legibility lock과 generated snapshot 동기화는 downstream 저장소가 맡는다.

## Next Step

사용자 승인 범위와 owner 근거가 다시 혼동되는 사례가 확인될 때 재검토한다.

## Working Boundary

- `skills/source-owner-audit/SKILL.md`
- `skills/source-owner-audit/SKILL.ko.md`
- `docs/tasks/2026/06-23/audit-boundary-owner-first/`
