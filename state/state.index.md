# State Index

## Purpose
- Register the active state entrypoints that `PAOS` loads by default.

## Dependencies
- `state/State-Module.md`
- `core/manifest/manifest.root.json`

## Inputs
- Current state submodule definitions
- Current load-priority rules

## Outputs
- State entrypoint registry
- Default-load navigation surface

## References
- `state/current/Status.md`
- `state/current/Current-Task.md`
- `state/decisions/Decision-Index.md`
- `state/active-projects/Active-Projects.md`

## Default Load Rule

`state` is the first content layer after `core`.
Default loading should stop at the smallest set of state surfaces needed to recover current truth.

Load order:
1. `state/state.index.md`
2. `state/current/Status.md`
3. `state/current/Current-Task.md`
4. `state/decisions/Decision-Index.md` only if behavior depends on current decisions
5. `state/active-projects/Active-Projects.md` only if active project scope matters

## State Surface Priority

- `Status` answers what is true now at the module and architecture level.
- `Current-Task` answers what is actively being advanced now.
- `Decision-Index` answers what effective decisions constrain work now.
- `Active-Projects` answers what scoped efforts remain in current state.

## State Index Rule

- `state.index.md` is a navigation and load-order surface, not a narrative log
- it should remain smaller than the state files it points to
- it should change only when state entrypoints or load behavior change
