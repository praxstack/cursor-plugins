# T7 — Reconcile branch with origin/main (upstream pstack docs port)

**Status:** done · **Labels:** ready-for-agent · **Spec:** SPEC.md AC5 (gates stay green on current main)

origin/main advanced past the remediation branch with upstream sync commits,
including `docs(pstack): port workflow and boundary guidance (#238)`. The open
remediation branch must absorb main so the PR is mergeable and the gates are
proven against current upstream content, not a stale base.

**Fix:** `git merge origin/main` onto `fix/post-merge-review-findings`.
Dry-run via `git merge-tree --write-tree HEAD origin/main` returned a single tree
OID with zero conflict entries, so the merge is clean by construction; all four
gates are re-run post-merge as proof.

Evidence: `.agent/evidence/pr9-rerun-post-merge-2026-08-22/` (fresh gate logs).
