# Fixture-recovery learning publication audit — 2026-11-11

Scope: generalized fixture-mode diagnosis, confinement-preserving repair and
independent acceptance dimensions. No private operational evidence is published.

- Complete change reviewed for semantic privacy: no raw conversations, personal
  context, credentials, identifiers, private endpoints or local paths added.
- Relative Markdown links and anchors passed (62); whitespace checks passed. No external
  references, executable code, dependencies or third-party assets added.
- Gitleaks 8.30.1 passed current-tree and all-ref reachable-history scans (48
  existing commits); final tree and resulting commit are rescanned before push.
- Effective author/committer and reachable-history addresses use GitHub noreply.
- Documentation-only repository has no executable test suite; the proposed sandbox
  exercise was not executed here and does not certify runtime confinement.
- Existing external links and remote security controls were not re-audited.
  Completion requires a post-push comparison against the remote branch commit.

## Tool-input recovery

Two malformed command submissions failed before dispatch, with no filesystem
mutation. A single escaped command string then dispatched successfully. Keep source
boundaries explicit across nested runtimes; distinguish input rejection, process
exit and repository effects rather than retrying a mutation blindly.

The first link-check expression matched zero links; a nonzero-coverage assertion
and a simpler parser corrected the oracle before publication. One corrective
script failed parsing before mutation; the corrected check then passed. A zero-match
check is not evidence of valid documentation links.
