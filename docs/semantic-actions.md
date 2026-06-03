# Semantic Actions

Semantic actions define what the user can do from an AIRS `Intent View`.

They are more meaningful than UI events. A click, voice command, keyboard action, or gesture can all map to the same semantic action.

## Action Shape

```json
{
  "id": "select_flight_1",
  "label": "Select this flight",
  "type": "semantic_action",
  "next_stage": "confirmation",
  "risk_level": "medium"
}
```

## Initial Action Types

| Type | Meaning |
| --- | --- |
| `semantic_action` | Task-level action such as selecting an option. |
| `navigation` | Move to another view or detail state. |
| `tool_call` | Execute a tool or service action. |
| `permission_request` | Ask the runtime or user for permission. |
| `cancel` | Stop or cancel the current task. |
| `handoff` | Move the task to another surface, app, or human channel. |

## Risk Levels

Every action should declare a risk level:

- `low`
- `medium`
- `high`
- `critical`

High and critical actions should require runtime confirmation.

## Feedback

When the user triggers an action, the runtime should send feedback to the agent with:

- Action ID
- View ID
- Runtime decision
- User confirmation result, if any
- Relevant state payload

This lets the agent continue the task without relying on raw UI events.
