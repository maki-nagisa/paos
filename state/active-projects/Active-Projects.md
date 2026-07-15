# Active Projects

## Purpose
- Register active scoped efforts that are still part of current `PAOS` state.

## Dependencies
- `state/State-Module.md`
- `state/current/Current-Task.md`

## Inputs
- Active project list
- Project status summaries

## Outputs
- Active project registry
- Project lookup anchor

## References
- `state/state.index.md`
- `state/current/Status.md`
- `roadmap/roadmap.index.md`

## Project Role

`active-projects` owns scoped efforts that still have current operational relevance.
It keeps present work surfaces visible without turning `state` into a long project diary.

## Project Rule

- include only efforts that still affect current decisions, current task routing, or current architecture state
- remove or archive projects when they no longer change present behavior
- prefer short status statements over process logs or milestone narratives

## Current Active Projects

| Project ID | Title | Current Relevance | Status |
| --- | --- | --- | --- |
| `paos.foundation` | `PAOS` foundation architecture | active canonical architecture build-out across `state`, `knowledge`, and `roadmap` | active |
