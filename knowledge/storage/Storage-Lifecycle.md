# Storage Lifecycle

## Purpose
- Define how artifacts move through PAOS storage over time.

## Dependencies
- `knowledge/storage/Knowledge-Storage.md`
- `knowledge/storage/Storage-Layers.md`
- `knowledge/storage/Storage-Rules.md`

## Inputs
- New artifacts
- Updated canonical files
- Superseded materials

## Outputs
- Predictable storage transitions
- Lower drift between active and inactive material

## References
- `state/state.index.md`
- `archive/Archive-Module.md`

## Lifecycle States

### `Draft`
- newly created but not yet canonical
- may exist outside manifests while under active shaping

### `Canonical Active`
- validated and registered in the relevant manifest
- expected to be the current source of truth for its scope

### `Superseded`
- replaced by a newer canonical artifact
- no longer valid as the default reference

### `Archived`
- retained only for history, audit, or rollback context
- excluded from normal retrieval unless explicitly needed

## Transition Rules

`Draft -> Canonical Active`
- requires clear layer ownership
- requires stable name and placement
- requires manifest registration
- requires non-duplication with existing canonical files

`Canonical Active -> Superseded`
- occurs when a newer artifact replaces the same authority role
- the old artifact must stop being the default reference

`Superseded -> Archived`
- use when historical retention still has value
- move out of active module paths when the artifact no longer serves current work

`Canonical Active -> Archived`
- allowed when a once-active artifact is no longer relevant and no replacement is needed in active context

## Promotion Guidance

Promote an artifact into canonical active storage when:
- it expresses durable truth
- it materially lowers future context cost
- it has a stable retrieval purpose

Keep an artifact as draft when:
- the structure is still moving
- the authority layer is still unclear
- the content is too transient to justify canonization

Archive an artifact when:
- it is historically useful but operationally inactive
- it would otherwise clutter current retrieval
- its replacement already exists elsewhere as active truth

## Lifecycle Principle

Storage should converge toward fewer active canonical files and clearer historical separation over time.
