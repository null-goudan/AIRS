# AIRS Architecture

## Layer Model

```text
User
  |
  v
AI Agent
  |
  v
Services / Tools / Context
  |
  v
AIRS Intent View
  |
  v
AIRS Runtime
  |
  v
Device UI + Semantic Action Feedback
```

## AI Agent

The AI agent understands intent, plans the task, calls services, and constructs an `Intent View`.

The agent does not directly execute arbitrary UI code through AIRS. It proposes a structured interface.

## Services

Services provide business data, tool results, and optional rendering hints. Services should declare data freshness and provenance when possible.

## AIRS Intent View

The `Intent View` is the protocol object passed from the agent layer to the runtime layer.

It includes:

- Intent
- Data sources
- Layout hints
- Components
- Actions
- Safety rules
- State

## AIRS Runtime

The runtime validates and renders the `Intent View`.

Responsibilities:

- Schema validation
- Runtime policy enforcement
- Device adaptation
- Permission handling
- Action dispatch
- Audit logging
- Error handling

## Feedback Loop

When a user interacts with the rendered interface, the runtime sends semantic action feedback back to the agent.

The agent can then update the task, call services, or emit a new `Intent View`.
