# AIRS Concepts

This document summarizes the core AIRS concepts.

## Intent View

An `Intent View` is the central AIRS object. It describes a generated interface in a structured form that can be validated, rendered, adapted, and audited by a runtime.

An `Intent View` is not arbitrary UI code. It is a protocol-level description of task state.

## Task Stage

`stage` describes where the user is in the task lifecycle.

Examples:

- `clarify`
- `searching`
- `selection`
- `comparison`
- `detail`
- `form_filling`
- `confirmation`
- `execution`
- `result`
- `error`

Stages help the runtime decide which actions are safe and which interaction patterns are appropriate.

## Render Component

A render component is a structured unit of interface content.

Examples:

- `summary_card`
- `option_card`
- `detail_panel`
- `form`
- `media`
- `permission_prompt`
- `error_message`

The runtime maps protocol components to platform-specific UI.

## Semantic Action

A semantic action describes what a user action means, not just which button was pressed.

Examples:

- Select an option
- Open details
- Request permission
- Call a tool
- Cancel a task
- Handoff to another surface

Semantic actions make interaction auditable and portable across devices.

## Data Source

Data sources declare provenance. They separate service data, user input, local context, system data, and model-generated content.

This is important because an AIRS view may combine trusted API results with AI-generated summaries.

## Safety Gate

Safety gates define runtime constraints around risk, confirmation, permissions, forbidden automation, and audit tags.

AIRS treats safety as part of the interface protocol.

## AIRS Runtime

The AIRS Runtime validates and renders `Intent View` objects. In this draft, it is positioned as part of an AI-native operating system layer; browser-like containers, application frameworks, and device-specific runtimes may integrate with it as adapters.
