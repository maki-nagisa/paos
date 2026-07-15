# PAOS Phase 3B — Runtime Authority Cleanup Report

## Scope

- allowed modifications: runtime-chain and authority-boundary conflicts confirmed by `PAOS Phase 3A`
- forbidden modifications: architecture decisions, core contracts, bootstrap files, operating rules, root manifest, current context, module body rewrites, historical archive cleanup, formatting-only cleanup, and non-runtime repetition cleanup
- modified files in this phase:
  - `E:/codex/paos/core/manifest/manifest.root.json`
  - `E:/codex/paos/core/PAOS-Architecture.md`

## Applied Fixes

### `P3A-F-001`

- file: `E:/codex/paos/core/manifest/manifest.root.json`
- conflict evidence before:
  - `defaultEntry` pointed to `core/PAOS-Architecture.md`
  - `loadOrder` began from `core/manifest/manifest.root.json` and `core` files, without the root bootstrap layer or explicit current-task recovery
- runtime impact:
  - a consumer could start from `core` and bypass the formal root bootstrap chain, current-truth recovery, and minimal-load sequencing
- minimal repair:
  - changed `defaultEntry` to `README.md`
  - changed `loadOrder` to the formal root bootstrap sequence first, then state recovery, then `core` structural files
- authority after repair:
  - root entry remains `README.md`
  - root bootstrap remains the only declared startup chain
  - `core` remains machine-readable structural contract, not competing startup authority

### `P3A-F-002`

- file: `E:/codex/paos/core/PAOS-Architecture.md`
- conflict evidence before:
  - `Canonical read path` restated a startup sequence that began in `core` and omitted `README.md`, `Bootstrap.md`, `OperatingRules.md`, `CurrentContext.md`, `state/current/Status.md`, `state/current/Current-Task.md`, and explicit owning-module selection
- runtime impact:
  - a consumer could follow a deeper-module read path that conflicts with the formal root bootstrap contract
- minimal repair:
  - reduced the `Canonical read path` to reference the root bootstrap contract, current state recovery, owning-module selection, then `core` structural files
- authority after repair:
  - `core` documents high-authority structure without redefining runtime startup order

## Excluded Findings

- `progress.md` as current authority: not changed, because `PAOS Phase 3A` found no deeper module promoting it to current-task truth
- `CurrentContext.md` vs `state/current/Current-Task.md`: not changed, because `PAOS Phase 3A` found the active-task truth boundary already clean
- root bootstrap files: not changed, because this phase only required deeper-module runtime-authority cleanup inside `core`
- reports, roadmap, archive, and module manifests outside `core`: not changed, because `PAOS Phase 3A` did not evidence runtime-authority conflicts there

## Validation

- `core/manifest/manifest.root.json` parses successfully as JSON
- current active-task truth continues to point to `state/current/Current-Task.md`
- the only formal startup-order definition remains the root bootstrap contract
- `CurrentContext.md` remains bootstrap loading context only and contains no active-task body
- no deeper module surface was changed to use `progress.md` as recovery source
- owning-module selection is explicitly placed after current-truth recovery in the repaired architecture read path
- root authority remains above module manifests; no module manifest override was introduced
- active startup paths referenced by the repaired `core` manifest resolve to existing files
- `git diff --check` passes for this phase

## Verdict

`Pass`
