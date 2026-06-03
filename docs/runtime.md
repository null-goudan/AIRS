# AIRS Runtime

The AIRS Runtime is the system layer that validates, adapts, renders, and enforces `Intent View` objects.

## Responsibilities

An AIRS Runtime should:

- Parse and validate `Intent View` objects.
- Apply platform policy.
- Adapt components to device capabilities.
- Enforce safety gates.
- Request user confirmation when needed.
- Dispatch approved semantic actions.
- Return semantic action feedback to the agent.
- Preserve audit records for sensitive actions.

## Validation

The runtime should validate:

- Required fields
- Known protocol version
- Component structure
- Action structure
- Risk and safety declarations
- Data source references, when possible

## Device Adaptation

The same AIRS view may be rendered differently on different devices.

Examples:

- Desktop: multi-column cards and detail panels
- Phone: stacked cards and sheets
- Voice: spoken options and confirmations
- TV: focusable panels and remote-friendly actions
- Wearable: condensed summaries and high-confidence actions only

## Policy

Runtime policy may depend on:

- Device type
- User permissions
- Organization policy
- Data sensitivity
- Network state
- Trust level of data sources
- Risk level of actions

## Action Dispatch

The runtime should dispatch semantic actions only after policy checks pass.

For high-risk actions, the runtime should use a trusted confirmation UI rather than relying only on agent-generated text.
