# Context Assembly

## Purpose
- Define how PAOS assembles minimum sufficient context for AI execution.

## Dependencies
- `knowledge/context/Knowledge-Context.md`
- `knowledge/context/Context-Layers.md`
- `core/manifest/manifest.root.json`
- `state/state.index.md`

## Inputs
- Task objective
- Current state
- Relevant knowledge modules

## Outputs
- Stable context assembly order
- Reusable context loading procedure

## References
- `knowledge/context/Context-Rules.md`
- `core/conventions/references.md`
- `knowledge/memory/Memory-Retrieval.md`

## Assembly Order

Default context assembly order:

1. read `core/manifest/manifest.root.json`
2. read `core/PAOS-Architecture.md`
3. read `core/PAOS-Directory.md`
4. read `state/state.index.md`
5. read only current-state files directly referenced by the active task
6. load only the minimum relevant `knowledge` modules
7. load `templates` only if the task requires structured output generation
8. load `reports` only if they reduce re-analysis cost for the current bounded question
9. load `archive` only by explicit need

## Assembly Principle

Context assembly should optimize for minimum sufficient truth.

This means:
- start from authority, not convenience
- load indexes before details
- prefer module entry files before deep leaf files
- stop loading once the task can be executed safely

## Context Packet Rule

Every reusable context bundle should be representable as a small packet with:
- `objective`
- `currentState`
- `constraints`
- `requiredModules`
- `optionalModules`
- `excludedHistory`

The packet is conceptual first.
It may later be represented through manifests, state files, or automation helpers, but the architecture stays the same.

## Escalation Rule

If required truth is still missing after the minimum packet is loaded:
- load the next smallest canonical file
- do not jump directly to large folders, raw logs, or full-history review
- record the new dependency only if it recurs and deserves promotion into stable context knowledge
