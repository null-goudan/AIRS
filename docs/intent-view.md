# Intent View

An `Intent View` is the minimum unit of AIRS rendering.

It represents one task state and the interface needed to let the user inspect, decide, confirm, or recover.

## Required Fields

```json
{
  "airs_version": "0.1",
  "view_id": "example_001",
  "intent": {},
  "components": [],
  "actions": [],
  "safety": {}
}
```

## Recommended Fields

```json
{
  "data_sources": [],
  "layout": {},
  "state": {}
}
```

## Design Principles

- The view should be structured enough to validate.
- The view should be abstract enough to render across devices.
- The view should preserve data provenance.
- The view should declare meaningful user actions.
- The view should expose safety constraints to the runtime.

## Lifecycle

1. Agent emits an `Intent View`.
2. Runtime validates it.
3. Runtime renders it.
4. User triggers a semantic action.
5. Runtime enforces safety gates.
6. Runtime sends semantic action feedback to the agent.
7. Agent emits the next `Intent View`.
