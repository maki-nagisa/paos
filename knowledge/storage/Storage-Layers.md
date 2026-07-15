# Storage Layers

## Purpose
- Define the fixed storage layers used by PAOS.

## Dependencies
- `knowledge/storage/Knowledge-Storage.md`
- `core/PAOS-Architecture.md`

## Inputs
- PAOS module boundaries
- Artifact authority level
- Artifact time horizon

## Outputs
- Stable layer selection model
- Consistent placement vocabulary

## References
- `knowledge/storage/Storage-Rules.md`
- `knowledge/storage/Storage-Lifecycle.md`

## Layer Model

### `Core Storage`
- stores architecture, ontology, conventions, and manifests
- highest authority and lowest churn
- examples: architecture files, manifest registry, dependency rules

### `State Storage`
- stores current active truth that should be loaded first
- highest recency, not highest historical depth
- examples: current task, current status, current decision index

### `Knowledge Storage`
- stores reusable facts, systems, patterns, solutions, memory, and storage rules
- optimized for stable reuse across tasks
- examples: system maps, memory rules, solution modules, storage contracts

### `Template Storage`
- stores reusable output skeletons and section contracts
- avoids re-inventing stable document shapes
- examples: manifest template, report template, roadmap template

### `Report Storage`
- stores bounded synthesized outputs derived from other layers
- not authoritative over current state when the source layer still exists
- examples: audit reports, state snapshots, analysis outputs

### `Roadmap Storage`
- stores intended structural evolution and pending architecture change
- future-facing rather than current-facing
- examples: initiatives, horizons, module evolution items

### `Archive Storage`
- stores inactive, superseded, or historical material outside default load
- preservation layer, not operating layer
- examples: retired reports, archived roadmap items, superseded knowledge notes

## Layer Selection Rule

Choose the layer by the artifact's authority first, then by time horizon.

Selection order:
1. ask whether the artifact defines rules, state, knowledge, template, report, roadmap, or archive material
2. place it in the smallest matching layer
3. avoid dual-homing the same canonical artifact across multiple layers

## Layer Anti-Patterns

Do not:
- store current state in `archive`
- store durable knowledge only in `reports`
- store canonical rules in `templates`
- store process residue in `knowledge`
- use `state` as a catch-all for everything active in a conversation
