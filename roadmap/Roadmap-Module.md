# Roadmap Module

## Purpose
- Track intended structural evolution of `PAOS` without storing execution residue.
- Define the canonical planning layer for controlled long-term evolution of `PAOS`.

## Dependencies
- `core/manifest/manifest.root.json`
- `state/State-Module.md`
- `knowledge/Knowledge-Module.md`

## Inputs
- Architecture gaps
- Planned system improvements

## Outputs
- Active initiatives
- Horizon-level planning view
- Compact forward-change contracts that do not require replaying past discussion

## References
- `roadmap/roadmap.index.md`
- `roadmap/horizons/Roadmap-Horizons.md`
- `roadmap/initiatives/Roadmap-Initiatives.md`

## Scope

`roadmap` owns intended future structural change.
It stores what should change next, why it should change, and what exit condition defines completion.

It does not store execution transcripts, sprint diaries, or historical planning residue that no longer governs future work.

## Roadmap Role

`roadmap` is the forward-planning control surface for `PAOS`.
It exists so the system can evolve intentionally without depending on scattered discussion history.

Roadmap should answer:
- what architectural change is still intended
- what priority it has
- what dependency gates apply
- what target state defines completion
- what can be deferred or archived

## Roadmap Boundary Rule

Place content in `roadmap` only if it expresses future structural intent with active planning authority.

Boundary rules:
- if the content describes current truth, place it in `state`
- if the content describes durable reusable rules, place it in `knowledge` or `core`
- if the content is a bounded analysis or evidence set, place it in `reports`
- if the planning item is complete and no longer active, reflect it into canonical modules and move historical residue out of active roadmap

## Roadmap Surfaces

The first-wave `roadmap` surfaces for `PAOS` are fixed to the following groups:

| Roadmap Surface | Role | Canonical Entry |
| --- | --- | --- |
| `roadmap-index` | active planning entrypoint and load surface | `roadmap/roadmap.index.md` |
| `horizons` | grouped planning by time and structural depth | `roadmap/horizons/Roadmap-Horizons.md` |
| `initiatives` | discrete change units and sequencing | `roadmap/initiatives/Roadmap-Initiatives.md` |

Surface rules:
- each roadmap item should belong to one primary horizon and one primary initiative record
- roadmap surfaces should compress future intent, not narrate planning discussion
- future planning files may extend these surfaces without changing the fixed first-wave map

## Roadmap Unit Rule

Every canonical roadmap item should be expressible as a compact roadmap unit.

Recommended fields:
- `initiativeId`
- `title`
- `targetModule`
- `problem`
- `targetState`
- `constraints`
- `dependencies`
- `priority`
- `status`
- `exitCriteria`
- `ownerFile`

Unit rules:
- one unit should capture one meaningful structural change
- roadmap items should describe intended future truth, not execution chronology
- when an item is complete, its durable result should move into canonical modules rather than remain only in roadmap text

## Roadmap Lifecycle Rule

`roadmap` should stay small by keeping only active future change.

Lifecycle rules:
- active items remain in `roadmap` only while they still govern future work
- completed items should be reflected into `core`, `state`, `knowledge`, or other owning modules
- superseded planning detail should be removed from active surfaces and retained only where explicitly needed

## Completion Standard

The `roadmap` module is complete for this phase only when all of the following are true:
- its role is distinct from `state`, `knowledge`, `reports`, and `archive`
- the first-wave roadmap surfaces are fixed
- roadmap units have a standard field contract
- lifecycle behavior prefers active future intent over planning accumulation
- future roadmap files can extend the module without redefining the base contract

## Stable Sections

The following sections are now treated as `Stable` for the current architecture phase:
- `Roadmap Role`
- `Roadmap Boundary Rule`
- `Roadmap Surfaces`
- `Roadmap Unit Rule`
- `Roadmap Lifecycle Rule`

Stable rule:
- later roadmap documents must reference these sections instead of redefining them
- any change requires an explicit update here first

Current status for this file: `Stable`
