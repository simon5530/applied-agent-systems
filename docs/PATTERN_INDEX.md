# Engineering pattern index

## Least privilege

Grant only the data and actions required for one workflow. A guest-facing agent should
receive derived availability, not raw calendar events or broad filesystem access.

## Defense in depth

Combine independent controls, such as private network membership and application
authentication. Avoid treating either control as a substitute for the other.

## Idempotency

Retries with the same idempotency key return the same result instead of duplicating an
external action.

## State machine

Represent meaningful states explicitly, such as proposed, held, confirmed, declined,
and expired.

## TTL

A time-to-live gives temporary state an automatic expiry. It is essential for soft
holds, cached authority, and short-lived credentials.

## Optimistic concurrency

Re-check state immediately before committing. If the version or availability changed,
reject and renegotiate rather than silently overwriting.

## Human approval gate

Allow low-risk queries and reversible drafts to run automatically. Require a preview
and explicit approval for external, destructive, financial, or socially consequential
actions.

## Fallback with quality floor

Fallback improves availability only when every candidate still satisfies context,
tool-use, safety, and reliability requirements.

Treat a fallback as an executable recovery path, not a model name in configuration.
Keep it only when it has an independent credential/quota path, passes a live tool-use
probe, meets the workload's safety floor, and fails over within an acceptable latency.
An unreachable or quota-exhausted fallback reduces reliability by extending failure
time. When no candidate passes, an empty fallback chain is safer and more truthful.

Model-size and family heuristics are screening signals rather than universal proof of
safety. A runtime audit can reject a known weak tier and separately flag small parameter
counts, but operational admission still requires task-specific evaluation and a live
provider proof.

## Failure-path testing

Test unauthorized requests, stale state, provider failure, duplicate delivery, restart
persistence, and unavailable humans—not only the happy path.

## Verification over trust

Express consequential behavior as an inspectable contract, then check the produced
artifact with an independent executable oracle before allowing the effect. Use the
cheapest adequate oracle: schemas and types, deterministic calculations, linting,
unit or property tests, dry-runs, policy checks, or formal verification when the
risk and tractability justify it.

A passing oracle proves only the encoded contract. Review the specification and the
oracle too, test boundary cases, and reject weakened constraints or trivial solutions.
Stable checks belong in versioned code so later runs execute evidence instead of
repeating model self-review.

This qualification is illustrated by Ehrenborg et al., [*A benchmark for vericoding:
formally verified program synthesis*](https://arxiv.org/html/2509.22908v1) (arXiv
preprint v1, September 2025): proof checking was supplemented with anti-cheating
validation, model comparison, and manual inspection because weak specifications could
admit unintended solutions. The accompanying
[benchmark repository](https://github.com/Beneficial-AI-Foundation/vericoding-benchmark)
provides the executable artifact.

## Unknown-outcome recovery

If a restart, timeout, or interrupted tool call occurs during a mutation, treat the
result as unknown rather than failed. First inspect authoritative state through a
read-only path; retry only when that check proves the intended effect is absent. This
prevents both duplicate effects and false completion claims.

Keep diagnostic and product paths distinct. A failure in a shell probe, proxy, or
credential-resolution path does not prove the user-facing capability is broken. The
cheapest discriminating check exercises the real product path. For layered
integrations, verify installation, process health, user-visible availability, and
functional behavior as separate completion criteria.

## Resolved execution surface

For restricted or scheduled agent runs, distinguish four layers that are easy to
collapse into one claim:

1. the tool name described in a prompt or runbook;
2. the tools permitted by policy;
3. the concrete tool names exposed by the resolved runtime; and
4. the external effect produced by a submitted call.

A permitted capability can still appear under a runtime-specific name, and a job can
finish successfully after merely reporting that it could not perform its intended
work. Diagnose the resolved runtime and its concrete tool surface before changing
credentials or repository settings. Then verify tool availability, workflow run
status, command exit status, and authoritative external state separately.

Durable sessions may also retain runtime or model overrides after global defaults
change. Inspect the session's resolved configuration when a job fails before model
inference or behaves differently from an equivalent fresh session. Recovery is
complete only when the intended product path succeeds and its external effect is
independently observed.

## Correlation ID

Carry one non-secret identifier across channel, agent, tool, and audit events so a
workflow can be reconstructed without logging sensitive content.

## Conversation as UI

Use an existing communication channel for commands, clarification, approval, and
status; use the system of record for inspection. A thin state and policy service can
support the workflow without requiring users to adopt another destination app.

## Candidate before commitment

Extraction identifies a possible action, not authority to execute it. Convert natural
language into a candidate, validate missing facts and conflicts, then apply explicit
policy before creating an external commitment.

## Candidate is not tentative availability

Use precise authority labels. A **candidate** is generated from constraints and policy
but may not have been checked against a system of record. **Tentative availability**
requires an authoritative conflict check but still awaits human approval. Only an
explicit owner decision creates a **confirmed** commitment. Clear terms prevent an
agent from overstating what its data sources actually prove.

## Derived-data boundary

Expose the smallest fact needed across an agent boundary—for example availability,
not event titles; a proposal and expiry, not a conversation transcript.

## Context firewall with provenance labels

Let the privileged agent retrieve private context inside its own boundary, then pass
only validated derived output through a typed broker. Use a small allowlist of source
labels such as `policy_only` or `main_memory`; never pass memory excerpts or arbitrary
rationale to the untrusted agent. If retrieval finds no explicit fact that supports a
decision, fall back to request constraints rather than inferring a preference.

## Human-agent-agent-human handoff

Each person's agent applies private preferences and releases only a minimal proposal
envelope. Humans retain approval for consequential commitments while agents handle
normalization, availability, alternatives, expiry, and audit.

## Capability broker

Keep an untrusted agent's general tool policy minimal and expose one typed business
capability with a fixed target, bounded input, derived output, policy checks, and
audit. This avoids solving every new workflow by granting filesystem, calendar,
node, transcript, or generic cross-agent access.

Where the runtime supports tool factories, enforce the boundary twice: restrict the
tool name in the agent policy, then return no tool instance unless both the agent and
exact requester session match the allowlist. Disable generic cross-agent session
visibility when the broker does not require it.

## Policy-enforced agent action zone

Place a deterministic reference monitor between untrusted agents and consequential
resources. Govern what crosses the boundary rather than trying to control an agent's
private prompts or reasoning.

The boundary should bind authenticated identity and delegation depth to a typed
intent; authorize the exact data, tool, resource, and effect; apply rate, time, and
cost budgets; expose only derived output; stage reversible actions; require approval
for irreversible or socially consequential effects; re-check policy at commit time;
and emit correlated decision and effect receipts.

A workflow describes how work normally proceeds. A sandbox limits the computation
an agent can perform. A gateway mediates traffic. A policy engine decides whether an
action is allowed. An action zone composes these controls so the invariant still
holds when the agent changes its plan, framework, model, or internal delegation.
