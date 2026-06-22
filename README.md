# Source Owner Audit

[한국어](README.md) | [English](README.en.md)

## 요약

`source-owner-audit`는 에이전트가 “지금 어느 코드/API/설정/문서를 따라야 하고, 현재 변경이 그 기준과 맞는지”를 읽기 전용으로 확인하게 해주는 스킬입니다.

먼저 기준 소스(source owner)를 찾고, 그다음 근거, 차이, 권고를 정리합니다. 파일 수정은 사용자가 범위를 넓힐 때만 다룹니다.

넓은 질문을 세 가지 결과로 좁혀줍니다.

- 따라야 할 기준
- 기준과 다른 부분
- 지금 결정이 필요한 부분

## 빠른 시작

**설치**

```bash
npx skills add perhapsspy/source-owner-audit
```

혹은 `skills/source-owner-audit` 폴더를 에이전트 스킬 디렉터리에 직접 복사합니다.

**바로 사용**

```text
$source-owner-audit 이 API 응답은 어느 코드나 문서를 기준으로 맞춰야 해?

$source-owner-audit 이 화면 동작이 기존 기준과 달라졌는지 봐줘. 파일은 고치지 마.

$source-owner-audit 이 문서 결론이 아직 맞는지 현재 코드로 확인해줘.
```

## 이런 때 사용

- 어느 저장소, 파일, API, 설정, 문서를 따라야 할지 애매할 때
- 오래된 요약이나 작업 문서를 현재 코드 기준으로 다시 확인해야 할 때
- porting, migration, routing 작업에서 유지해야 할 원본 동작을 찾아야 할 때
- 제안했거나 이미 만든 구현이 기준과 맞는지 읽기 전용으로 보고 싶을 때
- “백엔드가 지원한다”와 “화면이나 제품에서 승인한 동작이다”를 구분해야 할 때

## 관련 스킬

이 스킬은 독립적으로 동작합니다. 같은 계열의 스킬은 [`structure-first`](https://github.com/perhapsspy/structure-first), [`project-context`](https://github.com/perhapsspy/project-context), [`justified-change`](https://github.com/perhapsspy/justified-change)입니다.

## 지원

[![Buy Me A Coffee](https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png)](https://www.buymeacoffee.com/perhapsspy)

## 라이선스

[MIT](LICENSE)
