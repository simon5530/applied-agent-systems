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

## Failure-path testing

Test unauthorized requests, stale state, provider failure, duplicate delivery, restart
persistence, and unavailable humans—not only the happy path.

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
