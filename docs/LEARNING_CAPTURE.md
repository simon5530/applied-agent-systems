# Learning capture workflow

This repository captures reusable lessons from real agent-system work without
turning chat transcripts into public documentation.

## Routing rule

| Learning type | Destination |
|---|---|
| Project requirement, ADR, implementation, or verification evidence | Corresponding project repository |
| Reusable mental model, protocol, design pattern, lab, or review question | `applied-agent-systems` |
| Personal preference, identity, credential, endpoint, or private operational detail | Local private memory or configuration only |

## Trigger

Capture at a meaningful milestone: a decision is made, a failure is diagnosed, a
protocol is applied, a security boundary changes, or a verification produces
reusable evidence. Context-window compaction is automatic and therefore is not a
reliable publication trigger.

## Publication gate

1. Convert the lesson into an explanation, decision, lab, or evidence update; do
   not publish raw conversation transcripts.
2. Remove personal identifiers, credentials, private endpoints, local paths, and
   account-specific operational details.
3. Review the diff and scan the current tree plus reachable Git history for
   secrets.
4. Verify affected links, commands, tests, or external visibility.
5. Commit with GitHub noreply metadata, push, and report the files changed.

The goal is a useful engineering record, not a complete diary. No durable lesson
means no repository update.
