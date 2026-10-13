# Update lifecycle boundaries: executable retention is not mutable state

## Failure model

A self-updating service needs to preserve the updater's executable dependencies
while replacing its installed package. A recovery journal has a different purpose:
it records mutable transaction progress and must remain under one state owner.

Hard-linking an executable can preserve old bytes efficiently. Hard-linking a
mutable SQLite recovery journal creates a second pathname to the same inode,
not an independent backup. If an activation guard requires one link, a retention
inventory that accidentally includes the journal makes a valid state file fail
the guard. The message may say “unsafe permissions” even though file mode is right.
Failure cleanup can remove the extra link before inspection, hiding the transient.

## Evidence and recovery

1. Trace the reported guard to its actual predicates: mode, ownership, identity,
   link count, and path custody are different checks.
2. Reproduce the boundary in an isolated fixture using the real planner/guard.
   Distinguish deterministic reproduction from a captured production transient.
3. Preserve safety checks. Fix executable inventory to exclude recovery state and
   reject dependencies whose links target it.
4. If the old updater itself is defective, an already-fixed candidate cannot fix
   the code currently performing retention. Use a documented independent operator
   installation path, keeping the service stopped during in-place package replacement.
5. Verify installed and running versions, health, plugins, channel ingress, and
   actual model routes separately. A diagnostic patch is not a completed upgrade.

The observed updated OpenClaw 2026.10.2 planner excludes package recovery artifacts.
A direct exported-planner synthetic test excluded the control/journal subtree,
kept the journal at one link, and retained ordinary runtime dependencies. This
is boundary verification, not a complete updater or live SQLite validation.

## Prevention contract

- Inventory executable dependencies separately from journals, receipts and helpers.
- Make the specification inspectable: excluded state remains at one link; ordinary
  dependencies remain available; malicious state-targeting links are rejected.
- Stop repeating a failure after its mechanism is reproducible. Doctor/lint success
  does not prove the later package-swap phase succeeds.
- Check supported maintenance paths before declaring installation impossible.
  Opening another Terminal is not evidence that an agent has released its runtime
  or obtained a coordinated shutdown/completion path.
- Cleanup uses dependency and lease evidence, not age or identical bytes alone.
  Record exact recoverable moves; preserve rollback data until its retirement is justified.

## Review questions

- What needs to survive package replacement: immutable code or mutable state?
- Could error cleanup erase the most useful diagnostic evidence?
- Which process executes the bug: the installed updater or the candidate?
- What proves completion independently of a successful command exit?

Reference: [OpenClaw manual update lifecycle](https://docs.openclaw.ai/install/updating/update-methods#alternative-manual-npm-pnpm-or-bun).
