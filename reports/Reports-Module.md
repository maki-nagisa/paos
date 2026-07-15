# Reports Module

## Purpose
- Store bounded synthesized outputs that summarize current state, decisions, and analysis.

## Scope
- Personal `PAOS` report governance for `ChatGPT`, `Codex`, local development environments, and AI agents.
- Covers report classes, report boundaries, snapshot handling, freshness rules, and lifecycle rules.
- Does not act as a second `knowledge` layer, a second `state` layer, or a dumping ground for logs and transcripts.

## Dependencies
- `core/manifest/manifest.root.json`
- `core/PAOS-Architecture.md`
- `templates/reports/report-template.md`
- `state/state.index.md`
- `knowledge/Knowledge-Module.md`

## Inputs
- State snapshots
- Knowledge-backed analysis
- Decision outputs

## Outputs
- Active reports
- Archived or replaced snapshots

## Canonical Files
- `reports/Reports-Module.md`
- `reports/indexes/reports.index.md`
- `reports/active/Reports-Active.md`
- `reports/active/PAOS-Principle-Compliance-Matrix.md`
- `reports/snapshots/Reports-Snapshots.md`

## References
- `reports/indexes/reports.index.md`
- `reports/active/Reports-Active.md`
- `reports/snapshots/Reports-Snapshots.md`

## Update Rule
- Update this module only when `reports` boundaries, classes, lifecycle rules, or default loading policy materially change.
- Add concrete report instances to the active or snapshot registries first; do not turn this file into an ever-growing report list.
- Once a section is marked `Stable`, later work must reference it rather than silently redefining it.

## Report Role

`reports` exists to answer bounded questions with compressed outputs.
It stores the smallest durable artifact needed to communicate current judgment, not the full path taken to reach that judgment.

Reports are downstream of `state` and `knowledge`.
They package conclusions, current facts, and explicit risks into a compact surface that can be loaded when needed and ignored when not needed.

Reports must satisfy all of the following:
- answer one bounded question or audit surface
- summarize current conclusions instead of replaying process
- point back to canonical sources instead of duplicating them
- remain optional by default unless a task explicitly needs the report
- become replaceable when fresher or stronger outputs exist

Reports must not become long-running project journals, raw logs, or hidden canonical knowledge.

## Report Boundary Rule

`PAOS` keeps `reports` separate from adjacent layers so that bounded outputs do not pollute default context.

| Layer | Role | Default Load | Time Horizon |
| --- | --- | --- | --- |
| `state` | current active truth | yes | now |
| `knowledge` | durable reusable truth | selective | long-lived |
| `reports` | bounded synthesized outputs | selective | point-in-time or decision-bounded |
| `archive` | inactive historical material | no | historical |

Boundary rules:
- if the information is the current authoritative fact that should load by default, keep it in `state`
- if the information is durable and reusable beyond the current question, keep it in `knowledge`
- if the information is a bounded synthesis, audit, matrix, decision package, or point-in-time export, keep it in `reports`
- if the report is superseded and no longer belongs in active surfaces, move it to `archive`

## Report Classes

The `reports` module is fixed to the following first-wave report classes:

| Class | Role | Default Surface |
| --- | --- | --- |
| `active reports` | currently useful bounded outputs | `reports/active/` |
| `snapshot reports` | point-in-time exports and captures | `reports/snapshots/` |
| `compliance reports` | architecture or principle audits | `reports/active/` unless superseded |

Class rules:
- `active reports` hold still-relevant outputs that may support current work
- `snapshot reports` hold time-bounded exports that should not become default truth
- `compliance reports` remain active only while they still express a governing audit surface
- new report files must fit an existing class; do not create new top-level modules or parallel report taxonomies

## Report Unit Rule

Each canonical report instance should remain expressible through the following compact fields:

- `reportId`
- `reportType`
- `title`
- `scope`
- `sourceModules`
- `currentState`
- `keyDecisions`
- `openRisks`
- `nextActions`
- `freshness`

Unit rules:
- one report should answer one bounded question
- the title and scope should let future sessions decide quickly whether to load it
- report body sections should stay smaller than the combined source material they summarize
- evidence should be referenced compactly rather than pasted in full

## Report Lifecycle Rule

Reports move through a bounded lifecycle rather than accumulating forever.

Lifecycle states:
1. `draft` - being formed, not yet a default report surface
2. `active` - currently useful, loadable on demand
3. `superseded` - replaced by a fresher or better report
4. `archived` - retained only for explicit historical need

Lifecycle rules:
- promote a report to `active` only when it communicates a stable bounded judgment
- replace rather than stack duplicate reports answering the same bounded question
- move superseded report instances out of active registries as soon as a stronger replacement exists
- keep snapshot-heavy material out of default report surfaces unless it remains the best bounded evidence package

## Completion Standard

The `reports` module is complete for this phase only when all of the following are true:
- report role and boundaries are explicit
- report classes are fixed for the current phase
- report unit fields are explicit and reusable
- report lifecycle and freshness rules prevent accumulation drift
- future chapters can add reports without redefining report governance

## Stable Sections

The following sections are now treated as `Stable` for the current architecture phase:
- `Report Role`
- `Report Boundary Rule`
- `Report Classes`
- `Report Unit Rule`
- `Report Lifecycle Rule`

Stable rule:
- later chapters and later modules may extend these sections only by referencing them
- they must not silently redefine, contradict, or partially overwrite them
- any change requires explicit architecture approval and a direct edit to this file first

Current status for this file: `Stable`
