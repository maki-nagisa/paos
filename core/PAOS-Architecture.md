# PAOS Architecture

## 1. System Position

`PAOS` is a personal AI operating system for long-term use with `ChatGPT`, `Codex`, local development environments, and AI agents.

PAOS is not a document collection.
PAOS is a continuously evolving knowledge system.

Core operating principles:
- `Knowledge > History`
- `State > Process`
- `Decision > Discussion`
- `Solution > Debug`
- `Current > Archive`
- `Modular > Long Document`
- `Compression > Accumulation`
- `AI-first`
- `Low Context`
- `Evolvable`

## 2. Architectural Model

PAOS uses a layered knowledge architecture with fixed module boundaries.

Layers:
1. `Core` - global rules, ontology, architecture, naming, dependency contracts
2. `State` - current stable state that AI should load by default
3. `Knowledge` - durable reusable knowledge modules
4. `Templates` - generation contracts for stable outputs
5. `Reports` - bounded state snapshots and synthesized outputs
6. `Roadmap` - controlled evolution, maintenance posture, and approved future architecture work
7. `Archive` - inactive history kept outside default context

Load priority:
1. `core/manifest/manifest.root.json`
2. `state/state.index.md`
3. referenced active manifests
4. only the minimum required knowledge modules
5. reports or archive only when explicitly needed

## 3. Fixed Module Map

Top-level modules are fixed in this phase and cannot be added or removed without architecture approval.

| Module | Role | Default Load | Mutable |
| --- | --- | --- | --- |
| `core` | system rules and contracts | yes | low |
| `state` | current active state | yes | high |
| `knowledge` | durable modular knowledge | selective | medium |
| `templates` | reusable document/output skeletons | selective | low |
| `reports` | bounded synthesized outputs | selective | high |
| `roadmap` | planned evolution and sequencing | selective | medium |
| `archive` | inactive history | no | low |

## 4. Canonical Directory

The canonical tree is defined in `core/PAOS-Directory.md`.

Directory control rules:
- `PAOS-Directory.md` is the structural source of truth for folder layout
- `manifest.root.json` is the machine-readable source of truth for module registration
- folder additions must stay inside an approved top-level module
- top-level module changes require explicit architecture approval

## 5. Module Responsibilities

### `core`
- defines architecture, ontology, naming, references, and dependency contracts
- contains the root manifest and all system-level invariants
- must stay small, stable, and high-authority

### `state`
- stores only current, active, decision-grade state
- preferred over reading raw history
- contains current decisions, active projects, and current operating assumptions

### `knowledge`
- stores reusable knowledge modules
- each module must capture stable knowledge, not transient work traces
- modules should be independently loadable
- operational automation belongs under `knowledge/workflows/` as reusable execution knowledge, not as a new top-level module

### `templates`
- stores generation contracts, not filled-in content
- every stable output type should have a template before scale expansion

### `reports`
- stores compressed outputs derived from current state or analysis
- reports are bounded artifacts, not permanent default knowledge

### `roadmap`
- stores planned changes to architecture, modules, and system evolution
- roadmap tracks intended future state, not execution transcripts

### `archive`
- stores inactive or superseded material
- archive is not part of the default context surface

## 6. Dependency Rules

Allowed dependency direction:

```text
core -> state -> knowledge -> reports
core -> templates -> reports
core -> roadmap
state -> roadmap
knowledge -> roadmap
archive <- any retired module output
```

Rules:
- `core` depends on nothing outside `core`
- `state` may reference `core`, but must not depend on `reports`
- `knowledge` may reference `core` and `state`, but must not require `archive`
- `templates` may reference `core` conventions only
- `reports` may reference `core`, `state`, `knowledge`, and `templates`
- `roadmap` may reference `core`, `state`, and `knowledge`
- `archive` must never be a required dependency of active modules

## 7. Reference Model

Reference rules are fixed:
- use relative repository paths from `paos/`
- one module references another through a manifest entry first
- direct inline duplication is forbidden when a canonical module already exists
- summaries may reference details; details must not restate global rules
- archives are referenced only by explicit need, never by default

Reference forms:
- module reference: `knowledge/patterns/<pattern-id>.md`
- workflow automation reference: `knowledge/workflows/<automation-topic>.md`
- manifest reference: `core/manifest/manifest.root.json#<module-id>`
- template reference: `templates/reports/<template-id>.md`

Canonical read path:
1. start from the root bootstrap contract in `README.md`, `Bootstrap.md`, `OperatingRules.md`, and `CurrentContext.md`
2. recover current state via `state/state.index.md`, `state/current/Status.md`, and `state/current/Current-Task.md`
3. select the owning module based on the recovered current task
4. use `core/manifest/manifest.root.json`, `core/PAOS-Architecture.md`, and `core/PAOS-Directory.md` as the high-authority structural contract
5. load only the referenced module manifests or canonical files required by the task

## 8. Naming Standard

Naming goals:
- stable
- sortable
- machine-readable
- low ambiguity
- low token cost

Rules:
- folders use `kebab-case`
- manifest ids use `dot.case`
- file basenames use `Pascal-Topic.md` for canonical docs and `snake_case.json` for machine files
- one file should express one module or one contract
- avoid date prefixes in canonical files
- dates are allowed only in reports, snapshots, and archive records

Naming classes:
- architecture docs: `PAOS-Architecture.md`
- ontology docs: `terms.md`
- rule docs: `dependency-rules.md`
- state indexes: `state.index.md`
- roadmap indexes: `roadmap.index.md`
- canonical module docs: `<Domain>-<Topic>.md`
- report instances: `report-<topic>-YYYYMMDD.md`
- snapshot instances: `snapshot-<topic>-YYYYMMDD.json`
- manifest files: `manifest.<scope>.json`

## 9. Manifest Design

Manifest is the machine-readable backbone of PAOS.

Required manifest levels:
- `root manifest` - system entry and module registry
- `module manifest` - per-folder module registry where needed
- `report manifest` - report metadata
- `archive manifest` - archive index and replacement mapping

Root manifest required fields:
- `systemId`
- `systemName`
- `version`
- `defaultEntry`
- `modules`
- `loadOrder`
- `referenceRules`
- `namingRules`
- `statusPolicy`
- `archivePolicy`

Per-module manifest recommended fields:
- `moduleId`
- `title`
- `purpose`
- `scope`
- `inputs`
- `outputs`
- `dependsOn`
- `defaultLoad`
- `owner`
- `status`

Manifest operating rules:
- manifests are authoritative over ad hoc folder interpretation
- every active top-level module must have a manifest path registered in the root manifest
- manifests describe current truth, not historical change logs
- manifests should point to canonical entry files before any deeper content file
- manifest fields should be stable enough for AI loading and lightweight tooling

## 10. Report Design

Reports are compressed deliverables, not long-form history.

Report types:
- `state-report` - current state summary
- `analysis-report` - bounded analysis outcome
- `decision-report` - final decision record
- `solution-report` - stable solution summary
- `audit-report` - compact compliance or structure audit
- `snapshot-report` - point-in-time state export

Required report fields:
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

Report rules:
- one report answers one bounded question
- reports summarize state and decisions only
- raw logs, chat traces, and long debug transcripts stay out of reports
- stale reports should be archived or replaced by fresher equivalents

## 11. Template Design

Templates provide stable output contracts.

Template classes:
- `manifest-template`
- `module-template`
- `report-template`
- `roadmap-template`
- `decision-template`
- `state-template`

Template rules:
- templates define sections, required metadata, and allowed optional fields
- templates must be smaller than the average document they generate
- templates should optimize for AI filling and AI reading
- templates must not embed project-specific narrative by default

## 12. Roadmap Design

Roadmap is architecture-facing, not task-log-facing.

Roadmap levels:
- `horizon-1` - current approved maintenance work
- `horizon-2` - next approved major capabilities
- `horizon-3` - long-range architectural evolution

Roadmap unit fields:
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

Roadmap rules:
- roadmap stores intended architecture changes, not chat-driven TODO drift
- every roadmap item must target a named module or system rule
- completed roadmap items should be reflected into `core`, `state`, or `knowledge`, then removed from active roadmap and archived if needed

## 13. Automation Design

Automation in `PAOS` is a knowledge-governed execution contract, not a dump of scripts, logs, or one-off runs.

Automation placement:
- reusable automation knowledge belongs in `knowledge/workflows/`
- active runtime state for automation belongs in `state/`
- point-in-time automation outcomes belong in `reports/`
- retired or superseded automation material belongs in `archive/`

Automation unit fields:
- `automationId`
- `title`
- `objective`
- `trigger`
- `inputs`
- `outputs`
- `preconditions`
- `stateDependencies`
- `failurePolicy`
- `acceptanceRule`
- `ownerFile`
- `status`

Automation rules:
- automation must be expressed as reusable knowledge rather than run transcripts
- every automation must define trigger, bounded state dependency, and acceptance criteria
- automation must prefer reading canonical state and knowledge files over replaying history
- automation must write durable conclusions back into canonical modules, not leave correctness in execution traces alone
- once an automation contract is marked `Stable`, later documents may reference it but must not silently redefine it

## 14. Evolution Guardrails

Any future document added to PAOS must pass all checks:
- does it increase durable knowledge density?
- does it reduce future context load?
- is it a module rather than a long narrative?
- does it store current truth rather than process residue?
- does it avoid duplicating an existing canonical file?

If any answer is `no`, the file should not be added without explicit approval.

## 15. Initial Build Order

Initial build order used to establish the architecture surface:
1. stabilize `core` manifests and conventions
2. establish `state` indexes and current-state contracts
3. define first-wave `knowledge` module taxonomy
4. finalize `templates`
5. enable bounded `reports`
6. establish `roadmap`
7. move legacy material into `archive` selectively

## 16. Architecture Status

Current architecture status:
- top-level module set is fixed for the current architecture phase
- machine-readable root manifest exists
- per-module manifests exist
- canonical directory map exists
- all fixed top-level modules now have stable canonical governance contracts
- future change should focus on consistency control, selective extension, and disciplined evolution rather than filling structural gaps
