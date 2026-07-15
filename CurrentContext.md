# Current Context

- `Role`: bootstrap-layer loading context for every new `PAOS` task
- `System Posture`: `PAOS v1` in `Operational` status inside the fixed module map
- `Current Version`: `1.0.0`
- `Default Work Type`: `Normal Operations`
- `Allowed Work Types`: `Normal Operations`, `Runtime Validation`, `Maintenance`, `Architecture`
- `Default Bootstrap`: `README.md`, `Bootstrap.md`, `OperatingRules.md`, `CurrentContext.md`, `bootstrap/README.md`, `core/manifest/manifest.root.json`
- `Cross-Device Bootstrap`: `config/machine.local.yaml` when present, otherwise `config/machine.example.yaml`
- `Default State Recovery`: `state/state.index.md`, `state/current/Status.md`, `state/current/Active-Writer.yaml`, `state/current/Current-Task.md`
- `Bootstrap Status`: root bootstrap layer confirmed and active
- `Last Confirmed`: `2026-07-15` root bootstrap and core contract review passed
- `Optimization Focus`: reduce startup tokens, reduce default document reads, shorten bootstrap time
- `Module Selection Rule`: after bootstrap, load only the smallest canonical surface required by the current task; use `state` for current truth, `knowledge` for durable reusable guidance, `roadmap` for planned change, `reports` for bounded evidence, `templates` for output contracts, and `archive` only when historical material is explicitly required
- `Files To Load`: bootstrap layer first, then the owning module entry and only the task-required canonical files beneath it
- `Device Path Rule`: use `config/machine.local.yaml` for local workspace, archive, and backup paths; keep root contracts device-independent
- `Files Forbidden`: full-tree `paos/` reads by default; `archive/` by default; unrelated stable module bodies without an owning maintenance reason
- `Constraints`: keep context bounded; prefer canonical updates over parallel explanation files; do not treat this file as the active task record
- `Task Source Of Truth`: `state/current/Current-Task.md`
- `Route Source Of Truth`: `Roadmap.md` for root bootstrap route, `roadmap/` module files for architecture-facing evolution
