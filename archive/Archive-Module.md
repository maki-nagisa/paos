# Archive Module

## Purpose
- Hold inactive or superseded material outside the default `PAOS` context surface.

## Scope
- Personal `PAOS` archive governance for `ChatGPT`, `Codex`, local development environments, and AI agents.
- Covers archive role, archive boundaries, archive classes, retirement rules, and replacement mapping behavior.
- Does not act as a second active knowledge layer, a second state layer, or a generic dump for unresolved residue.

## Dependencies
- `core/manifest/manifest.root.json`
- `core/conventions/references.md`

## Canonical Files
- `archive/Archive-Module.md`
- `archive/knowledge/Archive-Knowledge.md`
- `archive/reports/Archive-Reports.md`
- `archive/roadmap/Archive-Roadmap.md`

## Inputs
- Retired knowledge
- Replaced reports
- Closed roadmap artifacts

## Outputs
- Low-priority historical storage
- Replacement mapping targets

## References
- `archive/knowledge/Archive-Knowledge.md`
- `archive/reports/Archive-Reports.md`
- `archive/roadmap/Archive-Roadmap.md`

## Update Rule
- Update this module only when archive governance, archive boundaries, or the fixed archive map materially change.
- Add retired content to the smallest owning archive registry first; do not turn this file into an inventory of archived items.
- Once a section is marked `Stable`, later work must reference it rather than silently redefining it.

## Archive Role

`archive` exists to retain historical material without letting history dominate current work.
It is the controlled retirement layer for content that is no longer active but still worth keeping for traceability, comparison, or explicit lookup.

Archive is not default context.
It should preserve just enough replacement and retirement information for recovery without pulling inactive material back into active decision surfaces.

Archive must satisfy all of the following:
- keep inactive material out of default load paths
- preserve replacement or retirement meaning when a canonical artifact is superseded
- support explicit lookup when historical evidence is required
- remain cheaper to ignore than to load by default
- prevent stale material from silently competing with current truth

Archive must not become a parking lot for unresolved drafts, current blockers, or content that still belongs in active modules.

## Archive Boundary Rule

`PAOS` keeps `archive` separate from active layers so retired content does not regain default authority.

| Layer | Role | Default Load | Time Horizon |
| --- | --- | --- | --- |
| `state` | current active truth | yes | now |
| `knowledge` | durable reusable truth | selective | long-lived |
| `reports` | bounded synthesized outputs | selective | point-in-time |
| `archive` | inactive retained history | no | historical |

Boundary rules:
- if the content is still current or default-load worthy, keep it out of `archive`
- if the content is durable and still authoritative, keep it in `knowledge`, `state`, `reports`, or `roadmap`
- if the content has been replaced, closed, or retired but still needs traceability, move it to `archive`
- if the content is low-value residue with no future lookup value, do not preserve it as a canonical archive document

## Archive Classes

The `archive` module is fixed to the following first-wave classes:

| Archive Class | Role | Canonical Surface |
| --- | --- | --- |
| `archived knowledge` | retired or replaced durable knowledge | `archive/knowledge/` |
| `archived reports` | replaced or stale bounded outputs | `archive/reports/` |
| `archived roadmap` | completed or retired planning artifacts | `archive/roadmap/` |

Class rules:
- each archive class owns one kind of retired active-layer artifact
- archive files should preserve retirement meaning, not restate the full original body by default
- new archive work must fit an existing class unless architecture approval changes the fixed map

## Archive Admission Rule

Move an artifact into `archive` only when all of the following are true:
1. it no longer belongs in the active default context
2. it has been replaced, closed, or explicitly retired
3. future sessions may still need historical lookup, traceability, or replacement mapping
4. keeping it active would increase context cost or ambiguity

Do not archive material merely because it is unfinished, confusing, or not yet properly placed.

## Archive Replacement Rule

When archived content has an active successor, preserve the replacement relationship explicitly.

Replacement rules:
- point from the archived artifact to the current canonical owner when one exists
- prefer a compact replacement mapping over copying the active artifact into archive
- when no direct successor exists, record the retirement reason instead of fabricating a replacement target

## Completion Standard

The `archive` module is complete for this phase only when all of the following are true:
- archive role and boundaries are explicit
- archive classes are fixed for the current phase
- admission and replacement rules keep stale content out of active context
- archive registries can support explicit historical lookup without redefining active truth
- future chapters can extend archive governance without reopening the module contract

## Stable Sections

The following sections are now treated as `Stable` for the current architecture phase:
- `Archive Role`
- `Archive Boundary Rule`
- `Archive Classes`
- `Archive Admission Rule`
- `Archive Replacement Rule`

Stable rule:
- later chapters and later modules may extend these sections only by referencing them
- they must not silently redefine, contradict, or partially overwrite them
- any change requires explicit architecture approval and a direct edit to this file first

Current status for this file: `Stable`
