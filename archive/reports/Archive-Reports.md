# Archive Reports

## Purpose
- Register inactive or replaced report artifacts outside the active report surface.

## Scope
- Register superseded, stale, or retired bounded reports whose active authority has ended.
- Keep report history reachable by explicit lookup without letting old outputs compete with active reports.
- Do not become a second active report index.

## Dependencies
- `archive/Archive-Module.md`
- `reports/Reports-Module.md`

## Inputs
- Archived reports
- Report replacement mappings

## Outputs
- Report archive registry
- Archive lookup anchor

## References
- `archive/Archive-Module.md`
- `reports/Reports-Module.md`
- `reports/indexes/reports.index.md`

## Report Archive Role

This registry exists to keep replaced or inactive reports traceable after they leave the active report surface.

## Registry Rule

- archive reports when a fresher or stronger bounded output replaces them, or when their question no longer belongs in active context
- preserve replacement mapping and retirement reason where useful
- do not keep duplicate active and archived report entries describing the same current answer

## Current Archived Reports

- no archived report entries are registered as canonical archive surfaces in this phase
