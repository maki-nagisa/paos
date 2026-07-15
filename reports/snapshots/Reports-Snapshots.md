# Reports Snapshots

## Purpose
- Register point-in-time snapshot outputs that may support active analysis without becoming default context.

## Scope
- Define how `PAOS` handles point-in-time report artifacts and state captures.
- Separate bounded snapshots from active default report surfaces.
- Prevent time-stamped exports from silently becoming canonical truth.

## Dependencies
- `reports/Reports-Module.md`
- `templates/reports/report-template.md`

## Inputs
- Snapshot artifacts
- Snapshot freshness metadata

## Outputs
- Snapshot registry
- Snapshot lookup anchor

## References
- `reports/indexes/reports.index.md`
- `reports/active/Reports-Active.md`
- `archive/reports/Archive-Reports.md`

## Snapshot Role

Snapshots preserve a bounded view of a specific moment, audit pass, or evidence package.
They are useful when a task needs the exact captured surface, but they should remain optional and non-authoritative by default.

## Snapshot Rule

Use a snapshot when at least one of the following is true:
- the task needs a point-in-time export or capture
- freshness itself matters to the interpretation
- active state or active reports would become too noisy if the artifact were loaded by default

Do not use a snapshot as the canonical source of durable truth when the content has already been promoted into `state` or `knowledge`.

## Snapshot Registry

- no snapshot reports are registered as current canonical snapshot surfaces in this phase
- add entries only when a point-in-time artifact is worth preserving for explicit lookup

## Snapshot Naming Rule

- snapshot report instances should use time-bounded names such as `snapshot-<topic>-YYYYMMDD.json`
- snapshot registries should describe freshness and bounded scope, not restate the entire snapshot body
