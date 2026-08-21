# T8 — Re-raise remediation PR against the fork base, with QA evidence

**Status:** done · **Labels:** ready-for-agent · **Spec:** SPEC.md AC6 (ship reviewed PR)

PR #245 ("Post-merge review remediation: truthful gate-5 audit, hardened
reference gate") was opened against the wrong default base: `gh` resolved the
upstream remote (`cursor/plugins`) instead of the fork, and was closed unmerged
with the note "intended for the fork". The branch content was correct; only the
base was wrong.

**Fix:** push the reconciled branch and raise a new PR explicitly scoped with
`gh pr create --repo praxstack/cursor-plugins --base main --head
fix/post-merge-review-findings`. The body carries: summary of the three
remediation commits, the T7 merge reconciliation, fresh gate evidence
(portability / references / validate exit 0, bun runtime tests pass count),
links to issues T7/T8, and a pointer to the closed #245 for context. The PR is
raised review-only: it is not merged by the authoring agent.

Evidence: `.agent/evidence/pr9-rerun-post-merge-2026-08-22/` + PR URL recorded
in `.agent/progress-pr9.txt`.
