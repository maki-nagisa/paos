# Bootstrap

This file defines the executable bootstrap protocol for `PAOS`.
It is the task-flow layer that sits between the entry README and the deeper module set.

## Task Flow

```text
Task Start
  -> Load README
  -> Load Bootstrap
  -> Load OperatingRules
  -> Load CurrentContext
  -> Recover Current State
  -> Load Current Module Files
  -> Execute
  -> Review
  -> Update Manifest
  -> Update Current Task
  -> Update CurrentContext when bootstrap rules changed
  -> Update Roadmap when needed
  -> Task Finish
```

## Work-Type Rule

Before module loading expands beyond the bootstrap layer, classify the task as one of:

- `Normal Operations`
- `Runtime Validation`
- `Maintenance`
- `Architecture`

Default to `Normal Operations` unless the task clearly requires one of the other three.

## Start Protocol

At task start:

1. read `README.md`
2. read `Bootstrap.md`
3. read `OperatingRules.md`
4. read `CurrentContext.md`
5. read `bootstrap/README.md`
6. read `core/manifest/manifest.root.json`
7. read `config/machine.local.yaml` when present, otherwise read `config/machine.example.yaml`
8. read `state/state.index.md`
9. read `state/current/Status.md`
10. read `state/current/Active-Writer.yaml`
11. read `state/current/Current-Task.md`
12. load only the current module files required by the task

## Execution Protocol

During execution:

- stay within the smallest file set needed for the current task
- prefer canonical updates over adding side explanations
- do not read the full `PAOS` tree
- resolve device-local paths from `config/machine.local.yaml` instead of fixed drive assumptions
- do not modify `stable` module bodies unless the change belongs to their owning maintenance surface

## Review Protocol

After execution and before finishing:

1. review the changed files against `OperatingRules.md`
2. verify reference consistency
3. verify terminology consistency
4. verify that new content reduces context cost rather than increasing residue
5. decide whether a compact review output is needed

## Update Protocol

After review:

1. update `Manifest.json` when files, dependencies, statuses, or references changed
2. update `state/current/Current-Task.md` when the active task changed
3. update `CurrentContext.md` when bootstrap loading rules, role boundaries, or default root context changed
4. update `Roadmap.md` when route or completion state changed

## Finish Protocol

Task may finish only when all required exit conditions are satisfied.

Required exit conditions:

- current goal is complete or explicitly blocked
- review is complete
- `Manifest.json` is current when structural metadata changed
- `state/current/Current-Task.md` is current when task state changed
- `CurrentContext.md` is current when bootstrap context changed
- `Roadmap.md` is current when route state changed

If any required condition is missing, continue the task or leave the task explicitly open.
