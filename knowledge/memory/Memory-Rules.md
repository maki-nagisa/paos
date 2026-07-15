# Memory Rules

## Purpose
- Define the operating rules that keep PAOS memory small, current, and maintainable.

## Dependencies
- `knowledge/memory/Knowledge-Memory.md`
- `knowledge/memory/Memory-Taxonomy.md`

## Inputs
- Candidate memories
- Architecture changes
- Repeated reusable findings

## Outputs
- Consistent memory quality
- Reduced duplication and drift

## References
- `knowledge/memory/Memory-Retrieval.md`
- `state/state.index.md`

## Storage Rules

- store knowledge, not work residue
- store current truth, not how the truth was discovered
- keep one canonical entry per durable fact or rule
- prefer compact statements over long explanation
- replace or retire stale memory instead of layering conflicting versions

## Freshness Rules

- memory should represent the latest validated durable truth
- when a newer decision supersedes an older one, update the canonical memory and move historical rationale to `reports` or `archive` if still needed
- memory entries without durable reuse should be demoted out of memory

## Compression Rules

- each memory file should answer one stable question
- avoid broad omnibus memory files that mix preferences, decisions, and project details
- prefer references to canonical files instead of reproducing their contents
- a memory file should be cheaper to read than the history it replaces

## Conflict Rules

When `state` and `memory` differ:
- treat `state` as authoritative for current active truth
- update memory only after the new state proves durable

When two memory entries differ:
- keep the newer canonical one
- mark the older one for retirement or archive migration

## Promotion And Demotion

Promote into memory when:
- the information is stable
- future tasks will likely need it
- the information reduces reconstruction cost

Demote out of memory when:
- it is session-specific
- it is obsolete or contradicted
- it duplicates better canonical content elsewhere
