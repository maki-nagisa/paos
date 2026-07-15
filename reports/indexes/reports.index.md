# Reports Index

## Purpose
- Register the active report surfaces and snapshot surfaces for `PAOS`.

## Dependencies
- `reports/Reports-Module.md`
- `templates/reports/report-template.md`

## Inputs
- Report registry definitions
- Snapshot registry definitions

## Outputs
- Report index surface
- Report lookup anchor

## References
- `reports/active/Reports-Active.md`
- `reports/active/PAOS-Architecture-Cleanup-Report.md`
- `reports/active/PAOS-Phase-3B-Runtime-Authority-Cleanup-Report.md`
- `reports/active/PAOS-Principle-Compliance-Matrix.md`
- `reports/active/PAOS-Phase-2-Review-Report.md`
- `reports/active/PAOS-Core-Refinement-Report.md`
- `reports/active/PAOS-Codex-C-Drive-Growth-ReadOnly-Analysis-Report.md`
- `reports/active/PAOS-Codex-C-Drive-Cleanup-Decision-Report.md`
- `reports/active/PAOS-Codex-C-Drive-Tmp-Cleanup-Execution-Report.md`
- `reports/active/PAOS-Git-Migration-Execution-Report.md`
- `reports/snapshots/Reports-Snapshots.md`
- `archive/reports/Archive-Reports.md`

## Active Report Focus

- `reports` is an active maintenance surface for bounded outputs that still govern current `PAOS` judgment.
- active report governance should stay compact and only expose still-governing bounded outputs.

## Current Sequencing

1. keep `reports/Reports-Module.md` as the stable report governance contract
2. keep `reports/active/` as the small active registry for still-governing outputs
3. keep `reports/snapshots/` as an explicit non-default lookup surface
4. archive superseded or stale report instances rather than expanding active context
