# Learning log

## 2026-09-15 — Ingress, gateway, nodes, and migration

- A webhook is an event contract; ngrok and Tailscale are transport/exposure choices;
  the gateway is the runtime authority.
- Public SaaS webhooks and private wearable access require different ingress trust
  models even when they reach the same gateway.
- Moving a tunnel does not move the gateway, and adding a GPU does not improve the
  gateway control plane by itself.
- Add devices, sessions, agents, nodes, and gateways for different reasons; one active
  gateway is the simplest safe default.
- A verified backup becomes recovery evidence only after a restore rehearsal.
- See [Deployment topology and migration](DEPLOYMENT_TOPOLOGIES.md).

## 2026-09-15 — Milestone-based learning capture

- Automatic context compaction is a runtime safeguard, not a controllable workflow
  hook.
- Durable learning should be captured when a decision, diagnosis, protocol, security
  boundary, or verification becomes reusable.
- Public notes are curated engineering artifacts rather than exported chat logs.
- See [Learning capture workflow](LEARNING_CAPTURE.md).

## 2026-09-14 — Selective adoption of external agent skills

- Agent skills are executable operating procedures and supply-chain dependencies,
  not just prompt snippets.
- Precise context pointers, progressive disclosure, shared domain language, and
  checkable completion criteria improve reliability without bloating global context.
- Adopted `diagnosing-bugs`, `domain-modeling`, and `writing-for-agents` from a
  pinned, reviewed upstream revision; deferred workflows that require unnecessary
  questioning, issue-tracker ceremony, or sub-agents.
- See [Agent skill design and adoption](AGENT_SKILLS.md).

## 2026-09-14 — Memory source/index identity

- Durable memory files and their semantic index are separate layers.
- An index-source mismatch can pause semantic recall without deleting source files.
- Validation requires both healthy index state and a real retrieval query.
- Reindexing the main workspace produced 15 files and 107 chunks with a valid identity.

## 2026-09-14 — Public repository security baseline

- Secret scanning must cover both the current tree and complete reachable history.
- Commit author email is public metadata and should use a GitHub noreply address when
  personal email disclosure is not intended.
- GitHub Secret Scanning, Push Protection, Dependabot, and private vulnerability
  reporting complement local scanners; none replaces manual semantic review.

## 2026-09-13 — Agent/session/channel separation

- One agent can own many sessions.
- Per-peer sessions isolate short-term context.
- Separate agents add workspace, memory, session-store, and tool-policy boundaries.
- Provider-issued IDs are authorization inputs; display names are not.

## 2026-09-13 — Private BYOA transport

- Loopback protects the local service boundary.
- Tailscale Serve makes it reachable to authenticated tailnet devices.
- Bearer authentication remains necessary behind the private network.
