# Decision Index

## Purpose
- Register the current effective decisions that shape `PAOS` behavior.

## Dependencies
- `state/State-Module.md`
- `core/PAOS-Architecture.md`

## Inputs
- Accepted architectural decisions
- Accepted operating decisions

## Outputs
- Current decision surface
- Decision lookup entrypoint

## References
- `state/state.index.md`
- `state/current/Status.md`
- `knowledge/Knowledge-Module.md`

## Decision Role

`decisions` owns the active decision surface for `PAOS`.
It keeps effective decisions visible without preserving the full discussion that produced them.

Decision records should answer:
- what decision is currently effective
- what scope it governs
- what constraint it imposes
- what supersedes it if it changes

## Decision Rule

- store final effective decisions, not open-ended discussion trails
- prefer compact decision statements over explanatory chronology
- when a decision is superseded, update current state and move obsolete detail out of default load

## Current Effective Decisions

- `knowledge` remains the durable truth layer; reusable facts should be promoted there instead of accumulating in `state`
- `state` remains the default current-truth surface and should replace stale process narration with current authority
- `archive` remains excluded from default load and must not become an active dependency
- `Stable` sections in canonical files cannot be silently redefined by later chapters
