# Protocol and standard index

| Protocol / standard | Problem solved | Agent-system application | First project |
|---|---|---|---|
| HTTP / REST | Request-response interoperability | Model-compatible APIs, health checks | OpenClaw Wearables |
| JSON | Structured portable data | Agent requests, tool inputs, configuration | OpenClaw Wearables |
| TLS / HTTPS | Transport confidentiality and server identity | Private wearable-to-gateway traffic | OpenClaw Wearables |
| WebSocket | Long-lived bidirectional connection | Control UI and remote node connection to a gateway | OpenClaw Wearables |
| Reverse tunnel | Outbound-established public ingress | Delivering signed SaaS webhooks to a loopback service | OpenClaw Wearables |
| Overlay network | Private addressing across networks | Tailnet access for wearables, operators, and nodes | OpenClaw Wearables |
| OAuth 2.0 | Scoped delegated access | Calendar access without password sharing | Agent Liaison |
| Webhook | Event-driven server notification | LINE channel messages and calendar changes | Both |
| iCalendar (RFC 5545) | Portable calendar representation | Events, recurrence, VFREEBUSY | Agent Liaison |
| CalDAV (RFC 4791) | Standard calendar access | Provider-neutral free/busy queries | Agent Liaison |
| IANA time zones | Unambiguous civil time | DST-safe scheduling decisions | Agent Liaison |
| OpenAI-compatible API | Shared model request schema | BYOA device integration | OpenClaw Wearables |
| A2A Protocol 1.0 | Discovery, messaging, and Task lifecycle across independent agents | Future cross-system Agent Liaison negotiation | Agent Liaison |
| Git | Versioned, reviewable change history | Learning evidence and ADR evolution | Both |

## How to add an entry

Every entry should answer:

1. What interoperability problem does it solve?
2. What assumptions and trust boundaries does it introduce?
3. Where did it appear in a real project?
4. What failure mode made it worth learning?
5. Which official specification or documentation is authoritative?
