# Knowledge Workflows

## Purpose
- Organize reusable workflow knowledge without preserving workflow residue.
- Define workflow-level execution contracts, including automation, as reusable knowledge rather than task transcripts.

## Dependencies
- `knowledge/Knowledge-Module.md`
- `state/current/Current-Task.md`

## Inputs
- Validated workflow patterns
- Repeatable operating flows

## Outputs
- Workflow knowledge registry
- Reusable execution references
- Stable automation contracts with explicit triggers, state boundaries, and acceptance rules

## References
- `knowledge/Knowledge-Module.md`
- `knowledge/workflows/Workflow-Automation.md`
- `knowledge/patterns/Knowledge-Patterns.md`
- `knowledge/solutions/Knowledge-Solutions.md`

## Workflow Role

`workflows` owns repeatable operating flows that coordinate state, knowledge, tools, and acceptance checks.
It does not own raw execution traces, local script inventories, or temporary run notes.

Workflow knowledge should answer:
- what repeatable flow exists
- what it reads
- what it writes
- when it is allowed to run
- how correctness is checked

## Workflow Submodules

The first stable workflow submodule is:

| Submodule | Role | Canonical Entry |
| --- | --- | --- |
| `automation` | reusable automation contract | `knowledge/workflows/Workflow-Automation.md` |

Submodule rule:
- additional workflow submodules require explicit architecture approval before becoming canonical

## Workflow Boundary Rule

`workflows` owns reusable operating flows, not execution residue.

Boundary rules:
- if the content describes a durable execution contract, place it in `workflows`
- if the content describes tool or environment structure, place it in `systems`
- if the content describes a reusable abstract strategy independent of one flow, place it in `patterns`
- if the content describes a validated answer to a concrete repeated problem, place it in `solutions`
- if the content records current progress or current blockers, place it in `state`
- if the content is a point-in-time run result, place it in `reports`

## Workflow Unit Rule

Every canonical workflow description should be expressible as a compact workflow unit.

Recommended fields:
- `workflowId`
- `title`
- `objective`
- `trigger`
- `inputs`
- `outputs`
- `dependencies`
- `stateReads`
- `stateWrites`
- `acceptanceRule`
- `ownerFile`
- `status`

Unit rules:
- each workflow should capture one repeatable flow with one bounded objective
- workflows should describe reusable logic, not run-by-run notes
- child files may specialize the unit contract, but must not weaken trigger or acceptance requirements

## Workflow Assembly Rule

When a task needs workflow knowledge, load it in this order:

1. `knowledge/workflows/Knowledge-Workflows.md`
2. the smallest relevant workflow entry file
3. only the supporting child files required by that workflow
4. `state` for current execution context
5. `reports` only if proof of a prior run is explicitly needed

This keeps workflow retrieval small and preserves the `knowledge > history` rule.

## Completion Standard

The `workflows` submodule is complete for this phase only when all of the following are true:
- workflow ownership is distinct from adjacent submodules
- at least one canonical workflow submodule is defined
- workflow unit fields are explicit
- load order for workflow knowledge is defined
- later workflow files can extend the module without redefining the base contract

## Stable Sections

The following sections are now treated as `Stable` for the current architecture phase:
- `Workflow Role`
- `Workflow Submodules`
- `Workflow Boundary Rule`
- `Workflow Unit Rule`
- `Workflow Assembly Rule`

Stable rule:
- later workflow documents must reference these sections instead of redefining them
- any change requires an explicit update here first

Current status for this file: `Stable`
