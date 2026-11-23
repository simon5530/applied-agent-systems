# Source of truth: development is not a registry release

**Learning note — 2026-11-23.**

**[suggested] Generic learning workflow:** use one explicit project repository for
development and a separate, deliberate registry release boundary. This note defines
review criteria; it does not report that a particular project has completed them.

## Give each surface one job

| Surface | What it establishes | What it does not establish |
|---|---|---|
| Local project Git working tree | Editable development state; changes can be reviewed before staging | Published availability, a release, or even a committed snapshot |
| Local Git commit | A specific recorded source revision | Remote delivery, public access or registry content identity |
| Authorized GitHub development repository | Shared, reviewable development history at a verified commit | That its default branch equals the released skill |
| Named registry release | A distribution version, with its retrieved payload and manifest | That all current development changes shipped, or that runtime behavior is correct |
| Learning hub | Reusable explanation and navigation | The authoritative implementation, private evidence or released payload |

Choose a canonical development source and record its role. Use local Git → reviewed
GitHub development history → explicit registry releases, not competing editable
copies with silent bidirectional overwrites. A planned GitHub repository is still
pending until authorized publication and anonymous access are verified. A registry
release can exist before that development repository becomes public.

## Separate development from release intent

1. **Scope the project.** Review only its intended files. Use an explicit staging
   list and upload allowlist; never blindly sync an agent workspace, home directory,
   memory store, private configuration or neighboring project.
2. **Review development changes.** Inspect the diff, provenance, licences and
   relevant checks. Keep local/unreleased changes labelled as such. A development
   commit or push does not automatically request a registry release.
3. **Freeze a release candidate.** Record the full source commit identifier, chosen
   release version and allowed payload inventory with relative names, sizes and
   cryptographic digests such as SHA-256. Document any export/build transformation.
   A floating branch or tag name alone is not immutable content evidence.
4. **Reconcile packaging.** Compare publisher dry-run output against that inventory;
   resolve ignored/reserved files, generated metadata and repaired references before
   upload. Follow the [skill publication contract](AGENT_SKILLS.md#publishing-is-a-content-identity-and-state-transition-contract).
5. **Release deliberately.** Obtain the required release authorization and run the
   [publication gate](PUBLICATION_SECURITY_GATE.md). Publish only the reviewed
   candidate. Not every commit deserves a release; select a meaningful, validated
   change and version it explicitly.
6. **Verify the remote result.** Confirm the GitHub commit separately from registry
   acceptance, checks and public availability. Retrieve the exact named registry
   version and compare its payload digests with the reviewed export. If access or
   identity cannot be checked, retain an explicit blocker rather than declaring a
   match or publishing a duplicate version.

## Keep an immutable identity chain

Record **source commit → export manifest/digest → registry version → retrieved
payload digest**, plus tool versions, verification date and any packaging exclusions.
Treat a named version as a locator, not sufficient proof of immutable bytes: retain
digests and investigate any later mismatch. Do not silently replace a reviewed
release with different content under the same version.

If an archive includes nondeterministic packaging metadata, distinguish the archive
digest from the per-file payload manifest; document the comparison boundary instead
of pretending the two digests should be equal. Missing remote payload access leaves
content identity **unverified**, even if upload returned success.

## Keep readiness claims independent

Copyright permission, source publication, registry checks, offline tests, model
behavior, sandbox enforcement and production acceptance answer different questions.
A release can be publicly available while model-behavior validation remains PARTIAL.
A proposed jurisdiction/report update is not part of the public release merely
because it exists in the development tree. No layer grants new tool authority or
permission to disclose private evidence.

**[suggested] Exercise, not executed here:** prepare a synthetic candidate, then
change one exported byte and verify that manifest comparison rejects it. Simulate
accepted-but-pending publication and confirm there is no duplicate upload or success
claim. Finally advance the development branch without a release and confirm the
release status still names the old reviewed commit and payload.

**Review question:** which exact commit and payload did a user receive, what is
still unreleased, and which acceptance dimension remains unverified?

Related: [project applications](../projects/README.md),
[learning capture](LEARNING_CAPTURE.md), and [security rules](../SECURITY.md).
