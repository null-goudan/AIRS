# Contributing to AIRS

Thank you for helping shape AIRS. This repository is an early protocol draft, so discussion, critique, examples, and counterexamples are all useful.

## Contribution Types

Useful contributions include:

- Spec feedback
- Schema improvements
- Example `Intent View` objects
- Runtime model proposals
- Safety and permission proposals
- Component model proposals
- Issue discussions
- RFC documents

## Discussion First

For large changes, please open an issue before sending a pull request. A good issue explains:

- What problem you are trying to solve
- Which AIRS concept is affected
- Whether the change affects schema compatibility
- Any examples or alternative designs

## RFCs

Use `rfcs/` for proposals that change protocol direction, semantics, or compatibility.

RFC file names should use this pattern:

```text
0002-short-topic-name.md
```

## Examples

Examples should be valid JSON and should reference `schema/airs.schema.json` when possible.

Each example should make clear:

- The user goal
- The task stage
- The data sources
- The visible components
- The semantic actions
- The safety constraints

## Pull Requests

Before opening a pull request:

- Check that JSON examples parse correctly.
- Keep changes focused on one topic.
- Update `SPEC.md` when schema meaning changes.
- Update examples when field names or semantics change.

## Tone

AIRS is a draft, not a finished standard. Please keep discussions precise, constructive, and open to revision.
