# Applied Agent Systems

A documentation-first learning hub for understanding, designing and evaluating
practical AI agent systems: **what can act, under whose authority, what can fail,
and what evidence establishes completion?**

## Current state — 2026-11-23

**Documentation-first, actively maintained.** This is a growing collection
of reusable mental models, engineering patterns, learning notes and project links,
not a runtime framework or a production-readiness certificate.

The linked documents below form the repository map as of 2026-11-23. The [labs page](labs/README.md) specifies a lab format and
lists **planned** labs; it does not contain implemented, executed lab packages.
Project implementation and acceptance evidence belong in their owning repositories.

## Start with a question

| If you want to… | Start here | Then explore |
|---|---|---|
| Understand agent/session/workspace/tool boundaries | [Mental model](docs/MENTAL_MODEL.md) | [Protocols](docs/PROTOCOL_INDEX.md) · [Deployment topologies](docs/DEPLOYMENT_TOPOLOGIES.md) |
| Recover a failed workflow without weakening its guards | [Bounded task recovery](docs/BOUNDED_TASK_RECOVERY.md) | [Update lifecycle boundaries](docs/UPDATE_LIFECYCLE_BOUNDARIES.md) · [Engineering patterns](docs/PATTERN_INDEX.md) |
| Decide whether an effect needs authority or approval | [Tools and authority](docs/MENTAL_MODEL.md#tools-and-authority) | [Human approval gate](docs/PATTERN_INDEX.md#human-approval-gate) · [Send-only coordination](docs/PATTERN_INDEX.md#send-only-coordination-is-not-delegated-authority) |
| Review or publish an agent skill | [Skill design and adoption](docs/AGENT_SKILLS.md) | [Development vs. registry releases](docs/SOURCE_OF_TRUTH_AND_RELEASES.md) · [Publication gate](docs/PUBLICATION_SECURITY_GATE.md) |
| Assess AI transparency and open-source responsibility | [Dated governance note](docs/AI_TRANSPARENCY_OPEN_SOURCE.md) | [Role-and-activity pattern](docs/PATTERN_INDEX.md#regulatory-scope-follows-role-and-activity-not-licence) |

## What the hub covers now

These are documentation topics, not claims that each boundary has passed a live test.

| Area | Questions and navigation |
|---|---|
| Runtime and topology | Agent, session, gateway, channel, binding and memory; [deployment and migration](docs/DEPLOYMENT_TOPOLOGIES.md); [model/workflow portability](docs/MODEL_PORTABILITY.md). |
| Lifecycle and recovery | Immutable executable retention vs. mutable state, runtime dependencies, consent and handoff; [maintenance boundaries](docs/UPDATE_LIFECYCLE_BOUNDARIES.md); [checkpoints, retry budgets and incomplete coverage](docs/BOUNDED_TASK_RECOVERY.md). |
| Tool authority | Least privilege, scoped approval, correction handling and execution-context authorization; [pattern index](docs/PATTERN_INDEX.md). Instructions and message transport are not enforced isolation or delegated privilege. |
| Evidence and artifacts | [Verification over trust](docs/PATTERN_INDEX.md#verification-over-trust), [typed artifact oracles](docs/PATTERN_INDEX.md#typed-boundary-oracles-for-generated-artifacts), source integrity and native acceptance are separate checks. |
| Skills and releases | Context loading, bounded delegation, fixture recovery and [published-payload identity](docs/AGENT_SKILLS.md#publishing-is-a-content-identity-and-state-transition-contract); [source-of-truth and explicit releases](docs/SOURCE_OF_TRUTH_AND_RELEASES.md). |
| AI transparency and open source | [Actor, activity, audience, jurisdiction and applicable date](docs/AI_TRANSPARENCY_OPEN_SOURCE.md), rather than a licence-based compliance verdict. The legal note is a **2026-11-22 snapshot**, AI-assisted and without independent human legal review. |
| Learning and application | [Learning log](docs/LEARNING_LOG.md), [capture workflow](docs/LEARNING_CAPTURE.md), [planned labs](labs/README.md) and [project applications](projects/README.md). |

## Project connections

[Project applications](projects/README.md) connects the notes to OpenClaw Wearables,
Agent Liaison, Mini Energy AI Lab and Carbon Accounting Review. A topic connection
is not a fresh implementation or deployment audit.

**Carbon Accounting Review** connects domain review procedures to these engineering
patterns. Its [ClawHub release](https://clawhub.ai/simon5530/skills/carbon-accounting-review)
is **1.1.0**, with **18 maintained text files** under **MIT-0**; source hashes were
checked against that named release on 2026-11-23. The
[GitHub development source](https://github.com/simon5530/carbon-accounting-review)
keeps local jurisdiction/report refinements labelled **Unreleased**. Packaging and
release-tool tests do not upgrade its **PARTIAL** model-behavior validation into
production readiness, legal assurance or a sandbox-security pass. See the
[project status](projects/README.md#carbon-accounting-review).

## How to read the evidence

- **[observed]** means a bounded check with a date and source, not continuous coverage.
- **[stated]** identifies a supplied status; it is not independent verification.
- **[inferred]** is an interpretation with uncertainty, not an observed result.
- **[suggested]** marks a proposed workflow or exercise, not completed implementation.
- A proposed check, static scan, licence or successful command does not establish
  model behavior, enforced sandbox isolation, legal compliance or live recovery.

The learning loop is **observe → explain → connect → propose a bounded exercise →
verify success and failure paths → apply → review**. Until an exercise has actual
receipts, keep it labelled planned rather than turning the loop into a maturity claim.

## Where things belong

| Content | Authoritative home |
|---|---|
| Reusable concept, protocol, pattern or learning exercise | This hub |
| Requirement, ADR, implementation, tests and project-specific evidence | Owning project repository |
| Reviewed development history | Explicit project Git repository and commit; see [source-of-truth guidance](docs/SOURCE_OF_TRUTH_AND_RELEASES.md) |
| Released skill payload | Named registry version, independently matched to reviewed content |
| Preferences, identities, credentials, private endpoints and operational context | Private storage only; never bulk-synced into the hub |

## Contributing and publication

Capture a reusable lesson at a meaningful milestone, not every conversation or
commit. Use the [learning-note template](templates/LEARNING_NOTE.md), follow
[security rules](SECURITY.md), and run the [publication security gate](docs/PUBLICATION_SECURITY_GATE.md)
before authorized publication. Git development and registry releases are separate
approval and verification boundaries; neither implies release-on-every-commit.

- [Decisions](docs/DECISIONS.md) explain the Markdown-first approach and evidence ownership.
- [Baseline publication audit](docs/PUBLICATION_AUDIT.md) was last verified **2026-09-21**;
  it is historical, not a current blanket pass.
- [AI-governance documentation audit](docs/PUBLICATION_AUDIT_2026-11-22_AI_GOVERNANCE.md)
  covers that dated note's bounded scope.
- [Landing-update check record](docs/PUBLICATION_AUDIT_2026-11-23_LANDING.md) records
  the scope, completed local checks and remaining publication boundary.
- [Publication-audit template](templates/PUBLICATION_AUDIT.md) defines what a new receipt needs.

## License

This hub remains under the [MIT License](LICENSE). Linked projects and registry
artifacts have their own licences; the skill's MIT-0 does not change this hub's MIT.
