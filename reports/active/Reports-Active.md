# Reports Active

## Purpose
- Register the currently useful report artifacts in active use.

## Scope
- Define which report artifacts remain active enough to justify default discoverability.
- Keep the active registry small, current, and decision-oriented.
- Do not become a second archive index or a complete inventory of every report ever produced.

## Dependencies
- `reports/Reports-Module.md`
- `reports/indexes/reports.index.md`

## Inputs
- Current active reports
- Current report freshness state

## Outputs
- Active report registry
- Report default-load filter

## References
- `reports/indexes/reports.index.md`
- `reports/snapshots/Reports-Snapshots.md`
- `archive/reports/Archive-Reports.md`

## Active Report Rule

Keep a report in the active registry only if at least one of the following remains true:
- it still expresses the current best bounded answer to an active question
- it provides a still-governing compliance or audit surface
- it materially reduces future context cost for ongoing architecture work

Remove a report from the active registry when a stronger replacement exists or when the question it answered is no longer active.

## Current Active Reports

| Report ID | Title | Report Type | Why Active |
| --- | --- | --- | --- |
| `paos.principle-compliance.matrix` | `PAOS Principle Compliance Matrix` | `audit-report` | current compact audit surface for the 10 governing principles |
| `paos.phase2.review.report` | `PAOS Phase 2 Review Report` | `audit-report` | current compact audit surface for root bootstrap-layer architecture, metadata, and consistency |
| `paos.core.refinement.report` | `PAOS Core Refinement Report` | `audit-report` | current compact audit surface for root core-contract reduction and manifest tightening |
| `paos.architecture.cleanup.report` | `PAOS Architecture Cleanup Report` | `audit-report` | current compact audit surface for architecture-document-only cleanup and out-of-scope findings |
| `paos.phase3b.runtime-authority.cleanup.report` | `PAOS Phase 3B Runtime Authority Cleanup Report` | `audit-report` | current compact audit surface for targeted runtime-chain and authority-boundary repairs inside `core` |
| `paos.codex-c-drive-growth.readonly-analysis` | `PAOS Codex C Drive Growth Read-Only Analysis Report` | `analysis-report` | current bounded evidence surface for first-pass Codex-related `C:` growth analysis and next-step recommendation |
| `paos.codex-c-drive-cleanup.decision` | `PAOS Codex C Drive Cleanup Decision Report` | `analysis-report` | current bounded decision surface for the first executable Codex-related `C:` cleanup wave |
| `paos.codex-c-drive-tmp-cleanup.execution` | `PAOS Codex C Drive Tmp Cleanup Execution Report` | `execution-report` | current bounded execution surface for the completed first-wave `.codex\tmp` residue cleanup |

## Registry Rule

- keep only current and still-governing active reports here
- point to the canonical report file rather than restating its conclusions in full
- move stale entries to archive-facing surfaces instead of letting the active list grow
