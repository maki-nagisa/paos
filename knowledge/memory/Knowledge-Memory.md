# Knowledge Memory Module

## Purpose
- Define how PAOS stores memory as durable knowledge instead of conversation residue.
- Keep memory loadable in small modules with clear authority and freshness.

## Scope
- Personal long-term memory rules for `ChatGPT`, `Codex`, local workspace, and AI agents.
- Covers memory classes, storage rules, update rules, and retrieval boundaries.
- Does not store raw chat history, full execution traces, or temporary debugging residue.

## Inputs
- Stable user preferences validated across sessions.
- Durable architecture decisions.
- Reusable problem-solution knowledge.
- Active project facts that remain true beyond one session.

## Outputs
- Canonical memory taxonomy for PAOS.
- Memory storage rules for future modules and tools.
- Retrieval guidance that minimizes default context cost.

## Dependencies
- `core/PAOS-Architecture.md`
- `core/ontology/terms.md`
- `core/conventions/references.md`
- `knowledge/Knowledge-Module.md`
- `state/state.index.md`

## Canonical Files
- `knowledge/memory/Knowledge-Memory.md`
- `knowledge/memory/Memory-Taxonomy.md`
- `knowledge/memory/Memory-Rules.md`
- `knowledge/memory/Memory-Retrieval.md`

## Update Rule
- Update only when memory architecture, classification, or retrieval contracts change.
- Project-specific instances should be stored in `state` or `reports` first, then promoted only after validation.

## Memory Role

Memory in PAOS is not a replay system.
Memory is the compressed layer that preserves what future work should still know without re-reading old sessions.

Memory must satisfy all of the following:
- durable enough to survive multiple sessions
- compressible into small referenceable units
- useful for future execution or decision quality
- cheaper to load than reconstructing the same fact from history

Memory must not become a second archive.

## Memory Boundaries

PAOS distinguishes four adjacent concepts:

| Concept | Purpose | Default Load | Time Horizon |
| --- | --- | --- | --- |
| `state` | current truth | yes | now |
| `memory` | durable reusable truth | selective | long-lived |
| `reports` | bounded synthesized outputs | selective | point-in-time |
| `archive` | inactive historical material | no | historical |

Boundary rules:
- if a fact is only true now, it belongs in `state`
- if a fact will likely remain useful later, it may become `memory`
- if a document answers one bounded question, it belongs in `reports`
- if a document exists mainly for audit or retrospective traceability, it belongs in `archive`

## Memory Promotion Rule

Information should enter memory only after passing a promotion gate:

1. the fact or rule appears more than once or has clear future reuse
2. the content can be stated as current knowledge, not session narration
3. the content has a stable owner or canonical location
4. storing it reduces future context cost
5. the memory does not duplicate an existing canonical module

If any condition fails, keep the content out of memory.
