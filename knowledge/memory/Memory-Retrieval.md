# Memory Retrieval

## Purpose
- Define how AI should retrieve memory with low context cost.

## Dependencies
- `knowledge/memory/Knowledge-Memory.md`
- `knowledge/memory/Memory-Taxonomy.md`
- `knowledge/memory/Memory-Rules.md`

## Inputs
- Current task
- Active project scope
- Required decision context

## Outputs
- Minimal relevant memory load
- Predictable retrieval order

## References
- `core/manifest/manifest.root.json`
- `state/state.index.md`

## Retrieval Order

Default retrieval order:
1. `core`
2. `state`
3. `knowledge/memory` only for task-relevant classes
4. other `knowledge` modules only when memory is insufficient
5. `reports` only when a bounded synthesized answer is needed
6. `archive` only by explicit need

## Retrieval Rules

- retrieve by task need, not by folder breadth
- prefer class-level targeting before reading multiple files
- load the smallest canonical memory unit that can answer the question
- stop retrieval once the decision or implementation path is sufficiently grounded

## Retrieval Heuristics

Use `Preference Memory` when output style, risk tolerance, or workflow defaults matter.

Use `Decision Memory` when architecture or structural constraints matter.

Use `Solution Memory` when a known issue, repair path, or workaround likely repeats.

Use `Project Memory` when continuing prior work in the same project.

Use `Reference Memory` when the task needs a source-of-truth pointer rather than full detail.

## Anti-Patterns

Do not:
- preload all memory files by default
- read archive before memory
- use memory as a substitute for current `state`
- treat reports as canonical memory when a memory module already exists
