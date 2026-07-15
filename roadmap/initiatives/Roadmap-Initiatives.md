# Roadmap Initiatives

## Purpose
- Register discrete `PAOS` evolution initiatives tied to named modules or system rules.

## Dependencies
- `roadmap/Roadmap-Module.md`
- `roadmap/horizons/Roadmap-Horizons.md`

## Inputs
- Initiative definitions
- Target-state requirements

## Outputs
- Initiative registry
- Execution planning anchor

## References
- `roadmap/roadmap.index.md`
- `state/current/Current-Task.md`
- `state/current/Status.md`

## Active Initiatives

There is no currently open architecture-facing initiative.
`PAOS v1.0` is in maintenance mode until a real approved gap requires a new initiative.

## Recently Completed

| Initiative ID | Title | Target Module | Problem | Target State | Priority | Status |
| --- | --- | --- | --- | --- | --- | --- |
| `paos.v1.review-maintenance` | Maintain v1 review consistency | `core` | post-v1 changes could introduce terminology drift, reference drift, or manifest-state mismatch over time | canonical maintenance surfaces now align on a maintenance-first `PAOS v1.0` posture without reopening module foundations | low | complete |

## Initiative Rule

- complete one architecture-facing initiative at a time
- reflect completed initiatives into canonical module files before marking them done here
- do not open new top-level modules; evolve only within the fixed architecture map

## Initiative Fields

Each active initiative should remain expressible through the following compact contract:

- `initiativeId`
- `title`
- `targetModule`
- `problem`
- `targetState`
- `priority`
- `status`

## Exit Rule

- mark an initiative complete only after its target state is reflected into the owning canonical files
- keep only active or still-governing initiatives in the active registry
- move stale or superseded planning detail out of default roadmap surfaces
- when no initiative is active, keep the surface explicit rather than inventing placeholder work
