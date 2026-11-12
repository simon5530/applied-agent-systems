# Designing and adopting agent skills

An agent skill is a reusable operating procedure: it tells an agent **when** a
workflow applies, **what sequence** to follow, and **how to know it is complete**.
It does not add intelligence by itself. Its value comes from making proven behavior
repeatable across sessions and projects.

## Evaluation case

The public repository [mattpocock/skills](https://github.com/mattpocock/skills)
was reviewed as a possible addition to this learning environment. The evaluated
snapshot was commit
[`3cca18b`](https://github.com/mattpocock/skills/tree/3cca18b368ae95cdbdebbff572ccafa662551015).
It is MIT-licensed, actively maintained, and organizes small engineering practices
as composable skills rather than one end-to-end framework.

## Lessons worth transferring

### 1. Context pointers are routing rules

A skill description or a line in `AGENTS.md` is not merely documentation. It is a
pointer that determines when the agent loads more instructions. A useful pointer
names the material and the distinct situations that should trigger it.

**Practical consequence:** keep always-loaded instructions short, and move
branch-specific detail behind precise pointers.

### 2. Progressive disclosure protects attention

Put the actions required on every run in the main skill file. Move optional formats,
examples, and branch-specific rules into referenced files. This reduces context load
without hiding steps needed for successful completion.

### 3. Completion criteria prevent premature stopping

Every workflow step should end with an observable condition. "Investigate the bug"
is vague; "one deterministic command reproduces the reported symptom" is checkable.
Strong criteria are both clear and exhaustive.

### 4. Shared language compounds

A small domain glossary aligns product discussion, file names, functions, tests, and
agent output. Precise terms reduce ambiguity and repeated explanation. Architectural
decision records are most useful only when a choice is hard to reverse, surprising
without context, and based on a real trade-off.

### 5. Debugging starts with a feedback loop

Before forming a theory, build a tight signal that can reproduce the exact symptom.
Then minimise, rank falsifiable hypotheses, instrument one variable at a time, fix,
and verify the original scenario again. Logs and captured artifacts must be redacted.

### 6. Skills are supply-chain dependencies

Skill files influence tool use and may contain scripts. Treat them like code:

1. Review the source, referenced files, scripts, and license.
2. Pin the evaluated revision for the initial installation.
3. Install only the skills that solve a current problem.
4. Review upstream diffs before updating.
5. Avoid repository helper scripts that overwrite existing skill directories.

## Context loading is an executable contract

A file being present does not prove that a particular runtime or delegated worker
loads it. Separate discovery metadata, automatically loaded instructions, explicit
reads and retained session context. Check version-specific loading rules for the
actual execution path; do not assume that a child inherits its parent's persona,
private memory or repository instructions. Execution-directory instructions and a
configured workspace bootstrap can have different scopes.

Keep the always-loaded core small, but retain required safety and acceptance rules.
Route optional detail through precise triggers and explicit read pointers. Prose
restrictions do not enforce permissions: a command-execution tool may still write
when a task packet says "read-only." Enforce that boundary in tool policy or an
appropriate sandbox, and test the actual denied operation separately.

Use a bounded delegation packet rather than a transcript:

- objective, permitted inputs and their provenance or revision;
- exact allowed effects, forbidden effects and escalation boundary;
- output schema, independent acceptance checks and evidence locations;
- completion destination, timeout, retry budget and unresolved-blocker format.

A worker returns findings and evidence, not a new grant of authority. Assign one
canonical integrator to reconcile versions and update shared durable conclusions;
other workers propose changes. Keep stated facts, observations and inferences
distinct, and explicitly supersede outdated conclusions. This coordination rule
does not itself enforce filesystem or memory-write isolation.

### Bounded validation exercise

Use synthetic instruction markers and a disposable fixture, never private memory.
Inspect actual bootstrap/read receipts for a fresh parent and child, then ask each
to return its intended source marker. A model echo alone is not proof of loading.
Confirm an intentionally unprovided marker remains unavailable and the enforcement
layer rejects a forbidden write. Feed the integrator conflicting revisions and
verify stale results cannot silently replace newer conclusions or grant authority.

Record missing visibility as unverified coverage; do not broaden permissions to
complete a probe. These are proposed checks, not an executed runtime lab. Measure
success, rework and total resource use on comparable repeated tasks before claiming
that fewer instructions or more workers improved performance.

**Review question:** Which receipt proves the child consumed the intended rules,
which control limits its effects, and who resolves conflicting durable conclusions?

## Recover fixture permissions without weakening confinement

An offline helper failure can originate in the fixture rather than the helper or
sandbox policy. A copied read-only fixture may retain its mode and reject an
otherwise permitted overwrite. Inspect effective identity, copied mode, intended
output location and policy-denial evidence before changing access controls.

When the test contract requires a writable copy, recreate only that disposable copy
with the intended ownership and mode inside the existing sandbox. Preserve immutable
sources, read-only source mounts and mandatory access controls. A writable backing
file mode does not make a read-only mount writable; verify both independently. Never
disable confinement merely to make the helper pass.

Rerun the affected case, compare source hashes and retain previously accepted outputs.
Record which cases were rerun rather than claiming a new full-suite execution. Keep
offline helper behavior, interactive visual behavior, actual model provenance and
sandbox enforcement as separate acceptance dimensions. A passing suite proves only
its encoded scope.

**Proposed exercise (not executed here):** reproduce an overwrite failure using a
synthetic read-only fixture; repair only its disposable copy. Verify the original
hash is unchanged and a forbidden write outside the allowed output area still fails.
Preserve denial receipts and explicitly label untested acceptance dimensions.

**Review question:** Which observation distinguishes a fixture-mode error from a
policy denial, and which negative test proves the repair preserved confinement?

## Publishing is a content-identity and state-transition contract

A publisher can transform a local directory before upload: reserved filenames,
ignore rules or generated metadata can change the bundle. Local review therefore
does not establish which bytes the registry received.

1. Freeze an explicit upload allowlist with relative names, sizes and content
   hashes. Exclude private evidence and credentials.
2. Compare that inventory with the publisher's dry run. Investigate every missing,
   added or transformed file against the installed publisher's version and rules.
   Resolve reserved-name collisions without bypassing validation, repair references
   and repeat the comparison before uploading.
3. Keep license authorization and attribution separate from security review and
   behavioral acceptance. A permissive license, governance card or static scan is
   not evidence of runtime safety or domain correctness.
4. Separate upload acceptance, automated checks, public availability and exact-content
   verification. Accepted-but-pending is not published. Retain the receipt and
   inspect the same version before retrying an uncertain outcome.
5. Retrieve the remote manifest or artifact after checks finish. Compare its
   documented payload with reviewed hashes and intended public metadata. If
   retrieval is unavailable, mark content identity unverified; do not infer a match
   or submit a duplicate release.

An asynchronous release needs a supported completion path or an explicit blocker
and resume condition. Confirm follow-up registration before claiming it exists;
never bypass registry checks to close a task.

**Proposed exercise (not executed here):** a mock publisher drops a reserved file
from a synthetic bundle. Detect the mismatch, rename the file and repair references.
Simulate accepted-but-pending publication; verify no resubmission, bypass or success
announcement occurs. Finally compare a retrieved payload with the inventory,
including a negative case with one changed byte.

**Review question:** Which receipt establishes acceptance, which proves public
availability, and which proves the published bytes match the review?

## Selective adoption

| Skill | Decision | Reason |
|---|---|---|
| `diagnosing-bugs` | Adopt | Adds a disciplined, redaction-aware feedback loop for hard failures. |
| `domain-modeling` | Adopt | Improves terminology and keeps ADRs focused on consequential decisions. |
| `writing-for-agents` | Adopt | Improves skill and `AGENTS.md` design through pointers, disclosure, and pruning. |
| `teach` | Learn from, do not install | Retrieval practice and spacing are useful, but its HTML course structure duplicates this repository's Markdown learning hub. |
| `grilling` | Do not install | Its default of exhaustive questioning conflicts with an autonomy-first collaboration style. |
| `research` and `code-review` | Defer | Their required sub-agent workflows should be adopted only when the runtime policy and project need justify them. |
| Full workflow bundle | Do not install | Issue-tracker and orchestration conventions would add process before a demonstrated need. |

The three adopted skills were installed from the pinned reviewed revision rather
than through a floating `latest` command. The upstream repository passed a local
Gitleaks scan; installation still does not imply that future updates are trusted
automatically.

## Review questions

1. What is the difference between a skill body and its context pointer?
2. Which content must remain inline, and which content can be progressively disclosed?
3. How can a completion criterion change an agent's behavior?
4. Why is a skill installation a supply-chain decision?
5. What exact signal should exist before debugging moves to hypotheses?
