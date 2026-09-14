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
