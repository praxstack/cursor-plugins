# T10 port ledger — upstream pstack 0.14.2 → pstack-generic

Source: upstream/main 4612556 · Target: fix/port-upstream-pstack-0142
Rule: every semantic upstream addition is either ported in host-neutral phrasing
or omitted with a recorded reason. Identity files stay ours (SPEC non-goals).

## autopilot-full.md

| Upstream addition | Decision |
|---|---|
| `/goal` arming on operator go, persists across turns | PORTED — "persistent program goal … host's native goal or plan mechanism when it has one, otherwise a recorded objective every audit tick re-reads" |
| Terminal `/loop` audit cadence + monitored-shell sleep | PARTIAL PORT — cadence stays on the existing host-neutral sentence ("event, wait, or recurring-work feature … bounded polling"); Cursor's terminal-/loop and cloud-sleeper mechanics are host-specific and omitted |
| Output-notification sentinel per tick | PORTED verbatim-in-meaning |
| Never leave cadence to memory / lossy completion notifications | PORTED |
| Re-read playbook from trunk via `git show origin/main:<path>` + re-read armed goal | PORTED (path adjusted to this file) |
| Fix drift during tick, treat as urgent | PORTED |
| Liveness/status probe per owner | PORTED (replaces vaguer "probes delegated-work status") |
| Count only side effects as progress (commits/pushes/PR-check deltas/store reports) | PORTED |
| Stuck-lane stand-down + immediate replacement, "do not wait for a polite return" | PORTED |
| Bugbot pass counters / `cursor-team-kit` deslop / control-cli-control-ui names | OMITTED — already generalized in ours ("skeptical automated-review triage", "installed deslop equivalent", "installed CLI or UI control skill"); naming the Cursor plugin would re-couple the generic variant |
| Cloud-sleeper wake chain | OMITTED — Cursor cloud concept; ours' bounded-polling fallback covers it |

## autopilot-stack.md

| Upstream addition | Decision |
|---|---|
| `/goal` arming on explicit go | PORTED (same neutral phrasing as full) |
| Audit-tick hardening block (sentinel, trunk re-read, side-effects progress, stuck stand-down) | PORTED (path adjusted) |
| `gt` restack/submit mechanics, Graphite UI delivery | OMITTED — ours keeps source-control-host adapter phrasing ("whatever stacking tool the team uses", "active source-control adapter"); semantics preserved, tool coupling dropped |
| Cloud-agent division-of-labor framing | OMITTED — host-specific |

## opening-a-pr.md

| Upstream addition | Decision |
|---|---|
| Per-invocation worktree isolation for sequential writers (`fetch && reset --hard origin/<branch>`) | PORTED |
| `/technical-writing` layers except Diátaxis + one-word-per-action / keep articles / avoid `-ing` | PORTED (skill referenced generically) |
| Conventional Commits title spec (types, scope examples, imperative subject, real symbol, no trailing period) | PORTED |
| Sectioned description template Why/Scope/Tradeoffs/Blast Radius/Verification + drop-when-empty + media after sections | PORTED |
| Boilerplate ban extended from "small PRs" to all PRs | PORTED (stronger form adopted; duplicate clause removed) |
| Open ready never draft + ready-command fallback + verify via PR viewer | PORTED (host-neutral wording; absorbs ours' viewer sentence) |
| Babysit reversal: opening ≠ babysit; separate pass only on request post-stack; stalls-build rationale | PORTED — replaces ours' auto-babysit line (upstream semantics win; recorded here) |
| `gt` stacking specifics | OMITTED — team-tool neutrality retained |

## plugin.json

| Upstream change | Decision |
|---|---|
| name/displayName/description/publisher/homepage/repository/keywords/tags | OMITTED — identity is human-owned and intentionally generic (`pstack-generic`, praxstack) |
| version 0.14.2 | PORTED AS `0.14.2-generic.1` — signals upstream-content parity of carried guidance while keeping the generic identity scheme |
