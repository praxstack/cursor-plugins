# T7 — Port upstream pstack 0.14.2 workflow/boundary guidance into pstack-generic

**Status:** open · **Labels:** needs-triage · **GitHub:** praxstack/cursor-plugins#10
**Origin:** PR #9 reconciliation merge 215edb0 (upstream-synced main 4612556)

Upstream's pstack 0.14.2 added genuinely new guidance to the four files that
conflicted with the generic port (plugin.json + three poteto-mode playbooks):
`/goal` arming on operator go, terminal `/loop` audit-tick cadence with liveness
probes and stuck-owner stand-down, output-notification sentinels, re-read
playbook from trunk, boundary hardening — written Cursor-specifically.

PR #9 resolved those files **ours (generic)** so the port is not reverted on a
main branch that was force-synced to upstream. This ticket carries the upstream
additions forward: port each into host-neutral phrasing (host adapters, generic
delegates), preserving semantics, then re-run all three gates + runtime tests.

**Acceptance:** every semantic upstream addition present in generic phrasing or
an explicit recorded decision to omit; gates 1–3 exit 0; `bun test pstack` green.

**Parked (needs human):** none — fully agent-executable once triaged
`ready-for-agent`.
