# Templates Module

## Purpose
- Provide stable document and machine-output contracts for `PAOS` artifacts.

## Scope
- Personal `PAOS` template governance for `ChatGPT`, `Codex`, local development environments, and AI agents.
- Covers template role, template boundaries, template classes, registry surfaces, and usage rules.
- Does not store filled content, historical drafts, or project-specific narrative as canonical templates.

## Dependencies
- `core/manifest/manifest.root.json`
- `core/conventions/naming.md`

## Canonical Files
- `templates/Templates-Module.md`
- `templates/manifests/Templates-Manifests.md`
- `templates/modules/Templates-Modules.md`
- `templates/reports/Templates-Reports.md`
- `templates/roadmap/Templates-Roadmap.md`

## Inputs
- Output structure requirements
- Canonical formatting rules

## Outputs
- Reusable templates
- Consistent artifact structure

## References
- `templates/manifests/manifest-template.md`
- `templates/manifests/Templates-Manifests.md`
- `templates/modules/module-template.md`
- `templates/modules/Templates-Modules.md`
- `templates/reports/report-template.md`
- `templates/reports/Templates-Reports.md`
- `templates/roadmap/roadmap-template.md`
- `templates/roadmap/Templates-Roadmap.md`

## Update Rule
- Update this module only when template governance, template boundaries, or the fixed template map materially change.
- Add concrete template wording to the smallest owning template file first; do not turn this file into a catch-all example bank.
- Once a section is marked `Stable`, later work must reference it rather than silently redefining it.

## Template Role

`templates` exists to make `PAOS` outputs structurally repeatable.
It provides the smallest reusable contract needed to create new canonical files without re-deciding structure every time.

Templates are not knowledge modules and not finished reports.
They are generation contracts that keep future files aligned with the architecture while minimizing token cost and drift.

Templates must satisfy all of the following:
- solve a recurring output-structure problem
- be reused across more than one artifact or chapter
- remain smaller than the artifacts they generate
- encode structure and required fields rather than project-specific prose
- reduce future context cost by preventing structural re-explanation

Templates must not become examples archives, duplicated canonical content, or partially filled working notes.

## Template Boundary Rule

`PAOS` keeps `templates` separate from adjacent layers so output contracts do not become live content.

| Layer | Role | Default Load | Time Horizon |
| --- | --- | --- | --- |
| `knowledge` | durable reusable truth | selective | long-lived |
| `templates` | reusable output contracts | selective | long-lived but structure-only |
| `reports` | bounded synthesized outputs | selective | point-in-time or decision-bounded |
| `archive` | inactive historical material | no | historical |

Boundary rules:
- if the file defines structure for future artifacts, keep it in `templates`
- if the file contains current authoritative truth, keep it in `state` or `knowledge`
- if the file answers a bounded question with actual conclusions, keep it in `reports`
- if the file is an obsolete template no longer governing creation, move it to `archive`

## Template Classes

The `templates` module is fixed to the following first-wave classes:

| Template Class | Role | Canonical Surface |
| --- | --- | --- |
| `manifest templates` | machine-readable module and registry contracts | `templates/manifests/` |
| `module templates` | canonical architecture and module document contracts | `templates/modules/` |
| `report templates` | bounded report output contracts | `templates/reports/` |
| `roadmap templates` | initiative and planning output contracts | `templates/roadmap/` |

Class rules:
- each template class owns one recurring artifact shape
- new template work must fit one existing class unless architecture approval changes the fixed map
- template files should register structure, not duplicate the generated artifact bodies

## Template Usage Rule

Use a template only when all of the following are true:
1. the artifact type recurs often enough to justify a stable contract
2. consistent structure materially reduces future ambiguity or drift
3. the template is smaller than repeatedly re-explaining the artifact shape
4. deleting the template would weaken cross-file consistency in `PAOS`

Do not create a new template when the output is rare, one-off, or unlikely to recur.

## Template Assembly Rule

When creating or updating a canonical artifact, load templates in this order:
1. `templates/Templates-Module.md`
2. the smallest relevant template registry file
3. the exact concrete template file for the artifact type
4. the owning module contract only if the artifact needs module-specific constraints

This keeps template usage selective and prevents overloading the default context.

## Completion Standard

The `templates` module is complete for this phase only when all of the following are true:
- template role and boundaries are explicit
- template classes are fixed for the current phase
- template usage rules block low-value template growth
- registry files can guide future artifact creation without redefining base structure
- future chapters can extend templates without reopening template governance

## Stable Sections

The following sections are now treated as `Stable` for the current architecture phase:
- `Template Role`
- `Template Boundary Rule`
- `Template Classes`
- `Template Usage Rule`
- `Template Assembly Rule`

Stable rule:
- later chapters and later modules may extend these sections only by referencing them
- they must not silently redefine, contradict, or partially overwrite them
- any change requires explicit architecture approval and a direct edit to this file first

Current status for this file: `Stable`
