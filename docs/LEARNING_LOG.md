# Learning log

## 2026-09-18 — Verify contracts and recover unknown outcomes

- A model can draft an implementation, but consequential execution should depend on
  an independent executable oracle derived from an inspectable contract.
- Formal proof establishes conformance to the encoded specification, not that the
  specification captures the intended behavior. Boundary tests and review must detect
  weak constraints and trivial solutions.
- Stable checks should become versioned schemas, tests, policies, or proofs so later
  runs reuse evidence instead of repeating model self-review.
- A restart or interrupted mutation makes the result unknown. Read authoritative state
  before retrying or claiming completion.
- Diagnose through the real product path when possible. Installation, process health,
  visible integration, and functional behavior are separate completion criteria.
- See [Verification over trust and unknown-outcome recovery](PATTERN_INDEX.md#verification-over-trust).

## 2026-09-18 — Govern agent effects, not private reasoning

- When an external requester is also an agent, its internal prompt, model, tools, and
  reasoning are neither observable nor a trustworthy enforcement surface.
- Put deterministic controls at ingress, data access, tool invocation, network egress,
  and commit points. Treat every call as a new authorization decision.
- Workflow orchestration specifies the expected path; a policy-enforced action zone
  preserves safety invariants even when an agent takes an unexpected path.
- Sandboxes, gateways, identity systems, policy engines, approvals, and audit logs are
  complementary layers. No single layer proves that a business effect is safe.
- Existing projects already cover much of the generic infrastructure. Differentiate
  through a narrow domain state machine, explicit authority labels, reversible
  effects, and measurable reduction in human interruption.

## 2026-09-17 — Failover must be proven, not merely configured

- A heartbeat failure after quota exhaustion can mean the entire model chain was
  attempted and exhausted; it does not prove that failover was skipped.
- In this incident, the primary route exhausted its subscription, one weak Ollama
  model timed out, Google returned quota exhaustion, and a local Ollama route was
  unreachable. The configured chain increased latency without providing recovery.
- The safe interim state is an empty fallback list for every agent: fail fast and
  visibly until an independent, high-quality provider passes a live runtime probe.
- Security audit heuristics use both known model-family quality tiers and a separate
  parameter-count warning. They are admission screens, not substitutes for workload
  evaluation.
- Remove an unused provider rather than preserving a synthetic or plaintext API-key
  marker. Pin external official plugins to exact versions and verify registry metadata,
  package locks, plugin loading, and compatibility.
- Heartbeat inference and heartbeat delivery are separate failure domains. A healthy
  model cannot deliver an alert when no owner route resolves; diagnose both layers.

## 2026-09-17 — Bounded private-context enrichment

- A public-facing agent does not need direct access to owner memory to benefit from
  it; a fixed owner workflow can retrieve context and return only derived candidates.
- Schema-level provenance labels make the boundary testable: `main_memory` requires
  an explicit scheduling-preference or time-boundary basis, while `policy_only`
  cannot claim one.
- Empty or irrelevant memory search results are a normal condition. The safe behavior
  is to use typed request constraints, not to manufacture a personal preference.
- Private context can influence a reversible candidate, but it cannot grant authority
  to confirm a consequential commitment.

## 2026-09-16 — Prove authority flow before adding data sources

- Calendar access does not make an unreliable agent handoff safe.
- First prove correlation, expiry, owner approval, and bounded return delivery inside
  one runtime; then carry the same typed capability across A2A.
- Without an authoritative schedule source, proposed times are candidates rather
  than tentative availability.
- Tool permissions should reflect real runtime state: the current Guest can use its
  own memory but does not have Node, Calendar, owner-memory, or transcript access.
- External adapters should enrich a proven state machine, not redefine who has
  authority to confirm a commitment.
- A live same-runtime test proved that tool factories can enforce both agent identity
  and exact session allowlists: Main and an unrelated Guest could not see the
  requester tools, while the intended Guest completed candidate → owner approval →
  confirmed-status retrieval.
- Generic cross-agent messaging and Gateway-wide transcript visibility were then
  disabled. The typed broker continued to work because its capability boundary does
  not depend on arbitrary session access.

## 2026-09-16 — A2A transport versus capability safety

- A2A standardizes discovery, Agent Cards and Skills, Messages and structured Parts,
  Task lifecycle, protocol bindings, and authentication advertisement.
- Authentication identifies a caller; the A2A server still implements per-Skill,
  data-level, and action-level authorization.
- A2A Messages can carry untrusted text or files, so protocol compliance alone does
  not prevent prompt injection or instruction smuggling.
- A typed capability broker can later become an A2A Skill; its validation, derived-
  data boundary, approval policy, idempotency, and audit remain application logic.

## 2026-09-16 — Brokered internal agent handoff

- Two agents on one Gateway can coordinate without adopting a cross-system A2A
  protocol.
- A generic cross-agent message tool enlarges prompt-injection and transcript-access
  risk; a typed capability broker is the narrower control surface.
- Guest access can stay minimal while the owner agent returns derived availability,
  requests human approval, commits a selected slot, and signals final status.
- Add a standard A2A protocol only when independently administered agents need
  discovery, authentication, portable task exchange, and status interoperability.

## 2026-09-15 — Conversation-first coordination

- A workflow can use messaging as its command surface and a calendar as its visual
  system of record without creating a new destination application.
- Natural-language extraction produces a candidate, not permission to act.
- Agent-to-agent coordination should exchange minimal proposals, authority labels,
  and expiry rather than raw calendars or chat history.
- Priority scoring should recommend conflict resolution; it must not silently grant
  authority to displace a confirmed commitment.
- A separate tentative calendar makes reversible agent holds visible without
  confusing them with confirmed events.

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
