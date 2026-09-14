# Learning log

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
