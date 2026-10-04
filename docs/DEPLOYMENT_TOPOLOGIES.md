# Deployment topology and migration

## Separate the roles

- **Ingress** makes a service reachable and terminates HTTPS.
- **Gateway** authenticates, routes, and coordinates agent runtime state.
- **Agent** defines instructions, memory, models, workspace, and tools.
- **Session** holds one conversation's short-term state.
- **Node** exposes capabilities from a trusted remote device; it is not another
  gateway.
- **Inference provider** runs the model and may be cloud-hosted or local.

Conflating these roles leads to unnecessary replicas. Moving a reverse tunnel does
not move the gateway; adding a GPU does not improve gateway availability; adding a
device does not necessarily justify another agent.

## Topology selection

| Need | Smallest suitable change |
|---|---|
| Another wearable uses the same assistant and policy | Add client identity and session routing |
| Different memory or tool authority | Add an agent |
| Use a remote computer's browser, screen, or apps | Pair it as a node |
| Keep the system online when a laptop sleeps | Move the active gateway to an always-on host |
| Run a private local model | Add an inference host/provider |
| Hard tenant or administrative isolation | Add a separate gateway/runtime boundary |
| Disaster recovery | Add verified backups and an inactive standby |

## Control-plane reliability before scale

One active gateway is the safest default because it owns channel admission, routing,
session state, and tool dispatch. Before considering active-active replicas, establish:

1. a stable ingress name;
2. service supervision and health checks;
3. idempotent webhook processing;
4. externally durable or replicated state;
5. leader election or a single authoritative ingress target;
6. tested failover and rollback.

Without those controls, two gateways may both process the same event or build
different versions of the same session.

## Health claims need path-specific evidence

A successful provider API probe proves outbound access, not inbound webhook delivery.
After maintenance, verify each boundary independently before declaring the channel
healthy:

1. Check the ingress supervisor and its live process, not just installed configuration.
2. Inspect the live public-to-upstream mapping, including the upstream HTTP/TLS scheme.
3. Request the public health route to test reachability through ingress.
4. Send an unsigned synthetic webhook request and assert the application's documented
   missing-signature rejection. A generic proxy error is not equivalent evidence.
5. Use a fresh authorized event and observe its reply to establish end-to-end delivery.

Report partial evidence explicitly: health-route success and signature rejection do
not prove valid-event processing or reply delivery. Keep request-body inspection off
unless a scoped diagnostic need justifies capturing potentially private messages.

Supervise ingress independently when it must survive gateway maintenance. Test
process recovery separately from reboot persistence, login requirements, and host
sleep behavior; passing one does not establish the others. Repair the failing layer
rather than restarting unrelated services as a diagnostic shortcut.

## Migration is a testable workflow

A portable system needs both declarative and stateful assets:

- Git repositories for public code and documentation;
- versioned configuration with secret references rather than plaintext secrets;
- encrypted backups for credentials, sessions, databases, and private workspaces;
- an inventory of external bindings such as webhook URLs, DNS, OAuth callbacks, and
  paired nodes;
- an end-to-end acceptance test that runs before cutover.

A backup artifact is evidence of copying. A successful restore rehearsal is evidence
of recoverability.

## Primary references

- [OpenClaw Tailscale integration](https://docs.openclaw.ai/gateway/tailscale)
- [OpenClaw remote gateways and nodes](https://docs.openclaw.ai/help/faq/remote-gateways-and-nodes)
- [OpenClaw backup CLI](https://docs.openclaw.ai/cli/backup)
