# Source Owner Audit

[한국어](README.md) | [English](README.en.md)

## 요약

`source-owner-audit`는 구현이나 마이그레이션 전에 현재 권위 있는 source owner, 계약 근거, parity gap, stale surface, decision-owner boundary를 read-only로 판정하기 위한 스킬입니다.

이 스킬은 두 가지 문제를 줄이는 데 초점을 둡니다.

- 이전 요약, 메모리, 오래된 문서, 복사된 코드 표면을 현재 owner처럼 믿는 것
- backend capability나 command 존재만 보고 기존 제품 계약이나 UX를 임의로 구현 TODO로 바꾸는 것

목표는 코드를 바로 바꾸는 것이 아닙니다.

목표는 무엇이 현재 source of truth인지, 무엇이 derived/evidence/stale인지, 무엇이 decision-owner boundary인지 근거로 분류하는 것입니다.

`스펙:` Agent Skills / SKILL.md | `라이선스:` MIT | `에이전트:` Codex, ChatGPT, Agent Skills 호환 도구

## 빠른 시작

**설치**

```bash
npx skills add perhapsspy/source-owner-audit
```

혹은 `skills/source-owner-audit` 폴더를 에이전트 스킬 디렉터리에 직접 복사합니다.

**바로 사용**

```text
$source-owner-audit 를 사용해서 이 기능의 현재 owner path, caller path, 계약 근거, disposition을 read-only로 감사해줘
```

## 이런 때 사용

- 여러 repo, API, 문서, config 중 현재 source of truth를 가려야 할 때
- 이전 요약이나 오래된 task doc을 현재 소스 기준으로 재검증해야 할 때
- porting, migration, parity 작업 전에 무엇을 그대로 따라야 하는지 확인해야 할 때
- backend command/API 존재와 caller/UI intent 또는 product approval을 구분해야 할 때
- dirty worktree에서 source-of-truth/owner dispute에 대한 read-only 감사 결과만 필요할 때
- source-of-truth/owner dispute finding을 owner path, source evidence, impact, disposition 중심으로 정리해야 할 때

## 프로젝트 가치 보존 스킬

이 스킬들은 오래 운영되는 프로젝트가 나중에도 이해되고 수정될 수 있는 상태를 유지하도록 돕습니다.

- [`structure-first`](https://github.com/perhapsspy/structure-first): 코드 흐름, 책임 경계, 수정 가능성, 계약 중심 테스트를 보존합니다.
- [`project-context`](https://github.com/perhapsspy/project-context): 저장소 안의 일반 문서로 프로젝트 기억, 결정 이유, 현재 작업 상태, 작업 연속성을 보존합니다.
- [`interactive-state-flow`](https://github.com/perhapsspy/interactive-state-flow): 지체 없이 기록되어야 하는 기준 상태와 비용이 큰 표현·비동기 작업·실행 경로를 분리합니다.
- [`justified-change`](https://github.com/perhapsspy/justified-change): 변경 목표, 직접 영향 범위, 범위 근거, 검증 기준을 맞춰 불필요한 작업과 누락된 후속 수정을 함께 줄입니다.
- [`codex-token-discipline`](https://github.com/perhapsspy/codex-token-discipline): 긴 세션, 넓은 읽기, 서브에이전트, always-read 지시문 비용을 관리합니다.
- `source-owner-audit`: 변경 전에 현재 owner와 계약 근거를 분류해, 무엇을 바꿔야 하는지와 바꾸면 안 되는지를 구분합니다.

각 스킬은 독립적으로 설치하고 사용할 수 있습니다. 이 README는 같은 철학의 스킬들을 소개할 뿐, 개별 `SKILL.md`가 서로를 호출하거나 의존하게 만들지 않습니다.

## 지원

[![Buy Me A Coffee](https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png)](https://www.buymeacoffee.com/perhapsspy)

## 라이선스

[MIT](LICENSE)
