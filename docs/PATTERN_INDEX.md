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
