# Publication audit

Last verified: YYYY-MM-DD

Reviewed commit: `<full-commit-sha>`

## Scope

- current repository tree and working-tree state;
- all commits, tags, and reachable Git objects;
- commit author and committer metadata;
- dependencies, bundled assets, documentation, and generated artifacts;
- GitHub visibility, default branch, security controls, and anonymous behavior.

## Evidence

- Secret scanner and version: `<tool and version>`
- Current-tree result: `<result>`
- Complete-history result: `<result>`
- Semantic privacy review: `<scope and result>`
- Binary, screenshot, and metadata review: `<scope and result>`
- Dependency and license checks: `<commands and result>`
- Links, tests, schemas, and reproducibility: `<commands and result>`
- Commit identity and remote commit: `<result>`
- GitHub security controls: `<result>`
- Anonymous repository, README, and API checks: `<result>`

## Findings and resolutions

- `<finding, resolution, and verification>`

Write `None` only after reviewing the evidence; do not omit this section.

## Residual limitations

- Pattern scanning cannot prove the absence of every sensitive semantic detail.
- `<project-specific limitation or evidence gap>`

## Decision

`PASS` or `BLOCKED`

Reason: `<concise evidence-based decision>`
