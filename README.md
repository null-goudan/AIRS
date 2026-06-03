# AIRS: AI Interface Rendering Specification

**AIRS is a rendering protocol and interaction paradigm for AI-native operating systems.**

AIRS defines how AI agents describe dynamic interfaces through structured `Intent View` objects, so AI-native operating system runtimes can safely render, interact with, and audit AI-generated interfaces.

The goal of AIRS is not to let AI freely generate arbitrary UI code. Instead, AIRS provides a structured protocol between AI agents, service providers, and the operating system runtime, allowing AI-generated interfaces to be constrained, explainable, auditable, and renderable across devices.

> Status: AIRS is an early conceptual draft for discussion. It is not a finalized standard.

[中文说明](README.zh-CN.md)

## Why AIRS?

AI agents are becoming an interaction layer for future devices. They may understand user intent, call services, combine data, and create task-specific interfaces at runtime.

Without a shared interface protocol, this process can become unsafe and inconsistent:

- AI may generate arbitrary UI code that is hard to validate.
- Service data may be mixed with model-generated text without provenance.
- User actions may be ambiguous, unaudited, or executed without clear permission.
- Interfaces may not adapt consistently across phones, tablets, desktop environments, vehicles, wearables, or voice-first devices.

AIRS proposes a structured alternative: AI agents output `Intent View` objects, and AIRS runtimes validate, adapt, render, and execute them under explicit safety rules.

## Core Workflow

```text
User Input
Voice / Image / Text / Video / Context
        |
        v
AI Agent
Intent understanding / task planning / service calling
        |
        v
AI-Native Service
Business data + rendering hints + risk declaration
        |
        v
AIRS Intent View
Intent / Stage / Components / Actions / Safety
        |
        v
AIRS Runtime
Validation / permission control / device adaptation / rendering
        |
        v
User Interaction
Touch / Voice / Gesture / Confirmation
        |
        v
Semantic Action Feedback
```

## Key Concepts

- `Intent View`: A structured description of a generated interface.
- `Task Stage`: The current phase of the user task, such as clarification, selection, confirmation, or result.
- `Render Component`: A protocol-level UI unit such as a summary card, option card, form, media view, or permission prompt.
- `Semantic Action`: A user action with meaning, risk, and next-stage behavior.
- `Data Source`: A declared origin for data shown in the interface.
- `Safety Gate`: Runtime rules for confirmation, permissions, forbidden automation, and auditability.
- `AIRS Runtime`: The system layer that validates and renders `Intent View` objects.

## Repository Structure

```text
.
├── README.md
├── README.zh-CN.md
├── WHITEPAPER.md
├── SPEC.md
├── ROADMAP.md
├── CONTRIBUTING.md
├── LICENSE
├── schema/
│   └── airs.schema.json
├── examples/
├── docs/
└── rfcs/
```

## First Draft Scope

AIRS 0.1 focuses on:

- A minimal `Intent View` structure
- Common task stages
- Core render component types
- Semantic action definitions
- Data provenance
- Safety and permission gates
- Example views for common AI-native tasks

## Examples

See:

- [Flight booking](examples/flight-booking.json)
- [Product search](examples/product-search.json)
- [Video stream](examples/video-stream.json)
- [Permission confirmation](examples/permission-confirmation.json)
- [Error recovery](examples/error-recovery.json)

## Participate

This repository is intended to host an open discussion about AI-generated interfaces and the runtime protocols needed to make them safe, portable, and auditable.

Good starting points:

- What responsibilities should an AI-native operating system runtime own when rendering AIRS views?
- What is the minimal useful `Intent View` structure?
- Which render components should AIRS 0.1 standardize?
- How should risk levels and safety gates be represented?
- Should an AIRS Runtime interpret, compile, or transform `Intent View` objects?

See [CONTRIBUTING.md](CONTRIBUTING.md) for contribution guidelines.

## License

Apache License 2.0. See [LICENSE](LICENSE).
