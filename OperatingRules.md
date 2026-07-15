# Operating Rules

This file defines the minimum rules required to operate `PAOS` during daily Codex work.
It is not a full restatement of the stable architecture documents.

## Core Principles

- `Knowledge > History`
- `State > Process`
- `Decision > Discussion`
- `Solution > Debug`
- `Current > Archive`
- `Compression > Accumulation`
- `Modular > Long Document`
- `AI-first`
- `Low Context`
- `Evolvable`

## Runtime Rules

- start every task from `README.md`, `Bootstrap.md`, `OperatingRules.md`, and `CurrentContext.md`
- load `core/manifest/manifest.root.json` before expanding into modules
- recover current truth from `state` before choosing deeper module files
- read only the canonical files required by the current task
- prefer current canonical state over replaying old work traces
- prefer updating an owning canonical file over adding a parallel explanation file
- follow the bootstrap flow for start, execute, review, update, and finish

## Change Rules

- do not modify `stable` module contracts unless the task explicitly belongs to their owning maintenance surface
- do not create new top-level modules
- do not duplicate canonical content across operating files and module files
- add files only when they reduce future context cost and clearly improve long-term maintainability

## Maintenance Rules

- keep `CurrentContext.md` limited to bootstrap loading context; do not turn it into a task log
- keep `state/current/Current-Task.md` as the single active task surface
- after each meaningful task, refresh `state/current/Current-Task.md` when the active task changed
- refresh `CurrentContext.md` only when bootstrap loading context or root boundaries changed
- reflect route or status changes into `Roadmap.md`
- reflect file, dependency, reference, and status changes into `Manifest.json`
- check terminology, manifest alignment, and reference consistency before closing the task
- do not end the task until bootstrap exit criteria are satisfied
