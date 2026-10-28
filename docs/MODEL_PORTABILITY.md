# Model portability is a workflow contract

## Separate four dependency types

1. **Model dependency:** inference uses a named model/provider; switching models
   is possible only if the workload's output and tool-use contract still holds.
2. **Runtime dependency:** a connector may be hosted by one agent runtime even
   when its upstream service is unrelated to the model vendor. OAuth remains
   granted while a different runtime lacks a callable tool.
3. **Service dependency:** a provider-neutral tool can still route every request
   to one search, embedding, decision or storage service.
4. **Host dependency:** a portable Markdown skill can depend on binaries, native
   libraries, keychain custody, paths or operating-system behavior.

An interface named “provider-neutral” proves an abstraction, not tested
redundancy. A tool inventory proves exposure, not account authentication or use.

## Portable capability bundle

Retain a credential-free bundle containing:

- workflow/permission specification and standard-format data exports;
- skills plus explicit discovery/loading entry points;
- schemas, deterministic validators and representative synthetic fixtures;
- maintained adapters, dependency versions, licenses and runtime requirements;
- setup, protected reauthorization, restore and rollback instructions;
- acceptance results separated by model, runtime, service and host boundary.

Credentials belong in protected custody. Migration may require new OAuth consent;
exporting a hosted connector's token is not a portable integration strategy.
An index can be rebuilt from source, but incompatible embedding vectors cannot
be combined merely because their files are backed up.

### Instructions are portable; authority must be enforced

`AGENTS.md` and `SKILL.md` specify behavior and procedures. They neither grant
tool access nor enforce isolation. Verify instruction discovery/loading and
relative resource paths separately from filesystem sandboxing, tool policy,
OAuth scopes and user isolation. Preserve equal or narrower authority when
changing models; extra privileges do not compensate for weaker tool use.

## Staged task acceptance

Change one axis at a time and retain the incumbent:

1. Capture a representative workflow, expected outputs and an independent
   executable oracle on the working route. Set quality/latency/intervention
   tolerances before comparing implementations.
2. Keep the model and authentication route where supported; verify the native
   agent runtime, loaded instructions and actual tool execution.
3. Keep that runtime; test an alternate inference model against the same task,
   tool contract, permissions and oracle.
4. Restore onto the intended host and repeat acceptance. Local-model readiness
   also requires measured context, tool-calling, vision, quantization quality
   and latency; memory capacity alone is not parity.

Record runtime/model/service/host versions, fixture and oracle hashes, actual
results, denial/recovery checks, residual dependencies and rollback. Unsupported
combinations are coverage gaps, not permission to force a runtime. A synthetic
fixture does not prove a live connector or destination works. Separate removing
one model provider from eliminating all cloud services; neither implies the other.

## Pragmatic migration

An exclusive connector can be a valid temporary way to complete today's task.
Immediately create a backlog item with its dependency, verified behavior,
required replacement, acceptance oracle and rollback. Preserve the working route
until the replacement passes representative positive, denied, failure and restore
tests. Installation, catalogue presence and a successful provider probe each
cover only one part of that contract.

Prioritize dependencies on the critical path. Inventory optional hosted apps
before attempting to replace every exposed tool. Retaining a deliberately chosen
proprietary feature is compatible with portability when its residual limitation
and export boundary are explicit.

## Background work with a reserve

Use deterministic quota checks before optional inference, based on fresh
provider-reported allowance and the actual reset time. Unknown/stale account data
closes admission; token counts and context size are not subscription quota.
Keep an explicit reserve, bounded work units, and owner-facing reports separate.
Near-reset surplus can admit more useful work, not quota-burning filler.

Reporting can be an inference-free native command that reads maintained task
evidence. A low allowance can pause migration while still reporting that pause.
Do not evade the reserve by silently rerouting to paid inference elsewhere.

Validate the scheduler's real boundary too: a forced agent run may bypass a
condition trigger. Test budget predicates with independent boundary fixtures and
the script executor without inference; treat scheduled delivery as unverified
until a real receipt exists.

## Review questions

- If the model changes, does the tool survive? If the runtime changes, does it?
- Which credentials must be reauthorized rather than copied?
- Can another host load the skill and reproduce a representative result?
- What evidence permits retiring the incumbent without losing required behavior?

See [update lifecycle boundaries](UPDATE_LIFECYCLE_BOUNDARIES.md) and
[pattern index](PATTERN_INDEX.md).
