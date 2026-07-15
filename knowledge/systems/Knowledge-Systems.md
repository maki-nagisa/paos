# Knowledge Systems

## Purpose
- Organize knowledge about system structures, environments, and operating surfaces.
- Define how `PAOS` models the systems it runs with, depends on, and coordinates.

## Dependencies
- `knowledge/Knowledge-Module.md`
- `state/State-Module.md`

## Inputs
- System models
- Environment structures
- Stable descriptions of tools, runtimes, interfaces, and operating boundaries

## Outputs
- System knowledge registry
- System reference anchors
- Canonical system models with explicit ownership and reference rules

## References
- `knowledge/Knowledge-Module.md`
- `knowledge/domains/Knowledge-Domains.md`
- `knowledge/workflows/Knowledge-Workflows.md`

## Scope

`systems` owns durable knowledge about the operating surfaces around `PAOS`.
It describes what systems exist, what role each system plays, what boundaries apply, and how other modules should reference them.

It does not store live machine status, one-time setup traces, or temporary runtime incidents.

## System Role

`systems` is the structural map for external and local execution surfaces.
It explains the stable shape of the environment so that future work does not need to rediscover where reasoning happens, where execution happens, where state is stored, and what interfaces connect them.

System knowledge should answer:
- what system exists
- what responsibility it has
- what interface it exposes
- what data or state boundary applies
- what other modules may rely on it

## System Boundary Rule

Place information in `systems` only if it describes a durable operating surface or a stable relationship between systems.

Boundary rules:
- if the content describes current live status, keep it in `state`
- if the content describes a repeatable execution flow, keep it in `workflows`
- if the content describes a reusable abstraction independent of one concrete system, keep it in `patterns`
- if the content describes a validated fix to a concrete issue, keep it in `solutions`
- if the content is a point-in-time assessment or audit, keep it in `reports`

## Canonical System Map

The first-wave system map for `PAOS` is fixed to the following system classes:

| System Class | Role | Typical Examples |
| --- | --- | --- |
| `reasoning-systems` | AI reasoning surfaces | `ChatGPT`, `Codex` |
| `execution-systems` | local tool and runtime surfaces | shell, local scripts, package runtimes |
| `workspace-systems` | file and project operating surfaces | repositories, working trees, canonical folders |
| `memory-systems` | durable recall surfaces | structured memory tools, curated knowledge stores |
| `integration-systems` | external interfaces and connectors | APIs, MCP servers, local bridges |

Map rules:
- each concrete system should be assigned to one primary system class
- a system may support multiple workflows, but its structural definition belongs in one place
- system classes may gain canonical child files later, but this top-level map must stay stable unless architecture approval changes it

## System Unit Rule

Every canonical system description should be expressible as a compact system unit.

Recommended fields:
- `systemId`
- `title`
- `systemClass`
- `role`
- `interface`
- `inputs`
- `outputs`
- `stateBoundary`
- `dependencies`
- `failureSurface`
- `ownerFile`
- `status`

Unit rules:
- prefer one system unit per durable operating surface
- describe the current stable contract, not setup chronology
- keep implementation detail only when it changes usage or dependency reasoning

## Reference Rule

Other modules should reference `systems` when they need an environment model or operating-surface boundary.

Reference rules:
- `workflows` may reference `systems` to declare execution surfaces
- `solutions` may reference `systems` to anchor a fix to a concrete operating surface
- `state` may point to a system when current work depends on it, but should not duplicate its structural definition
- `reports` may summarize system findings, but should point back to the canonical system file

## Completion Standard

The `systems` submodule is complete for this phase only when all of the following are true:
- its role is distinct from `state`, `workflows`, `patterns`, and `solutions`
- the canonical system map is fixed
- system units have a standard field contract
- cross-module reference behavior is explicit
- future system files can be added without redefining the base rules here

## Stable Sections

The following sections are now treated as `Stable` for the current architecture phase:
- `System Role`
- `System Boundary Rule`
- `Canonical System Map`
- `System Unit Rule`
- `Reference Rule`

Stable rule:
- later system documents must reference these sections instead of redefining them
- any change requires an explicit update here first

Current status for this file: `Stable`
