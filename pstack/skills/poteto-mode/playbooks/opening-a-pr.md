### Opening a PR

Invoked at the end of every other playbook.

**Worktree.** Work from a git worktree off main; delegates receive its path or branch. Concurrent writers each get their own worktree; sequential writers reusing one branch run `git fetch && git reset --hard origin/<branch>` between passes. Dirty branch with unrelated work: patch out, fresh worktree, apply. Snarled worktree: reset from main, redo minimally.

**Commits.** Commit liberally; rebase into small, ordered commits before opening PRs. Each commit is a future PR: landable, ordered to tell the story. Amend when the fix belongs in a just-made commit; new commit when separable.

**PRs.** Use an installed `deslop` skill when available; otherwise run repository formatting and lint, then inspect the diff manually. Run `/no-comments` before review and apply the **unslop** skill to the PR description and commit bodies. Write every PR title, description, and commit body through the **technical-writing** skill's layers except Diátaxis: one word per action, keep articles, prefer a plain verb over `-ing`.

**Titles.** Conventional Commits, `type(scope): subject` — `feat`, `fix`, `docs`, `refactor`, `test`, `chore`, or `perf`; the changed area as scope (`pstack`, `poteto-mode`); short imperative subject naming the real symbol that carries the change (`fix(pstack): retarget opening-a-pr babysit trigger`). No trailing period. Same technical-writing + unslop pass as the body.

**Descriptions.** Use these sections in order; drop one when it is empty.

- `## Why` — the intent, and why this approach fits.
- `## Scope` — facts from the diff: real symbols and paths, both sides of a rename or retarget, in/out boundary when it matters.
- `## Tradeoffs` — real choices only.
- `## Blast Radius` — who and what the change touches, why it is safe or risky; if main is red without the fix, name the continuing cost.
- `## Verification` — how each check ran and its rigor: real surface names (an installed CLI or UI control skill, targeted tests) and each outcome, not just command names.

Attach videos or screenshots after these sections when they prove a claim. No `## Summary` / `## Test plan` boilerplate on any PR; a commit body does not restate its subject.

**Size and stacks.** Small PRs, 5 narrow over 1 fat; stack follow-ups, branch off main only for genuinely independent work. For stacked PRs, use whatever stacking tool the team uses; the principle is small, ordered slices with the stack visible to reviewers. Rebase on `main` before substantial stack work.

**Readiness.** Open every PR ready, never as a draft. Host tooling that defaults to draft gets flipped through the host's ready command. Verify state through the repository host's supported PR viewer before referencing status.

**Babysit.** Opening a PR does not start a babysit. Post the URL and keep building; finish the phase or stack first. Run a separate babysit pass only when the operator asks for one once the whole stack exists — a babysit per new PR stalls the build and spends checks on commits later waves restart. Push back when feedback drifts from intent.

A subagent that opens a PR runs `interrogate`, `/deslop`, and `/no-comments`, returns the URL, and does NOT babysit. Return to the parent.
