# Agent system mental model

## Core components

~~~mermaid
flowchart LR
    User[User or device] --> Channel[Channel / API]
    Channel --> Gateway[Gateway]
    Gateway --> Routing[Identity + binding]
    Routing --> Agent[Agent]
    Agent --> Session[Session context]
    Agent --> Memory[Durable memory]
    Agent --> Tools[Tools / capabilities]
    Agent --> Model[Primary + fallback models]
~~~

## Agent

An agent is a durable execution identity: instructions, model policy, memory access,
workspace, and tools. Changing a chat title does not rename or isolate an agent.

## Session

A session is one conversation's short-term state. One agent can own many sessions:
a home session, one per channel peer, automation runs, and device/API sessions.

## Workspace

A workspace is the agent's file-backed operating context. Separate workspaces help
prevent accidental sharing, but they are not automatically equivalent to VM/container
isolation.

## Gateway

The gateway accepts channel/API traffic, authenticates requests, applies routing,
loads agent configuration, and returns responses. It is a control plane and therefore
requires stronger protection than a single-purpose chat endpoint.

## Channel and binding

A channel connects an external platform. A binding maps trusted provider-issued
identity attributes to an agent. Display names are presentation, not authorization.

## Memory layers

- **Current context:** tokens visible in the active session.
- **Durable files:** curated preferences, decisions, and daily notes.
- **Search index:** chunks and embeddings used to retrieve relevant durable memory.

An index can be rebuilt without deleting the source memory files. A stale index affects
recall, not necessarily storage.

## Tools and authority

Tools convert model output into real effects. Evaluate tools by reversibility,
external impact, data sensitivity, and the strength of the runtime boundary.
