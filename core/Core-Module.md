# Core Module

## Purpose

Define the highest-authority rules, contracts, and canonical entrypoints for `PAOS`.

`core` is the governance surface that keeps every other module structurally compatible.

## Scope

`core` owns system-wide architecture, ontology, naming, references, dependency rules, and root manifest registration.

`core` does not store current operating state, reusable domain knowledge, generated outputs, future initiatives, or retired material.

## Canonical Files

- `core/PAOS-Architecture.md`
- `core/PAOS-Directory.md`
- `core/conventions/dependency-rules.md`
- `core/conventions/naming.md`
- `core/conventions/references.md`
- `core/ontology/terms.md`
- `core/manifest/manifest.root.json`
- `core/manifest/manifest.schema.md`

## Update Rule

Update `core` only when a change affects more than one module, changes the root loading contract, or resolves a system-wide ambiguity that would otherwise be redefined locally.

If a proposed change can stay inside `state`, `knowledge`, `templates`, `reports`, `roadmap`, or `archive`, it should not be absorbed into `core`.

## Core Role

`core` exists to keep `PAOS` structurally legible across long time horizons.

It answers the system-level questions that should not be rediscovered in each session:
- what the fixed module map is
- how modules may depend on each other
- how canonical files are named and referenced
- which files are default entrypoints
- which terms have fixed meaning across the system

## Core Boundary Rule

`core` stores invariant rules, not operational content.

The following content must not be promoted into `core`:
- current task state
- active decisions tied to a live project
- reusable domain knowledge that belongs under `knowledge/`
- output skeletons that belong under `templates/`
- bounded analyses or snapshots that belong under `reports/`
- future initiative sequencing that belongs under `roadmap/`
- retired material that belongs under `archive/`

## Core Surfaces

`core` is composed of four governance surfaces:

### Architecture Surface

Defined by `core/PAOS-Architecture.md`.

Owns the fixed module map, layer model, global principles, manifest design expectations, and cross-module operating constraints.

### Directory Surface

Defined by `core/PAOS-Directory.md`.

Owns the canonical folder layout, entry files, placement rules, and change-control rule for directory structure.

### Convention Surface

Defined by:
- `core/conventions/dependency-rules.md`
- `core/conventions/naming.md`
- `core/conventions/references.md`

Owns how files are named, how modules reference one another, and which dependency directions are allowed.

### Ontology and Manifest Surface

Defined by:
- `core/ontology/terms.md`
- `core/manifest/manifest.root.json`
- `core/manifest/manifest.schema.md`

Owns fixed system vocabulary, machine-readable module registration, and the root load contract.

## Core Rule Ownership

Global rules should be defined once in `core` and reused elsewhere by reference.

Ownership map:
- module map and load order -> `core/PAOS-Architecture.md`
- folder structure and placement -> `core/PAOS-Directory.md`
- dependency direction -> `core/conventions/dependency-rules.md`
- naming contract -> `core/conventions/naming.md`
- reference contract -> `core/conventions/references.md`
- fixed terminology -> `core/ontology/terms.md`
- machine-readable registration -> `core/manifest/manifest.root.json`

No downstream module may silently redefine these contracts.

## Core Assembly Rule

`core` is the first layer that must be loaded before any task-specific expansion.

Canonical read order:
1. `core/manifest/manifest.root.json`
2. `core/PAOS-Architecture.md`
3. `core/PAOS-Directory.md`
4. relevant convention and ontology files
5. `state/state.index.md`
6. only the minimum required downstream module files

This rule exists to keep future sessions aligned on structure before reading content.

## Completion Standard

`core` is complete enough for the current foundation phase when all of the following are true:
- the fixed top-level module map is explicit and stable
- root entry files and load order are explicit
- naming, reference, and dependency rules are explicit
- fixed system terms are explicit
- every active top-level module is registered in the root manifest
- downstream modules can reference `core` without redefining system-wide rules locally

## Stable Sections

The following sections are stable and must not be changed without explicit architecture approval:
- `Scope`
- `Canonical Files`
- `Update Rule`
- `Core Role`
- `Core Boundary Rule`
- `Core Surfaces`
- `Core Rule Ownership`
- `Core Assembly Rule`
- `Completion Standard`
- `Stable Sections`

## Dependencies

- `core/PAOS-Architecture.md`
- `core/PAOS-Directory.md`
- `core/conventions/dependency-rules.md`
- `core/conventions/naming.md`
- `core/conventions/references.md`
- `core/ontology/terms.md`
- `core/manifest/manifest.root.json`

## Inputs

- system architecture constraints
- naming, reference, and dependency conventions
- fixed terminology and module registration rules

## Outputs

- canonical system rules
- root loading contract
- cross-module governance contract

## References

- `core/PAOS-Architecture.md`
- `core/PAOS-Directory.md`
- `core/conventions/naming.md`
- `core/conventions/references.md`
- `core/conventions/dependency-rules.md`
- `core/ontology/terms.md`
- `core/manifest/manifest.root.json`
- `core/manifest/manifest.schema.md`
