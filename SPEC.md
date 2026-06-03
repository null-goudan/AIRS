# AIRS Specification Draft 0.1

> Status: conceptual draft. This document is not a finalized standard.

## 1. Top-Level Structure

An AIRS `Intent View` is a JSON object with the following minimum shape:

```json
{
  "airs_version": "0.1",
  "view_id": "flight_selection_001",
  "intent": {
    "name": "book_flight",
    "stage": "selection",
    "user_goal": "Find a cheap flight from Dalian to Shanghai tomorrow afternoon."
  },
  "data_sources": [],
  "layout": {},
  "components": [],
  "actions": [],
  "safety": {},
  "state": {}
}
```

Required fields:

- `airs_version`
- `view_id`
- `intent`
- `components`
- `actions`
- `safety`

Recommended fields:

- `data_sources`
- `layout`
- `state`

## 2. Intent

`intent` describes the user goal and the current task stage.

```json
{
  "name": "book_flight",
  "stage": "selection",
  "user_goal": "Find a cheap flight from Dalian to Shanghai tomorrow afternoon."
}
```

Fields:

- `name`: Stable task name.
- `stage`: Current task stage.
- `user_goal`: Natural-language user goal.

## 3. Stage

AIRS 0.1 defines the following initial task stages:

| Stage | Meaning |
| --- | --- |
| `clarify` | The agent needs more user input. |
| `searching` | The agent is searching or waiting for service results. |
| `selection` | The user is choosing from options. |
| `comparison` | The user is comparing multiple options. |
| `detail` | The user is inspecting one item. |
| `form_filling` | The user is entering or correcting structured information. |
| `confirmation` | The user is confirming a meaningful action. |
| `execution` | A requested operation is being executed. |
| `result` | The task result is being shown. |
| `error` | The task needs recovery from a failure. |

## 4. Data Source

`data_sources` declares where displayed data came from.

```json
{
  "id": "flight_service_001",
  "provider": "flight_search_service",
  "type": "api",
  "fetched_at": "2026-06-03T10:30:00+08:00",
  "stale_after_seconds": 300
}
```

Recommended fields:

- `id`: Source identifier referenced by components.
- `provider`: Service, tool, or model that produced the data.
- `type`: Source type, such as `api`, `user_input`, `model_generated`, `local_context`, or `system`.
- `fetched_at`: Timestamp for fetched data.
- `stale_after_seconds`: Optional freshness window.

## 5. Layout

`layout` gives the runtime high-level presentation guidance.

```json
{
  "mode": "adaptive_cards",
  "device_adaptive": true
}
```

The runtime may ignore or transform layout hints when device constraints, accessibility preferences, safety rules, or platform policy require it.

## 6. Component

`components` is an ordered list of renderable protocol-level UI units.

```json
{
  "id": "summary",
  "type": "summary_card",
  "title": "3 suitable flights found",
  "content": "Flights are filtered by afternoon departure and lower price."
}
```

Minimum fields:

- `id`
- `type`

Common component types:

- `summary_card`
- `option_card`
- `detail_panel`
- `form`
- `field`
- `list`
- `media`
- `permission_prompt`
- `error_message`
- `action_bar`

Components may reference available actions by ID.

## 7. Action

`actions` declares semantic operations the user may trigger.

```json
{
  "id": "select_flight_1",
  "label": "Select this flight",
  "type": "semantic_action",
  "next_stage": "confirmation",
  "risk_level": "medium"
}
```

Minimum fields:

- `id`
- `label`
- `type`
- `risk_level`

Action types:

- `semantic_action`
- `navigation`
- `tool_call`
- `permission_request`
- `cancel`
- `handoff`

## 8. Safety

`safety` describes runtime constraints for the view.

```json
{
  "risk_level": "medium",
  "requires_user_confirmation": false,
  "forbidden_auto_actions": ["payment", "final_booking"]
}
```

Risk levels:

- `low`
- `medium`
- `high`
- `critical`

Runtime requirements:

- High-risk or critical actions should require explicit user confirmation.
- Runtime policy may block actions even when the `Intent View` declares them.
- Forbidden automatic actions must not be executed without a separate trusted confirmation path.
- Sensitive actions should produce audit records.

## 9. State

`state` stores task-local state needed to continue the interaction.

```json
{
  "selected": null,
  "expires_at": "2026-06-03T10:35:00+08:00"
}
```

State is not a substitute for durable business records. It should be treated as runtime interaction state.

## 10. Compatibility

AIRS 0.1 is intentionally small. Future versions may add:

- Formal component registries
- Capability negotiation
- Accessibility requirements
- Internationalization fields
- Streaming and partial updates
- Signed service results
- Runtime conformance tests
