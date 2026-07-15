# Knowledge Patterns

## Purpose
- Store reusable structural or operational patterns that reduce repeated reasoning cost.
- Define the canonical abstraction layer for repeatable designs that should outlive any single workflow or solution.

## Dependencies
- `knowledge/Knowledge-Module.md`
- `core/PAOS-Architecture.md`

## Inputs
- Reusable patterns
- Stable abstractions
- Repeated design structures observed across systems, workflows, or solutions

## Outputs
- Pattern registry
- Pattern lookup anchors
- Canonical pattern contracts with reusable names and boundaries

## References
- `knowledge/Knowledge-Module.md`
- `knowledge/workflows/Knowledge-Workflows.md`
- `knowledge/solutions/Knowledge-Solutions.md`

## Scope

`patterns` owns reusable structural and operational abstractions.
It captures designs that are more general than one concrete workflow and more reusable than one specific fix.

It does not store current status, one-off execution flows, or issue-specific repair notes.

## Pattern Role

`patterns` is the abstraction layer that compresses repeated reasoning into named reusable forms.
It exists so future work can reuse a stable pattern directly instead of rediscovering the same structure from multiple examples.

Pattern knowledge should answer:
- what reusable pattern exists
- what problem shape it fits
- what constraints define it
- what modules commonly use it
- what boundary separates it from neighboring patterns

## Pattern Boundary Rule

Place content in `patterns` only if it is reusable across more than one concrete workflow, system, or solution unit.

Boundary rules:
- if the content describes one concrete operating flow, place it in `workflows`
- if the content describes one concrete environment or interface surface, place it in `systems`
- if the content describes one validated answer to a repeated issue, place it in `solutions`
- if the content describes current truth for one project or one run, keep it in `state` or `reports`

## Pattern Classes

The first-wave pattern classes for `PAOS` are fixed to the following groups:

| Pattern Class | Role |
| --- | --- |
| `context-patterns` | low-context loading and compression structures |
| `state-patterns` | state-first coordination and update patterns |
| `workflow-patterns` | repeatable execution-shape patterns |
| `knowledge-patterns` | modularization, promotion, and reference patterns |
| `integration-patterns` | connector and boundary management patterns |

Class rules:
- each canonical pattern should belong to one primary class
- child pattern files may be added later without changing this class map
- later modules should reference a pattern class before inventing a new parallel vocabulary

## Pattern Unit Rule

Every canonical pattern description should be expressible as a compact pattern unit.

Recommended fields:
- `patternId`
- `title`
- `patternClass`
- `problemShape`
- `structure`
- `constraints`
- `whenToUse`
- `whenNotToUse`
- `relatedModules`
- `ownerFile`
- `status`

Unit rules:
- one unit should capture one reusable abstraction
- pattern text should stay abstract enough to reuse, but concrete enough to guide implementation
- patterns should link to examples in other modules rather than absorb those examples fully

## Completion Standard

The `patterns` submodule is complete for this phase only when all of the following are true:
- its role is distinct from `systems`, `workflows`, and `solutions`
- the first-wave pattern classes are fixed
- pattern units have a standard field contract
- later pattern files can extend the module without redefining the base rules here

## Stable Sections

The following sections are now treated as `Stable` for the current architecture phase:
- `Pattern Role`
- `Pattern Boundary Rule`
- `Pattern Classes`
- `Pattern Unit Rule`

Stable rule:
- later pattern documents must reference these sections instead of redefining them
- any change requires an explicit update here first

Current status for this file: `Stable`
