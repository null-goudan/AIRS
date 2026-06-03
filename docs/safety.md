# Safety

AIRS treats safety as a first-class part of generated interfaces.

## View-Level Safety

Each `Intent View` includes a `safety` object.

```json
{
  "risk_level": "medium",
  "requires_user_confirmation": false,
  "forbidden_auto_actions": ["payment", "final_booking"]
}
```

## Action-Level Safety

Each action should also declare its own risk level and confirmation requirement.

```json
{
  "id": "confirm_send_invite",
  "label": "Confirm and send",
  "type": "tool_call",
  "risk_level": "high",
  "requires_confirmation": true
}
```

## Risk Levels

| Level | Meaning |
| --- | --- |
| `low` | Reversible or informational action. |
| `medium` | Meaningful preference, selection, or device action. |
| `high` | External side effect, private data access, payment setup, booking, or message sending. |
| `critical` | Irreversible, high-value, regulated, or security-sensitive action. |

## Runtime Enforcement

The runtime should be allowed to block or downgrade any action, regardless of what the agent declares.

Examples:

- Require confirmation for `high` actions.
- Block automatic payment.
- Hide unsafe actions on shared devices.
- Ask for device permission before casting media.
- Create audit logs for sensitive operations.

## Provenance

Components should reference data sources when possible. The runtime can use provenance to label uncertain data, stale data, or model-generated summaries.
