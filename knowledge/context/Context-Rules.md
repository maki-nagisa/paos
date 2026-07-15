# Context Rules

## Purpose
- Define the operating rules that keep PAOS context small, stable, and authoritative.

## Dependencies
- `knowledge/context/Knowledge-Context.md`
- `knowledge/context/Context-Layers.md`
- `knowledge/context/Context-Assembly.md`

## Inputs
- Context assembly needs
- Long-term maintenance constraints

## Outputs
- Canonical context control rules
- Stable rejection rules for context bloat

## References
- `core/conventions/dependency-rules.md`
- `knowledge/storage/Storage-Rules.md`
- `state/current/Status.md`

## Core Rules

- context must prefer `state` over chat history
- context must prefer canonical modules over duplicated summaries
- context must be assembled incrementally, not preloaded in bulk
- context must preserve authority order from `core` to `state` to selective `knowledge`
- context must exclude inactive history by default

## Rejection Rules

Do not add a file to default context when any of the following is true:
- the file mainly preserves process residue
- the file duplicates a canonical module already in scope
- the file is broad history instead of task-bounded truth
- the file is only useful for retrospective audit
- the file increases token load without changing likely execution quality

## Compression Rules

When context grows, compress by this order:

1. replace verbose narrative with current-state summary
2. replace repeated examples with one canonical rule
3. replace broad history with one bounded report
4. move inactive material to `archive`
5. promote recurring truths into `knowledge` only after validation

## Stable Context Rule

Once a context contract is marked `Stable`, later modules must conform to it and must not silently rewrite it.

Allowed follow-up changes after `Stable`:
- add a new dependent module that references the stable contract
- clarify wording without changing meaning
- append compatible examples in non-canonical supporting material

Disallowed follow-up changes after `Stable` without explicit architecture approval:
- changing layer order
- changing default load rules
- changing module ownership boundaries
- changing canonical file identity

## Validation Questions

Before accepting context changes, verify all of the following:
- does this reduce future context load?
- does this increase authority clarity?
- does this avoid storing transcript residue?
- does this preserve existing stable architecture?
- does this help future AI sessions start faster and safer?
