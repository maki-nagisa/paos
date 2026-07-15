# Knowledge Storage Module

## Purpose
- Define how PAOS stores durable knowledge artifacts across active and inactive layers.
- Keep storage architecture modular, low-context, and stable across long-term personal use.

## Scope
- Personal storage design for `ChatGPT`, `Codex`, local workspace, and AI-agent-assisted development.
- Covers storage layers, storage units, placement rules, and lifecycle boundaries.
- Does not define vendor-specific databases, cloud accounts, or infrastructure deployment details.

## Inputs
- Canonical modules
- Current state artifacts
- Durable knowledge units
- Bounded reports and archived records

## Outputs
- Canonical storage model for PAOS
- Stable placement rules for future modules and files
- Lifecycle guidance for promoting, retaining, and retiring knowledge artifacts

## Dependencies
- `core/PAOS-Architecture.md`
- `core/PAOS-Directory.md`
- `core/ontology/terms.md`
- `knowledge/Knowledge-Module.md`
- `knowledge/memory/Knowledge-Memory.md`
- `state/state.index.md`

## Canonical Files
- `knowledge/storage/Knowledge-Storage.md`
- `knowledge/storage/Storage-Layers.md`
- `knowledge/storage/Storage-Rules.md`
- `knowledge/storage/Storage-Lifecycle.md`

## Update Rule
- Update only when storage boundaries, placement contracts, or lifecycle rules change.
- Project-specific file locations should stay in `state` or project knowledge until they become reusable storage knowledge.

## Storage Role

Storage in PAOS is not a dump area.
Storage is the placement system that keeps durable knowledge discoverable without turning the workspace into history sludge.

Storage must satisfy all of the following:
- place each artifact in the smallest correct authority layer
- reduce future retrieval cost
- preserve current truth without mixing it with obsolete residue
- support long-term maintenance without requiring full-history reload

Storage must not become a second archive, a second memory system, or a generic file bucket.

## Storage Boundaries

PAOS separates storage by authority and time horizon:

| Layer | Purpose | Default Load | Time Horizon |
| --- | --- | --- | --- |
| `core` | global rules and contracts | yes | long-lived |
| `state` | current active truth | yes | now |
| `knowledge` | durable reusable truth | selective | long-lived |
| `templates` | reusable output contracts | selective | long-lived |
| `reports` | bounded synthesized artifacts | selective | point-in-time |
| `roadmap` | intended future structure | selective | forward-looking |
| `archive` | inactive historical material | no | historical |

Boundary rules:
- if an artifact defines system rules, store it in `core`
- if an artifact expresses current active truth, store it in `state`
- if an artifact carries durable reusable knowledge, store it in `knowledge`
- if an artifact defines how outputs should be generated, store it in `templates`
- if an artifact answers one bounded question, store it in `reports`
- if an artifact describes intended future change, store it in `roadmap`
- if an artifact is no longer active but still worth retaining, store it in `archive`

## Storage Objective

The storage objective is simple:
- one durable fact should have one canonical home
- one active question should require minimum file loading
- one obsolete artifact should move out of the default path

When storage is correct, PAOS reads less, not more.
