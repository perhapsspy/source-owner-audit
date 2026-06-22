# Source Owner Audit

[한국어](README.md) | [English](README.en.md)

## Summary

`source-owner-audit` is a lightweight skill for read-only source-first audits before implementation or migration. It helps identify the current authoritative source owner, contract evidence, parity gaps, stale surfaces, and decision boundaries.

The skill focuses on two failure modes:

- Treating old summaries, memory, stale docs, copied code, or generated surfaces as current owners
- Turning backend capability or command existence into implementation TODOs without caller/UI intent or product approval

The goal is not to edit code immediately.

The goal is to classify what is the current source of truth, what is derived/evidence/stale, and what needs a decision-owner boundary.

`Spec:` Agent Skills / SKILL.md | `License:` MIT | `Agents:` Codex, ChatGPT, Agent Skills-compatible tools

## Quick Start

**Install**

```bash
npx skills add perhapsspy/source-owner-audit
```

Or copy `skills/source-owner-audit` into your agent skills directory.

**Use**

```text
Use $source-owner-audit to audit the current owner path, caller path, contract evidence, and disposition for this feature without editing files.
```

## Use When

- Multiple repos, APIs, docs, or config surfaces may claim to be the source of truth
- A prior summary or old task doc must be revalidated against current source
- Porting, migration, or parity work needs owner evidence before implementation
- Backend command/API existence must be separated from caller/UI intent or product approval
- A dirty worktree requires read-only audit results for a source-of-truth or owner dispute
- Source-of-truth or owner-dispute findings should be reported as owner path, source evidence, impact, and disposition

## Project Value Preservation Skills

These skills help long-lived projects remain understandable and changeable.

- [`structure-first`](https://github.com/perhapsspy/structure-first): Preserve readable code flow, responsibility boundaries, maintainability, and contract-focused tests.
- [`project-context`](https://github.com/perhapsspy/project-context): Preserve project memory, decisions, current task state, and continuity in ordinary repo files.
- [`interactive-state-flow`](https://github.com/perhapsspy/interactive-state-flow): Separate prompt source state from expensive presentation, async work, and execution paths.
- [`justified-change`](https://github.com/perhapsspy/justified-change): Keep code changes proportional, justified, and verifiable.
- [`codex-token-discipline`](https://github.com/perhapsspy/codex-token-discipline): Manage long sessions, broad reads, subagents, and always-read instruction costs.
- `source-owner-audit`: Classify the current owner and contract evidence before deciding what should or should not change.

Each skill can be installed and used independently. This README introduces related skills in the same philosophy; individual `SKILL.md` files do not call or depend on one another.

## Support

[![Buy Me A Coffee](https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png)](https://www.buymeacoffee.com/perhapsspy)

## License

[MIT](LICENSE)
