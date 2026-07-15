# Templates Reports

## Purpose
- Define the template surface for bounded `PAOS` reports.

## Scope
- Register the template rules for bounded reports, audits, and summary outputs in `PAOS`.
- Keep reports compact and decision-grade rather than process-heavy.
- Do not turn report templates into filled report archives.

## Dependencies
- `templates/Templates-Module.md`
- `templates/reports/report-template.md`

## Inputs
- Report structure rules
- Required report metadata

## Outputs
- Report template registry
- Report creation anchor

## References
- `templates/reports/report-template.md`
- `reports/Reports-Module.md`
- `reports/indexes/reports.index.md`

## Report Template Role

Report templates exist to keep bounded outputs structurally comparable and cheap to scan.
They solve the recurring problem of reports expanding into inconsistent narrative shapes that are harder for both humans and AI to load.

## Registry Rule

- use `report-template.md` when creating any bounded report artifact intended to summarize current state, decisions, risks, or next actions
- keep report templates aligned with `reports/Reports-Module.md` instead of inventing parallel report semantics
- do not add sections here unless they materially improve recurring report readability or auditability

## Canonical Template

- `templates/reports/report-template.md`
