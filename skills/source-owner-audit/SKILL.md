---
name: source-owner-audit
description: Use when the central question is a read-only source-of-truth or contract-owner audit before implementation, migration, porting, parity work, or routing changes. Helps identify the authoritative source owner, static caller/UX contract owner, contract evidence, stale or derived surfaces, migration owner, parity gap, and decision-owner boundary from current code/docs/config/API evidence. Avoid for ordinary code edits, runtime UI state ownership, document restructuring, task-state storage, AGENTS editing, token budgeting, or work selection unless those tasks explicitly ask which current source owns the truth.
---

# Source Owner Audit

## Purpose

Determine the current authoritative source owner before implementation, migration, or routing changes.

This is an audit skill. Default to read-only evidence gathering and disposition. Do not turn the audit into edits, TODO ownership, migrations, deploy steps, or broad cleanup unless the user explicitly expands the scope.

## Core Bias

- Current source beats memory, prior summaries, old task notes, stale docs, and inferred parity.
- Start from concrete owner surfaces: routes, entrypoints, commands, schemas, API clients, config, tests, runbooks, owner docs, or user-visible behavior.
- Trace the smallest source paths needed to prove ownership.
- Separate confirmed facts from inference.
- Do not invent, simplify, or shrink an existing product contract or UX to make implementation easier.
- If the source leaves a policy/product choice open, name the decision owner instead of choosing silently.

## Operating Flow

1. **Fix the audit question and boundary.**
   - Name the question: source owner, contract owner, static caller/UX contract owner, parity gap, stale-summary revalidation, migration owner, or evidence sufficiency for possible later implementation.
   - Name closed scopes: no edits, no TODO conversion, no doc restructuring, no deploy, no live mutation, no broad cleanup.

2. **Inventory candidate surfaces narrowly.**
   - Use the surface named by the user first.
   - Prefer path-specific reads over repo-wide scans.
   - For dirty worktrees, start with status and small path-scoped diffs when local changes could affect the answer.
   - For cross-repo or cross-surface work, verify each candidate owner independently.

3. **Trace ownership.**
   - Follow caller -> adapter/client/helper -> route/API -> command/service -> persistence/schema/test owner where relevant.
   - Distinguish source owner, static caller/UX contract owner, write owner, read owner, doc owner, task owner, migration owner, and decision owner.
   - Distinguish current production owners from legacy, fallback, compatibility, generated, copied, or evidence-only surfaces.
   - Do not treat backend capability or command existence as caller intent, access policy, or product approval.

4. **Compare against the owner, not the memory.**
   - Compare candidate surfaces to the current owner source.
   - For UX parity, compare affordances, labels, state transitions, empty/error states, density, and permission behavior, not only backend capability.
   - Mark a gap as implementation work only when source evidence and user scope support that ownership.

5. **Classify each finding.**
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

## Output Contract

Lead with the recommendation or disposition when it is clear. For findings, prefer severity or impact order.

Each finding should include:

- `Surface:` the questioned file, route, feature, API, doc, config, or behavior
- `Owner path:` current authoritative source
- `Candidate/caller path:` competing or consuming path, when different
- `Evidence:` concrete source paths, symbols, routes, endpoints, schemas, tests, docs, commands, or observed behavior
- `Impact:` behavioral or ownership consequence
- `Disposition:` one classification from the audit taxonomy
- `Next:` only if the user scope allows a next action

If evidence is incomplete, say what was checked and classify the result as `Decision needed`, `Caller intent/access policy unconfirmed`, or `Insufficient current evidence` rather than filling the gap with inference.

## Defer Boundaries

- Code implementation, refactor scope, and verification planning belong to the change-execution layer after the audit.
- Code structure, decision/write-path redesign, and contract tests belong to the code-structure layer after the owner is known.
- Document package restructuring, current-canon promotion, task logs, and reference migration belong to document/context layers after the owner is known.
- Always-read instruction edits, token-budget strategy, runtime UI freshness ownership, and work-board selection are separate concerns unless the user asks a source-owner audit about them.

## Anti-Patterns

- Relying on memory or old summaries as proof.
- Starting from a broad grep when a concrete surface is named.
- Treating command/API existence as implementation approval.
- Treating a copied, generated, fallback, or evidence-only surface as the owner without proof.
- Opening implementation TODOs from audit-only findings.
- Rewriting code, docs, AGENTS files, task state, or deployment config during a read-only audit.
- Hiding uncertainty behind a confident recommendation.
