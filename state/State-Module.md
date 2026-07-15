# State Module

## Purpose
- Hold the current active truth that `PAOS` should load before broader knowledge.
- Define the canonical current-state control surface so `PAOS` can read present truth without replaying process history.

## Dependencies
- `core/manifest/manifest.root.json`
- `core/PAOS-Architecture.md`

## Inputs
- Current operating state
- Current effective decisions
- Current active tasks

## Outputs
- Default-load state surface
- Current execution context
- Compact current-truth contracts for status, task focus, decisions, and active projects

## References
- `state/state.index.md`
- `state/current/Status.md`
- `state/current/Current-Task.md`
- `state/decisions/Decision-Index.md`
- `state/active-projects/Active-Projects.md`

## Scope

`state` owns current, decision-grade truth.
It stores what is true now, what is currently active, and what effective decisions future work should load first.

It does not store full execution logs, long-lived reusable knowledge, one-off report packs, or historical discussion residue.

## State Role

`state` is the default control surface for `PAOS`.
It exists so future sessions can recover the present operating condition directly instead of replaying prior processes.

State should answer:
- what is true now
- what task or initiative is active now
- what decisions currently govern behavior
- what project surfaces remain active now
- what next step is currently allowed

## State Boundary Rule

Place content in `state` only if it expresses active truth with current authority.

Boundary rules:
- if the content is reusable beyond the current operating window, place it in `knowledge`
- if the content is a bounded analysis, audit, or evidence bundle, place it in `reports`
- if the content is intended future change, place it in `roadmap`
- if the content is superseded but still worth retaining, place it in `archive`
- if the content is only process narration without current authority, do not keep it in `state`

## State Surfaces

The first-wave `state` surfaces for `PAOS` are fixed to the following groups:

| State Surface | Role | Canonical Entry |
| --- | --- | --- |
| `current-status` | current module and architecture condition | `state/current/Status.md` |
| `current-task` | current execution focus and immediate next step | `state/current/Current-Task.md` |
| `decisions` | effective current decisions | `state/decisions/Decision-Index.md` |
| `active-projects` | currently active scoped efforts | `state/active-projects/Active-Projects.md` |

Surface rules:
- each active fact should have one primary owning state surface
- state surfaces may reference `knowledge` and `roadmap`, but should not duplicate them
- future state files may extend these surfaces without changing the fixed first-wave map

## State Unit Rule

Every canonical state surface should be expressible as a compact state unit.

Recommended fields:
- `stateId`
- `title`
- `currentTruth`
- `scope`
- `effectiveFrom`
- `dependencies`
- `relatedDecisions`
- `nextAction`
- `ownerFile`
- `status`

Unit rules:
- one unit should capture one active truth surface
- state text should prefer current conclusions over process chronology
- when truth changes, replace prior current truth rather than accumulating narration

## State Refresh Rule

`state` should be refreshed whenever the current authoritative truth changes.

Refresh rules:
- prefer replacement of stale state over append-only accumulation
- record only the minimum current truth needed for future recovery
- promote durable reusable facts into `knowledge` instead of bloating `state`
- move superseded or audit-only material into `reports` or `archive`

## Completion Standard

The `state` module is complete for this phase only when all of the following are true:
- its role is distinct from `knowledge`, `reports`, `roadmap`, and `archive`
- the first-wave state surfaces are fixed
- state units have a standard field contract
- refresh behavior prefers current truth over process accumulation
- future state files can extend the module without redefining the base contract

## Stable Sections

The following sections are now treated as `Stable` for the current architecture phase:
- `State Role`
- `State Boundary Rule`
- `State Surfaces`
- `State Unit Rule`
- `State Refresh Rule`

Stable rule:
- later state documents must reference these sections instead of redefining them
- any change requires an explicit update here first

Current status for this file: `Stable`
