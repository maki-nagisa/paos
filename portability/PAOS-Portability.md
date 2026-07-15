# PAOS Portability

`PAOS` portability keeps the canonical architecture and current-state surfaces in Git while leaving machine-specific paths and secrets on each device.

## Portable Scope

- versioned: bootstrap files, manifests, schemas, templates, canonical module documents, formal state, active reports, and portability runbooks
- local-only: `config/machine.local.yaml`, secrets, runtime caches, logs, temp data, local databases, generated indexes, and device credentials

## Required Files

- tracked template: `config/machine.example.yaml`
- ignored local config: `config/machine.local.yaml`
- writer coordination: `state/current/Active-Writer.yaml`
- onboarding and recovery runbooks: `portability/`

## Portability Rules

1. keep `PAOS` core semantics device-independent
2. resolve local paths from `config/machine.local.yaml`
3. commit formal state only after bounded review
4. never commit secrets, logs, caches, or local runtime artifacts
5. pull before editing current state on another device
