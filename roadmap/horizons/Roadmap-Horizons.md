# Roadmap Horizons

## Purpose
- Organize `PAOS` evolution by horizon rather than by raw execution timeline.

## Dependencies
- `roadmap/Roadmap-Module.md`
- `templates/roadmap/roadmap-template.md`

## Inputs
- Horizon-level priorities
- Horizon-level initiatives

## Outputs
- Horizon planning view
- Priority grouping anchor

## References
- `roadmap/roadmap.index.md`
- `roadmap/initiatives/Roadmap-Initiatives.md`
- `state/current/Current-Task.md`

## Horizon Role

`horizons` groups roadmap intent by structural distance rather than by chat order.
It exists so evolution can stay compressible and low-context while still preserving sequencing.

## Horizon Rule

- each initiative should belong to one primary horizon
- horizons should reflect planning distance and dependency order, not calendar narration
- horizons should remain stable enough that new initiatives can be slotted in without rewriting the whole roadmap

## Horizon Definitions

| Horizon | Role | Current Focus |
| --- | --- | --- |
| `horizon-1` | current approved maintenance work required to keep the architecture operationally strong | consistency control across references, terminology, manifests, and active governance surfaces |
| `horizon-2` | next major system capabilities after an approved new gap is confirmed | selective extension such as stronger decision surfaces or memory contracts when justified by real use |
| `horizon-3` | long-range architectural evolution once new approved capabilities materially accumulate | future extensibility, deeper automation governance, and advanced orchestration layers |

## Horizon Sequencing Rule

- complete or de-risk `horizon-1` maintenance items before opening broad `horizon-2` expansion
- use `horizon-2` only for capabilities that depend on a stable first-wave control surface and a confirmed new gap
- keep `horizon-3` compact and directional rather than detailed too early
