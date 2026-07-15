# Knowledge Module

## Purpose
- Define the canonical structure, boundaries, and operating rules for durable knowledge in `PAOS`.
- Ensure the system stores reusable knowledge rather than work traces, chat residue, or uncontrolled notes.

## Scope
- Personal long-term knowledge architecture for `ChatGPT`, `Codex`, local development environments, and AI agents.
- Covers knowledge classes, submodule responsibilities, promotion rules, stabilization rules, and reference order.
- Does not store raw conversation history, transient execution logs, or point-in-time reports as default knowledge.

## Dependencies
- `core/manifest/manifest.root.json`
- `core/PAOS-Architecture.md`
- `core/PAOS-Directory.md`
- `state/state.index.md`

## Inputs
- Stable knowledge validated across more than one use or decision cycle
- Reusable patterns and workflow abstractions
- Validated solutions and operating rules
- Durable system and domain understanding

## Outputs
- Canonical knowledge taxonomy for `PAOS`
- Modular knowledge surface with clear ownership boundaries
- Reusable reference units with low context cost
- Promotion and stabilization rules for future knowledge growth

## Canonical Files
- `knowledge/Knowledge-Module.md`
- `knowledge/domains/Knowledge-Domains.md`
- `knowledge/context/Knowledge-Context.md`
- `knowledge/memory/Knowledge-Memory.md`
- `knowledge/storage/Knowledge-Storage.md`
- `knowledge/systems/Knowledge-Systems.md`
- `knowledge/workflows/Knowledge-Workflows.md`
- `knowledge/workflows/Workflow-Automation.md`
- `knowledge/patterns/Knowledge-Patterns.md`
- `knowledge/solutions/Knowledge-Solutions.md`

## References
- `knowledge/domains/Knowledge-Domains.md`
- `knowledge/context/Knowledge-Context.md`
- `knowledge/memory/Knowledge-Memory.md`
- `knowledge/storage/Knowledge-Storage.md`
- `knowledge/systems/Knowledge-Systems.md`
- `knowledge/workflows/Knowledge-Workflows.md`
- `knowledge/workflows/Workflow-Automation.md`
- `knowledge/patterns/Knowledge-Patterns.md`
- `knowledge/solutions/Knowledge-Solutions.md`

## Update Rule
- Update this module only when the knowledge architecture, module boundaries, or governance rules change.
- Add concrete knowledge to submodules first; do not turn this file into a catch-all narrative.
- Once a section is marked `Stable`, later work must treat it as frozen unless an explicit architecture approval replaces it.

## Knowledge Role

Knowledge in `PAOS` is not history.
Knowledge is the durable layer that preserves what should remain true and reusable after the original work session is gone.

Knowledge exists to make future work cheaper and more correct.
It should reduce the need to replay old chats, re-scan long notes, or reconstruct prior decisions from residue.

Knowledge must satisfy all of the following:
- reusable across multiple tasks or sessions
- expressed as current truth rather than process narration
- modular enough to load selectively
- cheaper to retrieve than reconstructing from history
- anchored to a canonical file with clear ownership

Knowledge must not become a second `state`, a second `reports` layer, or a generic document dump.

## Knowledge Boundaries

`PAOS` separates adjacent information classes so that each one stays small and authoritative.

| Layer | Role | Default Load | Time Horizon |
| --- | --- | --- | --- |
| `state` | current active truth | yes | now |
| `knowledge` | durable reusable truth | selective | long-lived |
| `reports` | bounded synthesized output | selective | point-in-time |
| `archive` | inactive historical material | no | historical |

Boundary rules:
- if a fact is only true for the current moment or current task, keep it in `state`
- if a fact is reusable beyond the current session and should remain true later, place it in `knowledge`
- if a document answers one bounded question or audit, place it in `reports`
- if a document is superseded but still worth retaining, move it to `archive`

## Knowledge Submodule Map

The `knowledge` module is fixed to the following first-wave submodules:

| Submodule | Role | What It Owns |
| --- | --- | --- |
| `domains` | domain taxonomy | knowledge areas and their entrypoints |
| `context` | context architecture | context layers, assembly, and low-context rules |
| `memory` | durable memory rules | memory taxonomy, promotion, retrieval |
| `storage` | knowledge placement | storage layers, placement rules, lifecycle |
| `systems` | system knowledge | environments, structures, operating surfaces |
| `workflows` | reusable workflows | repeatable operating flows and execution knowledge |
| `patterns` | reusable abstractions | structural and operational patterns |
| `solutions` | validated answers | stable fixes and reusable solution units |

Submodule rules:
- each submodule must own one clear slice of durable knowledge
- each submodule should stay independently loadable
- cross-submodule references should point to canonical files, not duplicate content
- new folders must fit one of the existing submodules unless architecture approval changes the map

## Knowledge Promotion Rule

Information should enter `knowledge` only after passing all of the following checks:

1. it has reuse value beyond one task or one conversation
2. it can be expressed as knowledge rather than chronology
3. it has a clear canonical owner inside the module map
4. storing it reduces future context cost
5. it does not duplicate an existing canonical file

If any check fails, keep the material in `state`, `reports`, project files, or `archive` instead.

## Knowledge Assembly Order

When a task needs `knowledge`, load it in this order:

1. `knowledge/Knowledge-Module.md`
2. the smallest relevant submodule entry file
3. only the supporting canonical files needed by that submodule
4. `reports` or `archive` only if the task explicitly requires historical evidence

This keeps knowledge retrieval modular and prevents default expansion into narrative history.

## Stable Sections

The following sections are now treated as `Stable` for the current architecture phase:
- `Knowledge Role`
- `Knowledge Boundaries`
- `Knowledge Submodule Map`
- `Knowledge Promotion Rule`
- `Knowledge Assembly Order`

Stable rule:
- later chapters and later modules may extend these sections only by referencing them
- they must not silently redefine, contradict, or partially overwrite them
- any change requires explicit architecture approval and a direct edit to this file first

## Completion Standard

The `Knowledge` module is complete for this phase only when all of the following are true:
- the module boundary is explicitly defined
- submodule ownership is fixed
- promotion and reference rules are explicit
- storage of transient residue is prohibited
- future modules can extend knowledge without redefining its base contract

Current status for this file: `Stable`
