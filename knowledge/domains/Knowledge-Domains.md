# Knowledge Domains

## Purpose
- Define the domain model that partitions durable knowledge into clear, low-context knowledge areas.
- Prevent knowledge growth from collapsing into one undifferentiated repository of notes.

## Scope
- Personal long-term `PAOS` domain architecture for `ChatGPT`, `Codex`, local development environments, and AI agents.
- Covers domain boundary rules, canonical domain classes, entrypoint expectations, and cross-domain reference policy.
- Does not define transient project folders, runtime state buckets, or report-only classifications.

## Dependencies
- `knowledge/Knowledge-Module.md`
- `core/ontology/terms.md`
- `core/PAOS-Architecture.md`
- `core/PAOS-Directory.md`

## Inputs
- Domain-scoped knowledge modules
- Reusable knowledge units that need a stable domain home
- Domain taxonomy rules
- Cross-module retrieval needs

## Outputs
- Domain registry
- Domain entrypoint references
- Domain ownership rules
- Domain routing rules for future knowledge additions

## Canonical Files
- `knowledge/domains/Knowledge-Domains.md`

## References
- `knowledge/Knowledge-Module.md`
- `knowledge/systems/Knowledge-Systems.md`
- `knowledge/patterns/Knowledge-Patterns.md`
- `knowledge/workflows/Knowledge-Workflows.md`
- `knowledge/solutions/Knowledge-Solutions.md`

## Update Rule
- Update this file only when the domain model, domain ownership rules, or cross-domain routing rules change.
- Add concrete knowledge to the owning domain module rather than expanding this file into a catalog of facts.
- Once a section is marked `Stable`, later modules must reference it rather than silently redefining it.

## Domain Role

`domains` is the classification layer inside `knowledge`.
It answers one question: which durable knowledge area should own a given reusable fact, rule, pattern, or solution?

The role of `domains` is not to store all knowledge directly.
Its role is to keep knowledge modular by giving each durable unit a stable conceptual home.

`domains` exists so that future work can:
- route new knowledge into the correct submodule quickly
- avoid duplicating the same knowledge across adjacent modules
- retrieve the smallest relevant knowledge surface for a task
- preserve `Knowledge > History` by preferring ownership over accumulation

## Domain Boundary Rule

Every durable knowledge item in `PAOS` should belong to one primary domain owner.

Boundary rules:
- one knowledge unit should have one primary owning domain
- secondary relationships should be expressed by references, not duplicated content
- domain ownership should minimize future search cost
- domain ownership should remain stable across multiple sessions when possible
- if ownership is unclear, classify by reusable function rather than by the task that produced it

Classification tests:
1. what reusable question does this knowledge answer?
2. which submodule would a future AI load first to reuse it?
3. can another module reference it instead of copying it?

If these tests do not converge, the item is not ready for durable knowledge promotion yet.

## Canonical Domain Map

The first-wave `knowledge` domain map is fixed to the approved submodule set.

| Domain | Primary Question | Canonical Entrypoint |
| --- | --- | --- |
| `domains` | how knowledge areas are partitioned | `knowledge/domains/Knowledge-Domains.md` |
| `context` | what AI should load and in what order | `knowledge/context/Knowledge-Context.md` |
| `memory` | what durable remembered knowledge should persist | `knowledge/memory/Knowledge-Memory.md` |
| `storage` | where durable knowledge should live | `knowledge/storage/Knowledge-Storage.md` |
| `systems` | what system surfaces and operating environments exist | `knowledge/systems/Knowledge-Systems.md` |
| `workflows` | what repeatable operating flows should be reused | `knowledge/workflows/Knowledge-Workflows.md` |
| `patterns` | what abstractions and structural patterns recur | `knowledge/patterns/Knowledge-Patterns.md` |
| `solutions` | what validated answers or fixes are reusable | `knowledge/solutions/Knowledge-Solutions.md` |

Domain map rules:
- this map classifies knowledge by retrieval purpose, not by department or tool brand
- new durable knowledge must fit one of these domains unless architecture approval changes the module map
- domains are entrypoints, not dumping grounds

## Domain Naming Rule

Domain naming should optimize for long-term retrieval rather than narrative completeness.

Naming rules:
- domain folders use short `kebab-case` names
- domain entry files use `Pascal-Topic.md`
- a domain name should describe a durable reusable function
- avoid names tied to one temporary project, one incident, or one date
- avoid overlapping names that force repeated disambiguation

Preferred naming shape:
- broad enough to survive multiple tasks
- narrow enough to imply ownership boundaries
- stable enough to remain cheap for AI selection

## Domain Routing Rule

When new knowledge is promoted into `knowledge`, route it by the smallest durable owner.

Routing order:
1. determine whether the item is durable enough for `knowledge`
2. select the primary owning domain from the canonical domain map
3. store the canonical statement in that domain
4. add cross-domain references only where reuse genuinely requires them

Default routing heuristics:
- reusable retrieval/loading policy -> `context`
- durable preference/decision/lesson memory -> `memory`
- placement/lifecycle/retention rule -> `storage`
- environment/tool/system surface knowledge -> `systems`
- repeatable execution flow -> `workflows`
- reusable abstraction or design shape -> `patterns`
- validated fix or answer -> `solutions`

## Cross-Domain Reference Rule

Cross-domain overlap is expected, but duplication should stay controlled.

Reference rules:
- a domain may summarize why another domain matters, but must link to the other domain for canonical detail
- domain files should reference canonical entrypoints before deeper files
- a solution may depend on a pattern, but the pattern still owns the reusable abstraction
- a workflow may consume system knowledge, but the system module still owns the environment truth
- memory may store a durable decision, but the owning operational rule should still live in its canonical domain

This preserves modular retrieval and keeps context expansion bounded.

## Domain Completion Standard

The `domains` submodule is complete for this phase only when all of the following are true:
- the approved knowledge domains are explicitly named
- each domain has a distinct retrieval question
- ownership and routing rules are explicit
- cross-domain duplication is constrained by reference rules
- future knowledge additions can be classified without reopening architecture every time

## Stable Sections

The following sections are now treated as `Stable` for the current architecture phase:
- `Domain Role`
- `Domain Boundary Rule`
- `Canonical Domain Map`
- `Domain Naming Rule`
- `Domain Routing Rule`
- `Cross-Domain Reference Rule`

Stable rule:
- later domain-level or submodule-level documents may extend by reference only
- they must not silently redefine the canonical domain map or ownership boundaries
- any change requires explicit architecture approval and a direct edit to this file first

Current status for this file: `Stable`
