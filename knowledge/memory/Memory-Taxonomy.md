# Memory Taxonomy

## Purpose
- Define fixed memory classes for PAOS so future modules use the same language.

## Dependencies
- `knowledge/memory/Knowledge-Memory.md`
- `core/PAOS-Architecture.md`

## Inputs
- Durable facts
- Reusable decisions
- Validated solutions

## Outputs
- Stable memory classification
- Promotion targets for future memory entries

## References
- `knowledge/memory/Memory-Rules.md`
- `knowledge/memory/Memory-Retrieval.md`

## Classes

### `Preference Memory`
- stable user preferences that affect execution style, constraints, or output shape
- examples: preferred workflow, context-loading rule, validation preference

### `Decision Memory`
- architecture or operating decisions that future work must inherit
- examples: fixed module boundaries, naming rules, dependency constraints

### `Solution Memory`
- reusable problem-solution units with clear trigger conditions
- examples: proven local repair pattern, known workaround, verified fix path

### `Project Memory`
- long-lived facts about an active project that are expensive to rediscover
- examples: canonical entrypoints, key invariants, fixed directory roles

### `Reference Memory`
- compact pointers to high-value external or internal reference sources
- examples: canonical spec location, authority file, source of truth index

## Exclusions

The following are not memory classes:
- raw conversation logs
- temporary TODO lists
- step-by-step execution diaries
- large copied reports
- obsolete superseded decisions

## Class Selection Rule

Choose the narrowest class that explains future reuse.
Do not place one entry in multiple classes unless the system cannot retrieve it cleanly from one canonical location.
