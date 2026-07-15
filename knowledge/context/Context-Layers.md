# Context Layers

## Purpose
- Define the authority layers that compose PAOS context.

## Dependencies
- `knowledge/context/Knowledge-Context.md`
- `core/PAOS-Architecture.md`
- `state/state.index.md`

## Inputs
- Module boundaries
- Canonical authority rules

## Outputs
- Stable context-layer model
- Clear load priority by authority and time horizon

## References
- `knowledge/context/Context-Assembly.md`
- `knowledge/context/Context-Rules.md`
- `knowledge/memory/Memory-Retrieval.md`

## Layer Model

PAOS context is assembled from authority layers, not from chronological logs.

| Layer | Source | Role | Default Load |
| --- | --- | --- | --- |
| `L0` | `core` | architecture, ontology, naming, dependency rules | yes |
| `L1` | `state` | current active truth and current objective | yes |
| `L2` | `knowledge` | durable reusable knowledge relevant to the task | selective |
| `L3` | `templates` | output contracts and document skeletons | selective |
| `L4` | `reports` | bounded synthesized outputs for a specific question | selective |
| `L5` | `archive` | inactive history for explicit lookup only | no |

## Layer Rules

- higher-authority layers must load before lower-authority layers
- lower layers may refine, but must not override, higher-layer contracts
- `archive` is never part of baseline context
- `reports` enter context only when they answer the current bounded question more cheaply than re-derivation
- `templates` enter context only when the task requires generation against a stable output contract

## Layer Boundary Tests

Use these tests before adding a file to live context:
- does it define a rule? load from `core`
- does it express current truth? load from `state`
- does it provide durable reusable knowledge? load from `knowledge`
- does it define an output shape? load from `templates`
- does it answer a bounded question? load from `reports`
- is it mainly retained for history? keep it in `archive`
