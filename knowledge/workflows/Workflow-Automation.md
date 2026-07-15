# Workflow Automation

## Purpose
- Define the canonical automation contract for `PAOS`.
- Keep automation as durable knowledge with explicit boundaries, instead of mixing it with chat residue, raw scripts, or execution history.

## Scope
- Personal automations used with `ChatGPT`, `Codex`, local development environments, and AI agents.
- Covers automation role, placement, lifecycle entrypoints, naming, and required acceptance surface.
- Does not store run logs, tool output transcripts, scheduler-specific configuration dumps, or implementation-specific code bodies.

## Dependencies
- `core/PAOS-Architecture.md`
- `core/PAOS-Directory.md`
- `knowledge/Knowledge-Module.md`
- `knowledge/workflows/Knowledge-Workflows.md`
- `state/state.index.md`

## Inputs
- Reusable automation objectives
- Stable trigger conditions
- Canonical state inputs and knowledge inputs
- Validated acceptance criteria

## Outputs
- Canonical automation design contract
- Stable automation naming and organization rules
- Lifecycle and acceptance references for automation authors

## Canonical Files
- `knowledge/workflows/Workflow-Automation.md`
- `knowledge/workflows/Automation-Lifecycle.md`
- `knowledge/workflows/Automation-Acceptance.md`

## References
- `knowledge/workflows/Automation-Lifecycle.md`
- `knowledge/workflows/Automation-Acceptance.md`
- `knowledge/storage/Knowledge-Storage.md`
- `knowledge/context/Knowledge-Context.md`
- `reports/Reports-Module.md`
- `state/State-Module.md`

## Update Rule
- Update this file only when the automation architecture, ownership boundary, or canonical contract changes.
- Add concrete automation examples to dedicated downstream documents later; do not turn this file into an automation catalog.
- Once a section is marked `Stable`, later chapters must reference it instead of redefining it.

## Automation Role

Automation in `PAOS` is the reusable contract that allows a repeatable task to run with bounded context and bounded correctness checks.

Automation is not the script itself.
Automation is not the chat history that led to the script.
Automation is the durable knowledge layer that defines how a repeatable action should be triggered, what canonical inputs it may consume, what outputs it may produce, and how success is verified.

An automation is valid only when it reduces future reconstruction cost and preserves enough structure that another future agent can run or evolve it without replaying prior discussion.

## Automation Boundary Rule

`PAOS` separates automation knowledge from adjacent layers:

| Layer | Automation-Relevant Role | What Must Not Live There |
| --- | --- | --- |
| `state` | current automation state, active target, current enablement | reusable automation contract |
| `knowledge/workflows` | stable automation contract and operation rules | run-by-run execution residue |
| `reports` | bounded automation audit or run outcome summary | canonical automation definition |
| `archive` | superseded automation specs and retired variants | active automation source of truth |

Boundary rules:
- keep current toggles, current target, and active runtime assumptions in `state`
- keep reusable automation design and control rules in `knowledge/workflows`
- keep audits and point-in-time outcome packets in `reports`
- move superseded automation contracts to `archive` only after a replacement is canonical

## Automation Unit Contract

Every canonical automation definition must be able to answer the following fields, whether inline or through a structured companion manifest:

| Field | Meaning |
| --- | --- |
| `automationId` | stable unique id for the automation unit |
| `title` | short human-readable name |
| `objective` | the repeatable outcome it is supposed to achieve |
| `trigger` | what starts the automation |
| `inputs` | canonical inputs it may read |
| `outputs` | canonical outputs it may produce |
| `preconditions` | what must already be true |
| `stateDependencies` | which `state` files it depends on |
| `failurePolicy` | how it stops, retries, or escalates |
| `acceptanceRule` | how correctness is checked |
| `ownerFile` | canonical defining file |
| `status` | current stability level |

The contract must stay concise enough that an agent can load it without reading implementation history.

## Automation File Organization Rule

Canonical automation knowledge follows this organization model:

1. `Knowledge-Workflows.md` defines workflow-level ownership.
2. `Workflow-Automation.md` defines the automation architecture contract.
3. `Automation-Lifecycle.md` defines allowed lifecycle states and transitions.
4. `Automation-Acceptance.md` defines verification and acceptance requirements.
5. future automation-specific documents, if approved, must live under `knowledge/workflows/` and reference these canonical files first.

Organization rules:
- do not create a new top-level `automation/` module
- do not store scheduler-specific runtime dumps as canonical architecture knowledge
- do not duplicate lifecycle or acceptance rules across automation documents
- register any new canonical automation file through the relevant manifest before treating it as active

## Automation Naming Rule

Automation naming must optimize for low ambiguity and low context cost.

Rules:
- canonical automation architecture files use `Pascal-Topic.md`
- automation ids use stable `dot.case`
- one automation document should own one contract surface
- implementation filenames may vary outside `paos/`, but the canonical automation knowledge file must remain stable
- avoid date-based names for active automation contracts

Recommended id pattern:
- `automation.<domain>.<capability>`

Examples:
- `automation.briefing.morning`
- `automation.memory.refresh`
- `automation.workspace.bootstrap`

## Stable Sections

The following sections are now treated as `Stable` for the current architecture phase:
- `Automation Role`
- `Automation Boundary Rule`
- `Automation Unit Contract`
- `Automation File Organization Rule`
- `Automation Naming Rule`

Stable rule:
- later automation documents may extend these sections only by reference
- they must not silently redefine, contradict, or narrow them without explicit architecture approval
- any such approval must update this file first

## Completion Standard

The automation architecture is complete for this phase only when all of the following are true:
- automation has a fixed owner module
- automation is separated from state, reports, and archive
- unit contract fields are explicit
- lifecycle and acceptance are defined in dedicated canonical files
- stable sections can constrain later automation growth without reopening top-level architecture

Current status for this file: `Stable`
