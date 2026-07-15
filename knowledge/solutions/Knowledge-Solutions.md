# Knowledge Solutions

## Purpose
- Store validated solution modules that should outlive the original debugging process.
- Define the canonical layer for reusable answers to recurring problems in `PAOS`.

## Dependencies
- `knowledge/Knowledge-Module.md`
- `knowledge/patterns/Knowledge-Patterns.md`

## Inputs
- Validated solutions
- Stable fixes and operating answers

## Outputs
- Solution registry
- Reusable solution references
- Canonical solution contracts with explicit ownership, applicability, and acceptance boundaries

## References
- `knowledge/Knowledge-Module.md`
- `knowledge/systems/Knowledge-Systems.md`
- `knowledge/workflows/Knowledge-Workflows.md`
- `reports/Reports-Module.md`

## Scope

`solutions` owns validated answers to recurring or decision-grade problems.
It captures the stable resolution that should be reused later without replaying the original debugging history.

It does not store raw troubleshooting logs, temporary experiments, current blockers, or generic abstractions that belong in `patterns`.

## Solution Role

`solutions` is the answer layer of `PAOS` knowledge.
It exists so future work can load a stable operating answer directly instead of re-reading the incident trail that produced it.

Solution knowledge should answer:
- what problem has been solved
- what resolution is now considered canonical
- what boundary or precondition applies
- what systems or workflows the solution depends on
- what evidence standard makes the solution reusable

## Solution Boundary Rule

Place content in `solutions` only if it captures a validated answer that is expected to be reused.

Boundary rules:
- if the content describes a reusable abstract design, place it in `patterns`
- if the content describes a durable operating surface, place it in `systems`
- if the content describes a reusable execution flow, place it in `workflows`
- if the content describes current status, current blockers, or current ownership, place it in `state`
- if the content is a point-in-time audit, experiment result, or evidence packet, place it in `reports`
- if the content is superseded history, place it in `archive`

## Solution Classes

The first-wave solution classes for `PAOS` are fixed to the following groups:

| Solution Class | Role |
| --- | --- |
| `architecture-solutions` | validated answers for structural or module-boundary problems |
| `workflow-solutions` | validated answers for recurring execution or coordination problems |
| `integration-solutions` | validated answers for connector, tool, or interface issues |
| `state-solutions` | validated answers for current-state governance and handoff problems |
| `knowledge-solutions` | validated answers for storage, retrieval, promotion, or compression problems |

Class rules:
- each canonical solution should belong to one primary solution class
- child solution files may be added later without changing this class map
- later documents should reuse these class names before introducing parallel vocabulary

## Solution Unit Rule

Every canonical solution description should be expressible as a compact solution unit.

Recommended fields:
- `solutionId`
- `title`
- `solutionClass`
- `problem`
- `resolution`
- `applicability`
- `preconditions`
- `constraints`
- `dependencies`
- `acceptanceRule`
- `ownerFile`
- `status`

Unit rules:
- one unit should capture one reusable answer
- the solution should preserve the answer, not the full debugging chronology
- evidence may be referenced from `reports`, but the canonical answer must remain understandable without replaying the full report set

## Reference Rule

Other modules should reference `solutions` when they need a validated answer rather than a fresh exploration.

Reference rules:
- `state` may point to a solution when current work should reuse an established answer
- `workflows` may reference solutions when a flow depends on a known resolution
- `reports` may summarize evidence for a solution, but should point back to the canonical solution file
- `systems` and `patterns` may be cited by a solution as dependencies, but the solution must not duplicate their base contracts

## Completion Standard

The `solutions` submodule is complete for this phase only when all of the following are true:
- its role is distinct from `patterns`, `systems`, `workflows`, `state`, and `reports`
- the first-wave solution classes are fixed
- solution units have a standard field contract
- cross-module reference behavior is explicit
- later solution files can extend the module without redefining the base rules here

## Stable Sections

The following sections are now treated as `Stable` for the current architecture phase:
- `Solution Role`
- `Solution Boundary Rule`
- `Solution Classes`
- `Solution Unit Rule`
- `Reference Rule`

Stable rule:
- later solution documents must reference these sections instead of redefining them
- any change requires an explicit update here first

Current status for this file: `Stable`
