# AIRS Roadmap

## 0.1 Conceptual Draft

Goals:

- Publish the initial repository structure.
- Define the minimal `Intent View` object.
- Publish `schema/airs.schema.json`.
- Provide representative examples.
- Document the runtime and safety model.
- Open discussion through issues and RFCs.

Deliverables:

- `README.md`
- `README.zh-CN.md`
- `WHITEPAPER.md`
- `SPEC.md`
- `schema/airs.schema.json`
- `examples/*.json`
- `docs/*.md`
- `rfcs/0001-airs-core-concept.md`

## 0.2 Protocol Refinement

Possible topics:

- Component registry
- Action lifecycle
- Runtime validation errors
- Partial updates and streaming views
- Accessibility and localization fields
- Trust and provenance model
- Device capability negotiation

## 0.3 Runtime Prototype

Possible deliverables:

- JSON Schema validator
- Example renderer
- Runtime policy examples
- Test fixtures
- Conformance checklist

## Open Questions

- Which responsibilities belong to the AI-native operating system runtime, and which can be delegated to app or service adapters?
- What should be the minimum required fields for an `Intent View`?
- How should services provide rendering hints without taking over interface policy?
- How should AIRS represent high-risk actions such as payment, booking, messaging, or account changes?
- Should AIRS define a fixed component set or a registry mechanism?
