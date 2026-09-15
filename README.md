# Applied Agent Systems

A hands-on learning hub for designing, operating, securing, and evaluating practical
AI agent systems.

## Status

**Work in progress — continuously updated.** This public learning repository grows
alongside hands-on projects. Notes may be refined as experiments reveal better
explanations or engineering trade-offs. Reusable concepts and lab templates live
here; project-specific implementation evidence remains in the corresponding
project repositories.

## Why a separate learning hub?

Agent engineering knowledge was beginning to repeat across wearable integration,
scheduling, channel routing, memory, model fallback, and security work. A central
hub creates one durable map without turning every project README into a textbook.

| Content | Authoritative home |
|---|---|
| Reusable mental model, protocol, pattern, or lab | This repository |
| Project requirement, ADR, implementation, test evidence | Project repository |
| Private preference, identity, endpoint, credential, personal context | Local private memory/config only |

## Learning loop

1. **Observe** a real implementation problem.
2. **Explain** the concept in plain language.
3. **Connect** it to a protocol or engineering pattern.
4. **Practice** it in a small reproducible lab.
5. **Verify** both the success and failure path.
6. **Apply** it in a project.
7. **Review** with questions that test understanding, not memorization.

## Current map

- Runtime: agent, session, workspace, gateway, channel, binding, memory, tools.
- Reliability: fallback, health checks, retries, idempotency, TTL, state machines.
- Security: loopback, reverse proxy, private networks, OAuth 2.0, least privilege.
- Human interaction: approval gates, authority labels, privacy, human escalation.

## Repository map

- [Mental model](docs/MENTAL_MODEL.md)
- [Protocol index](docs/PROTOCOL_INDEX.md)
- [Pattern index](docs/PATTERN_INDEX.md)
- [Agent skill design and adoption](docs/AGENT_SKILLS.md)
- [Learning log](docs/LEARNING_LOG.md)
- [Learning capture workflow](docs/LEARNING_CAPTURE.md)
- [Decisions](docs/DECISIONS.md)
- [Labs](labs/README.md)
- [Project applications](projects/README.md)
- [Learning-note template](templates/LEARNING_NOTE.md)
- [Security rules](SECURITY.md)

## Publication direction

The long-term portfolio value is not a list of commands. It is evidence that common
agent concepts can be explained, tested, connected to business risk, and transferred
across projects.

## License

Released under the [MIT License](LICENSE).
