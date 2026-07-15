# Automation Lifecycle

## Purpose
- Define the canonical lifecycle for automation units in `PAOS`.
- Prevent automation knowledge from drifting between draft, active, and retired states without explicit control.

## Dependencies
- `knowledge/workflows/Workflow-Automation.md`
- `knowledge/storage/Storage-Lifecycle.md`
- `state/State-Module.md`

## Lifecycle States

Automation units use the following lifecycle states:

| State | Meaning |
| --- | --- |
| `draft` | concept exists but contract is not yet stable |
| `candidate` | contract is defined and ready for bounded validation |
| `stable` | contract is approved and may be reused by later modules |
| `superseded` | replaced by a newer canonical automation contract |
| `archived` | removed from active surface and retained only for historical reference |

## Transition Rule

Allowed transitions:

```text
draft -> candidate -> stable -> superseded -> archived
stable -> archived
candidate -> archived
```

Transition rules:
- `draft` becomes `candidate` only after fields, boundaries, and owning file are explicit
- `candidate` becomes `stable` only after acceptance checks pass and no boundary conflict remains
- `stable` may become `superseded` only when a replacement canonical file is named
- `superseded` may move to `archived` only after references are redirected to the replacement
- do not skip directly from `draft` to `stable`

## State Handling Rule

Lifecycle state must be visible in the canonical automation file and, where applicable, in the relevant manifest metadata.

Operational rule:
- current runtime enablement is tracked in `state`
- lifecycle maturity is tracked in the canonical automation knowledge file
- point-in-time validation evidence belongs in `reports`

## Stable Sections

The following sections are now treated as `Stable` for the current architecture phase:
- `Lifecycle States`
- `Transition Rule`
- `State Handling Rule`

Current status for this file: `Stable`
