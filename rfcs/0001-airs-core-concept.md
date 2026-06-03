# RFC 0001: AIRS Core Concept

## Status

Draft

## Summary

AIRS proposes a structured protocol for AI-generated interfaces. Instead of allowing an AI agent to output arbitrary frontend code, the agent outputs an `Intent View` object. An AIRS Runtime validates, adapts, renders, and enforces the view.

## Motivation

AI-native systems need a way to turn user intent, service data, and runtime context into safe interactive interfaces.

Free-form UI generation is difficult to constrain. Plain text is not expressive enough for structured tasks. AIRS sits between those extremes.

## Proposal

Define a minimal AIRS 0.1 `Intent View` with:

- Protocol version
- View identifier
- Intent and task stage
- Data sources
- Layout hints
- Components
- Semantic actions
- Safety constraints
- Runtime state

## Non-Goals

AIRS 0.1 does not attempt to:

- Define a full native UI toolkit
- Replace service protocols or function calling
- Specify a complete runtime implementation
- Standardize every possible component
- Declare AIRS as a finished standard

## Open Questions

- Should `stage` live only inside `intent`, or also at the top level?
- Should component types be fixed in the spec or managed through a registry?
- How strict should schema validation be in early drafts?
- How should runtimes expose rejection reasons to agents?
- Should AIRS views be signed by services, agents, or runtimes?

## Compatibility

This RFC assumes AIRS 0.1 is experimental. Compatibility may change as the concept is tested through examples and runtime prototypes.
