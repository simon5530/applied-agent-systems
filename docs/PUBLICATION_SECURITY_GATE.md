# Publication security gate

This procedure is the reusable release gate for repositories that may be pushed to
GitHub or made public. A private repository is access control, not permission to
commit credentials or personal data.

Project repositories keep their own `SECURITY.md` for project-specific data,
authority, threat, and disclosure rules. They also keep a dated publication audit
as evidence that this procedure was actually run. This document is the shared
procedure; it is not evidence that another repository passed the gate.

## When to run the gate

Run the complete gate:

- before the first push to a remote or a private-to-public visibility change;
- before a release or meaningful portfolio milestone;
- after adding logs, screenshots, fixtures, generated files, or third-party assets;
- after changing authentication, authorization, data flow, or deployment boundaries;
- after any suspected credential or personal-data exposure.

For routine commits, run the repository's faster local checks. Run the complete gate
again when the change can affect publication safety.

## Gate contract

The gate fails closed. Do not push, release, or change visibility while any finding is
unexplained, while the intended repository scope is ambiguous, or when the evidence
cannot distinguish a real pass from a skipped check.

Record tools and versions, scope, results, residual limitations, and the reviewed
commit in the project repository's publication audit. A scanner pass is supporting
evidence, not proof that semantically private information is absent.

## 1. Confirm scope and repository state

1. Confirm the working directory and remote point to the intended project only.
2. Review `git status`, staged changes, unstaged changes, and untracked files.
3. Review the diff that will be published and the commits not yet on the remote.
4. Confirm no parent workspace, memory store, user profile, local configuration, or
   unrelated project is included.
5. Confirm commit author and committer addresses use an appropriate public identity,
   such as a GitHub noreply address.

Useful checks:

```sh
git status --short --branch
git remote -v
git diff --check
git diff
git diff --cached
git log --format='%h %an <%ae> | %cn <%ce>' --all
```

## 2. Scan secrets in the tree and complete history

Use a maintained secret scanner against both the current tree and every reachable Git
object. Record the scanner version and exact scope in the audit. Do not weaken or
exclude a rule merely to obtain a passing result; document and independently review a
false positive.

At minimum, look for:

- API keys, bearer tokens, passwords, cookies, OAuth material, private keys, and
  certificates;
- `.env` files, secret-store exports, credential files, databases, logs, and backups;
- secrets embedded in deleted files, old commits, tags, or other reachable objects.

Redact findings in captured output. Never paste a live secret into an issue, chat,
audit, or commit message.

Example with Gitleaks 8.x:

```sh
gitleaks version
gitleaks dir --redact --no-banner .
gitleaks git --redact --no-banner .
```

## 3. Perform a separate semantic privacy review

Secret scanners do not reliably detect personal or operational context. Inspect text,
filenames, generated artifacts, and examples for:

- real names, personal email addresses, phone numbers, channel or account identifiers;
- home-directory paths, hostnames, private IP addresses, tailnet names, device IDs,
  auth-profile IDs, and private endpoints;
- real messages, calendar records, contacts, preferences, memory, or user profiles;
- screenshots containing notifications, contact lists, browser profiles, credentials,
  or identifying UI;
- logs or test fixtures copied from a live environment.

Replace private values with explicit placeholders or synthetic fixtures. Describe
roles and observable behavior instead of publishing raw operational data.

## 4. Inspect binaries, screenshots, and generated artifacts

1. Enumerate non-text files, archives, databases, logs, and generated outputs.
2. Inspect image and document metadata as well as visible content.
3. Confirm build outputs and caches are excluded unless intentionally distributed.
4. Confirm each retained artifact is necessary, reviewable, and licensed for release.

## 5. Check dependencies, licenses, and attribution

1. Run the ecosystem's dependency and vulnerability checks.
2. Verify the repository license matches the intended use.
3. Record licenses and attribution for bundled code, data, fonts, images, and other
   assets.
4. Confirm product names and trademarks are used only as permitted references.

Do not interpret a clean dependency audit as a privacy or authorization review.

## 6. Verify documentation and reproducibility

1. Validate internal links and important external links.
2. Check shell syntax, schemas, tests, and repository-specific acceptance criteria.
3. Reproduce the documented setup from a clean checkout or equivalent isolated
   environment without relying on private files or undocumented state.
4. Verify positive, unauthorized, failure, and restart-persistence paths where they
   apply.
5. Ensure verified, planned, and unknown claims are clearly separated.

## 7. Verify GitHub controls and public behavior

For repositories that are or will become public, verify the intended default branch,
visibility, license, and vulnerability-reporting path. Enable and check the available
secret scanning, push protection, dependency alerts, and automated security updates.
Enable dependency alerts before automated security fixes; GitHub rejects the latter
when the underlying alerts are disabled.

After an authorized push or visibility change, independently verify:

- the remote commit matches the reviewed local commit;
- anonymous users can see only the intended repository and files;
- the README and important links render correctly;
- private branches, artifacts, releases, issues, or metadata were not published by
  mistake.

An authenticated view or successful `git push` is not proof of anonymous behavior.

## 8. Record the audit

Copy [the publication audit template](../templates/PUBLICATION_AUDIT.md) into the
project repository, usually as `docs/PUBLICATION_AUDIT.md`. Record concrete results,
not only checked boxes. Keep historical evidence truthful: update the verification
date and commit when rerunning the gate rather than implying continuous coverage.

## Credential incident recovery

If a credential reaches Git history:

1. stop publication and assume the credential is exposed;
2. revoke or rotate it before relying on history cleanup;
3. identify every affected ref, clone, artifact, log, and downstream system;
4. remove the material and rewrite affected history when appropriate;
5. rescan the current tree and complete rewritten history;
6. verify the replacement credential and dependent services;
7. document the incident without reproducing the secret.

Deleting the latest file or making the repository private does not invalidate a leaked
credential and does not remove earlier Git objects from existing clones.
