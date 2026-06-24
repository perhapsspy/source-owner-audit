# source-owner-audit 보강 검토 제안

## 판단할 문제

읽기 전용, 조사만, 금지, 제외, 범위 제한 표현이 감사 초기에 실행 경계로 고정되는지 검토한다.

또한 이전 대화, 기억 자료, 오래된 문서, 후보 구현이 결론을 만들기 전에 현재 소유 표면을 먼저 확인하도록 충분히 안내하고 있는지 본다.

## 후보 위치

`skills/source-owner-audit/SKILL.md`의 `Operating Flow` 1-2번 근처가 후보 위치다.

## 영문 후보

```md
- Treat explicit read-only, investigation-only, prohibition, exclusion, or scope-limit wording as binding execution boundaries; audit findings do not authorize edits, cleanup, or implementation planning.
- Resolve the current owner surface before memory, prior summaries, old task notes, stale docs, or candidate implementations shape the conclusion; until then, label conclusions as unverified or inference.
- Treat legacy, stale, copied, generated, or fallback surfaces as evidence-only unless a current owner explicitly still delegates to them.
```

## 한국어 의미

```md
읽기 전용, 조사만, 금지, 제외, 범위 제한 표현은 실행 경계로 고정한다. 감사 결과가 곧 수정, 정리, 구현 계획 권한을 주지는 않는다.
기억, 이전 요약, 과거 작업 문서, 낡은 문서, 후보 구현이 결론을 만들기 전에 현재 소유 표면을 먼저 확인한다. 그 전 결론은 미확인 또는 추론으로 표시한다.
레거시, 낡은 문서, 복사본, 생성물, 대체 경로는 현재 소유자가 명시적으로 위임하지 않는 한 근거 전용으로 본다.
```

## 보강 찬성 근거

- 현재 스킬의 핵심 원칙은 충분하지만, 관찰된 실패는 그 원칙이 너무 늦게 적용되는 문제다.
- 실행 경계와 현재 소유자 확인은 감사 초기에 잠겨야 한다.
- 감사 결과가 곧 수정·정리·구현 계획 권한으로 확장되는 것을 막는다.

## 보강 반대 근거

- 현재 스킬에도 읽기 전용 기본값, 현재 소스 우선, 레거시/대체 경로 구분, 구현 계획 제한이 이미 있다.
- 문구를 추가하면 스킬이 너무 방어적으로 보일 수 있다.
- 너무 강한 문구는 사용자가 이후 구현 범위를 명시적으로 넓힌 경우에도 불필요하게 발목을 잡을 수 있다.

## 검토 질문

1. 후보 문구가 기존 `Core Bias`와 `Operating Flow`를 반복하는가, 아니면 실행 순서를 실제로 잠그는가?
2. “감사 결과가 곧 수정 권한을 주지 않는다”는 문장이 필요한가?
3. 레거시/대체 경로를 근거 전용으로 보는 문구가 너무 강하지 않은가?
4. `SKILL.ko.md`에 반영한다면 한국어 문구가 자연스럽고 과하지 않은가?

## 완료 기준

- 수정 여부 권고가 명확하다.
- 수정한다면 정확한 위치와 최종 후보 문구가 2-3줄 안에 남는다.
- 수정하지 않는다면 보류 이유가 기존 스킬 문장 근거와 함께 제시된다.
