# Landing update — prepublication checkpoint

Date: 2026-11-23 · Base source: 9433ae6f102716f74a1fd219d5745cdc1ca437c1

## Scope

README landing/navigation, project index, a generic source-of-truth/release note, learning-log entry and this record. Existing technical notes, historical audits, planned lab status and the hub's MIT licence are unchanged. This is documentation-only: no runtime code, dependency, service or repository setting was changed.

The update was drafted and separately reviewed by AI assistants. Neither that review nor the source-hash checks are independent human legal review or security certification.

## Actual checks

- Integrator rechecked 45 Markdown files, 106 internal inline links and 48 fragments, excluding fenced examples: no missing or out-of-repository targets. This is not a browser rendering or all-Markdown-extension test.
- Whitespace checks passed for the complete five-file candidate. Gitleaks 8.30.1 tree and all 56 then-reachable commits reported no findings; final post-commit history verification is retained separately. A semantic review of the changed files also found no private operational data, client material, credentials or home-directory information.
- All reachable author/committer email metadata uses GitHub noreply identities. The existing MIT licence has no diff; linked Carbon Accounting Review retains its separate MIT-0 licence.
- Carbon Accounting Review's named ClawHub 1.1.0 was inspected separately: all 18 maintained source hashes match its reconstructed source tag, with registry-generated skill-card.md excluded. Its five-file development delta remains Unreleased; no new ClawHub version was published.
- The Carbon GitHub development repository exists privately at this checkpoint. Its reviewed development commit 3f44c485f804e6a1683ff2fee9ee502af91d5ba3 matched the local source; the hosted check run completed successfully with 17 deterministic release-contract tests. This does not establish model accuracy, legal compliance or runtime sandbox enforcement.
- Source-of-truth guidance and the exercise in this hub remain learning material. The proposed exercise has not been executed in this repository. Existing model-behavior results remain PARTIAL, and labs remain planned.

## Publication boundary

This record is a **local preparation checkpoint**, not a receipt for a public push or anonymous availability. Public authorization is still required for this candidate. The intended paired operation is to make the curated Carbon development repository public first, then push this exact landing update; the landing's source link must not be presented as anonymously available before that step succeeds.

Do not substitute prior September or November audits for this change. Keep source identity, remote delivery, anonymous visibility, model behavior and legal/professional acceptance separate. No force-push, credential/security broadening, registry publication, scheduled sync or automated publishing hook is authorized by these local checks.
