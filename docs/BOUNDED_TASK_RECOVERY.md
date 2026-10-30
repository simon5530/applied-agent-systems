# Bounded task recovery

## Separate the task from its failed operation

Stopping an unsafe or invalid operation preserves evidence. Ending the authorized
task is a different decision. A task controller should classify the failure, retain
its checkpoint and investigate a bounded remedy before declaring itself blocked.

Use three recovery scopes:

- **Record or shard:** isolate a demonstrated local defect without skipping data
  within that shard; keep independent validated work moving.
- **Operation:** pause affected requests for diagnosis or a documented external
  wait. A valid prefix does not certify unobserved later records.
- **Task:** pause when permissions, external dependencies, unresolved integrity,
  or unsuccessful evidence-backed remedies leave no safe continuation path.

## Classify the requirement before fixing the data

A field required for analysis may be optional at acquisition. Retain a valid source
record with explicit missingness when the raw-data contract allows it, then enforce
the stricter prerequisite at the analysis boundary. Preserve raw values; neither
fabricate enrichment nor turn unknown into zero.

Conversely, scope, identity, timing and pagination constraints can be essential to
acquisition. Missing those constraints calls for isolation or diagnosis, not a
weakened oracle that makes the error disappear.

## Recovery procedure

1. Capture the exact phase, controlled reason, input/checkpoint, response or artifact
   hash and a secret-safe replay reference. An exception class is not a cause.
2. State competing explanations and choose the cheapest discriminating test. Replay
   saved input offline before spending another external request where possible.
3. Record each actual attempt: trigger, method, evidence, outcome and remaining
   uncertainty. Change the method when its prediction is falsified; repeated
   identical calls are not additional diagnosis.
4. Make a narrow, reversible correction under the existing authority. Add a
   regression that fails at the real production seam, preserve mandatory guards,
   then run the independent data/behavior oracle.
5. Resume one bounded unit. Require checkpoint advancement and unchanged accepted
   evidence, not merely a successful process exit or a created schedule.
6. If the agreed attempt budget is exhausted without a verified remedy, report the
   cause known so far, methods/results, partial output, remaining safe work, owner
   action and precise resume condition. Preserve the task/history rather than
   silently deleting it.

## Respect external boundaries

- Permission or credential failures pause protected requests. A code change is not
  authority to bypass consent, switch accounts or weaken access controls.
- Quota failures retain usage reservations and wait for the documented period and
  any retry instruction. A local counter is not the provider's remaining balance.
- Bounded time or lease expiry is a checkpoint boundary, not proof of technical
  failure or completed work. Make unfinished scope explicit.

## Put the controller in the effective runtime

Scheduled work must receive the recovery branch, available commands, evidence
journal and escalation criteria through instructions it actually loads. A note in
an omitted bootstrap file does not change behavior. Keep deterministic waiting,
checkpoint and quota logic outside inference; use reasoning for diagnosis.

Test the controller with a recoverable defect, an access denial, quota/reset waits,
exhausted attempts and a restart. Treat a configured future diagnostic procedure
separately from an incident already recovered in a live execution.

## Scheduler control can cancel its own recovery

Disabling a recurring job from its executing turn can cancel that same turn before
it checkpoints or returns a final report. A scheduler's cancellation label does not
by itself identify a human decision; inspect the initiating control action and its
execution scope before inferring that the owner abandoned the task.

Checkpoint accepted work, unresolved blockers and pending delivery before any
scheduler mutation. Determine whether the control affects future triggers only or
also the current run. Where supported and authorized, use post-run control or an
independent executor with a durable handoff; spawning a child alone does not prove
independence from parent cancellation. If safe control is unavailable, preserve the
checkpoint and report the limitation rather than claiming closure.

Separate business-output verification, run status, future schedule state and final
delivery evidence. Recovery should reuse validated outputs rather than repeating
acquisition just because the report was interrupted. Test the cancellation path
with a disposable synthetic job, not production work; a documented prevention
procedure remains unverified until that lifecycle is exercised.

Review question: if this control call terminates the caller immediately, where can
the next executor recover both the accepted output and the undelivered result?

## Verification invariants

- Accepted raw source bytes are retained unchanged.
- Checkpoints advance only after atomic acceptance of verified records.
- Missingness flags agree with the source, and false completeness flags fail an
  independent check.
- Held records/shards remain incomplete; they are not silently counted as zero.
- Attempt and external-usage budgets survive failures and restarts.
- Permission boundaries survive every recovery method.

Related: [State machines](PATTERN_INDEX.md#state-machine),
[idempotency](PATTERN_INDEX.md#idempotency), and
[learning capture](LEARNING_CAPTURE.md).
