## Summary

Re-raise of the post-merge review remediation that was closed unmerged as #245 (opened against the wrong default base — upstream instead of this fork; branch content was correct). Supersedes #245. Closes #11 (T7), closes #12 (T8); refs #13.

The branch carries three remediation commits plus a clean merge of current main:

- `a4eaaf1` fix(pstack): gate-5 degradation fixes and spec carve-out
- `d6b4292` fix(scripts): floor guard and CRLF tolerance in reference checker
- `12935ba` docs(evidence): reconcile gate-5 audit; fix dead evidence citations
- `215edb0` Merge upstream tip (4612556) — absorbs docs(pstack) workflow/boundary port (#238); `git merge-tree` dry-run showed zero conflicts

## What changed, honestly

1. **Reference gate hardening** (`scripts/check-pstack-references.mjs`): floor guard and CRLF tolerance so the gate degrades predictably instead of mis-reporting on Windows-style line endings or empty match sets.
2. **Gate-5 degradation fixes** under `pstack/`: bounded fallback behavior when subagents are unavailable, with spec carve-out documented rather than silently absorbed.
3. **Evidence truthfulness**: dead evidence citations repaired; gate-5 audit wording now matches what the code actually does.
4. **Reconciliation**: main absorbed; all gates proven against current upstream content, not a stale base.

## QA evidence (fresh, at HEAD `215edb0`, 2026-08-22)

| Gate | Command | Result |
|---|---|---|
| Portability (gate 1) | `npm run check-pstack-portability` | exit 0 |
| References (gate 3) | `npm run check-pstack-references` | exit 0 |
| Marketplace validation | `npm run validate-plugins` | exit 0 |
| Runtime tests | `bun test pstack` | 52 pass / 0 fail, exit 0 |

Raw logs: `.agent/evidence/pr9-rerun-post-merge-2026-08-22/` (`.log` files are gitignored by repo policy; substance mirrored above and in `.scratch/pstack-generic-gates/T7`/`T8`).

**Known unrelated failure (not introduced here):** bare `bun test` at repo root discovers 139 tests across 32 files including `orchestrate/*`, which errors on missing optional deps (`@slack/web-api`, `zod/v3`). `orchestrate/` is byte-identical to `origin/main` (verified via diff), so this is pre-existing upstream state — filed separately as #13 with repro and suggested directions.

## Process notes

- Tickets: T7 → #11, T8 → #12 (markdown mirrors in `.scratch/pstack-generic-gates/`).
- Fresh-context code review ran over `origin/main..HEAD` before this PR was raised; findings and verdict recorded in `.agent/evidence/code-review-findings.md`.
- Review-only PR: raised by the authoring agent, intentionally **not merged** — merge approval stays human.
