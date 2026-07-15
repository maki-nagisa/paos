# PAOS

`PAOS` is the bootstrap entrypoint for `Personal AI Operating System` inside Codex.
It provides the single startup entry into the existing stable module set.

## Purpose

- provide one unambiguous entrypoint for `PAOS`
- point Codex to the minimum bootstrap files needed before state recovery
- keep startup context small and bounded

## Bootstrap Layer

The root files in `PAOS` act as a bootstrap layer.
They define how Codex starts, executes, reviews, updates, and stops work with minimum default loading.

Bootstrap layer files:

- `README.md`
- `Bootstrap.md`
- `OperatingRules.md`
- `CurrentContext.md`
- `Lifecycle.md`
- `Roadmap.md`
- `Manifest.json`

## Start Here

Every new task should load files in this order:

1. `README.md`
2. `Bootstrap.md`
3. `OperatingRules.md`
4. `CurrentContext.md`
5. `bootstrap/README.md`
6. `core/manifest/manifest.root.json`
7. `config/machine.local.yaml` when present
8. `state/state.index.md`
9. `state/current/Status.md`
10. `state/current/Active-Writer.yaml`
11. `state/current/Current-Task.md`
12. only the module files explicitly needed for the task

## Work Types

`PAOS` uses four fixed work types:

- `Normal Operations`: default mode for nearly all real work
- `Runtime Validation`: one bounded validation pass after major `core` changes
- `Maintenance`: repair of a confirmed runtime defect or broken reference
- `Architecture`: rare structural adjustment only when a major approved change is required

`Architecture` is not the default daily operating mode.

Default module expansion order after the bootstrap layer:

1. recover current truth from `state`
2. choose the owning module for the task
3. load that module entry file
4. load task-specific canonical files only

## Priority Files

- bootstrap entry: `README.md`
- bootstrap protocol: `Bootstrap.md`
- operating rules: `OperatingRules.md`
- bootstrap loading context: `CurrentContext.md`
- cross-device bootstrap rules: `bootstrap/README.md`
- lifecycle surface: `Lifecycle.md`
- bootstrap index: `Manifest.json`
- machine config template: `config/machine.example.yaml`
- bootstrap maintenance route: `Roadmap.md`
- active writer state: `state/current/Active-Writer.yaml`
- active task record: `state/current/Current-Task.md`
- machine module registry: `core/manifest/manifest.root.json`
