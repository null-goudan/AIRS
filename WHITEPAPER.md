# AIRS Whitepaper

## 1. Background

Human-computer interaction is moving from application-centric workflows toward intent-centric workflows. Instead of opening a fixed application and navigating pre-built screens, users increasingly ask an AI system to understand a goal, gather data, call services, and guide them through completion.

In that model, the interface may not be fully designed ahead of time by an application developer. It may be assembled dynamically from user intent, service results, device context, and runtime safety policies.

AIRS, the AI Interface Rendering Specification, is a proposal for describing those generated interfaces in a structured and auditable way.

## 2. Problem

AI-generated interfaces raise a basic systems problem: what exactly should an AI agent output when it needs to show an interface?

Free-form HTML, JavaScript, or native UI code is powerful, but it is also difficult to validate, constrain, render consistently, and audit. Pure natural language is safe and flexible, but it cannot express structured UI, semantic actions, permissions, layout hints, data provenance, and runtime state in a reliable form.

A protocol layer is needed between AI agents and AI-native runtimes.

## 3. Definition

AIRS defines a structured object called an `Intent View`.

An `Intent View` describes:

- The user intent and task stage
- The data sources used by the view
- The render components to present
- The semantic actions available to the user
- The safety rules and permission constraints
- The state needed to continue the task

The AIRS Runtime is responsible for validating the object, adapting it to the device, rendering the interface, collecting user interaction, enforcing safety gates, and sending semantic action feedback to the agent.

## 4. Core Workflow

```text
User Input -> AI Agent -> Service Calls -> AIRS Intent View -> AIRS Runtime -> User Interaction -> Semantic Action Feedback
```

The key design choice is that AI does not directly execute arbitrary UI code. Instead, it proposes a structured view. The runtime decides whether and how that view can be rendered and which actions can be executed.

## 5. Key Abstractions

### Intent

The high-level user goal and task name, such as `book_flight`, `compare_products`, or `confirm_payment`.

### Stage

The current phase of the task. AIRS 0.1 proposes stages such as `clarify`, `searching`, `selection`, `comparison`, `detail`, `form_filling`, `confirmation`, `execution`, `result`, and `error`.

### Component

A renderable UI unit. Components are protocol-level declarations, not arbitrary frontend code. Examples include `summary_card`, `option_card`, `form`, `media`, `permission_prompt`, and `error_message`.

### Action

A semantic operation the user can choose. Actions include navigation, selection, tool calls, permission requests, cancellation, and handoff.

### Safety

The safety policy attached to a view or action. It can declare risk level, confirmation requirements, permission scopes, forbidden automatic actions, audit tags, and data sensitivity.

## 6. Relationship With Service Protocols and Function Calling

Service-connection protocols and function calling help an agent reach tools, APIs, files, and business systems. AIRS addresses a different layer: how the result of that reasoning and service access becomes a structured interface.

In simple terms:

- Service protocols connect the agent to capabilities and data.
- AIRS describes the interface that should be rendered from the task state.
- The AIRS Runtime validates and renders that interface safely.

These layers are complementary.

## 7. Runtime Model

An AIRS Runtime should be able to:

- Validate `Intent View` objects against a schema
- Reject unknown or unsafe structures according to runtime policy
- Adapt layout and components to device capability
- Preserve data source provenance
- Enforce confirmation and permission rules
- Convert user interaction into semantic action feedback
- Produce audit logs for sensitive actions

The runtime may be implemented inside an operating system, AI shell, browser-like container, application framework, or device-specific interaction layer.

## 8. Safety and Trust

AIRS treats safety as part of the protocol rather than an afterthought.

Risk should be declared at both the view level and action level. High-risk operations, such as payment, final booking, account changes, external messages, and irreversible changes, should require explicit user confirmation and runtime enforcement.

AIRS should also distinguish:

- Data from trusted services
- Data inferred or summarized by a model
- Data entered by the user
- Data that is stale, sensitive, or permission-scoped

## 9. Software Engineering Paradigm

AIRS suggests new engineering roles and boundaries:

- AI service providers expose business data and rendering hints.
- AI agents plan tasks and construct `Intent View` objects.
- Protocol designers define reusable components, stages, actions, and safety rules.
- Runtime implementers render and enforce AIRS across devices.

The interface becomes less like a fixed page and more like a structured, validated task state.

## 10. Roadmap

AIRS 0.1 should stay small enough to invite discussion:

- Define the minimal `Intent View` shape
- Publish JSON Schema
- Provide representative examples
- Document the runtime model and safety model
- Collect discussion through issues and RFCs
- Build a validator and prototype renderer later

The purpose of this repository is to make the idea concrete enough that others can critique it, test it, and improve it.
