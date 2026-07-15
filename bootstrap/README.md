# Bootstrap Device Rules

This file adds cross-device loading rules to the existing `PAOS` bootstrap entry.

## Load Order

1. core architecture
2. root manifest
3. `config/machine.local.yaml`
4. current state
5. active writer
6. current task
7. active knowledge
8. active reports

## Device Rules

- core documents must not depend on a fixed drive letter
- local paths come from `config/machine.local.yaml`
- `config/machine.local.yaml` must not enter Git
- first bootstrap on a new device must be validated in read-only mode
- current-state writes require active writer ownership
