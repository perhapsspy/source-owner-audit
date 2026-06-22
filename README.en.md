# Source Owner Audit

[한국어](README.md) | [English](README.en.md)

## Summary

`source-owner-audit` helps an agent answer: “which code, API, config, or doc should we follow now, and does this change match it?”

It is read-only. It finds the source owner first, then reports evidence, mismatches, and a recommendation. File edits are only in scope when the user expands the task.

It turns broad source-of-truth questions into three concrete answers:

- What should we follow?
- What does not match?
- What still needs a decision?

## Quick Start

**Install**

```bash
npx skills add perhapsspy/source-owner-audit
```

Or copy `skills/source-owner-audit` into your agent skills directory.

**Use**

```text
Use $source-owner-audit. Which code or doc should this API response follow?

Use $source-owner-audit to check whether this screen behavior still matches the existing owner. Do not edit files.

Use $source-owner-audit to check whether this doc is still true against the current code.
```

## Use When

- You are not sure which repo, file, API, config, or doc to follow
- You have an old summary or task doc and need it checked against current code
- Porting, migration, or routing work needs the original behavior to preserve
- You want a read-only review of a proposed or current implementation against the owner
- You need to separate “the backend supports this” from “the UI or product approved this behavior”

## Related Skills

This skill works independently. Related skills in the same family include [`structure-first`](https://github.com/perhapsspy/structure-first), [`project-context`](https://github.com/perhapsspy/project-context), and [`justified-change`](https://github.com/perhapsspy/justified-change).

## Support

[![Buy Me A Coffee](https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png)](https://www.buymeacoffee.com/perhapsspy)

## License

[MIT](LICENSE)
