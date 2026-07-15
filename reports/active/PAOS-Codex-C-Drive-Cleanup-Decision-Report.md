# PAOS Codex C Drive Cleanup Decision Report

## 1. Executive Summary

- This is the final evidence round for the current Codex `C:` growth investigation.
- The target system remained read-only throughout the analysis rounds.
- `PAOS` control-plane files were updated as expected for task tracking and report write-back.
- An actionable cleanup decision can now be made without further broad evidence gathering.

## 2. Scope Clarification

### Target-System Read-Only

The following surfaces were treated as read-only in this and the previous analysis round:

- `C:\Users\Administrator\.codex\*`
- `C:\Users\Administrator\AppData\Local\OpenAI\Codex\*`
- `C:\Users\Administrator\AppData\Roaming\Codex\*`
- `C:\Users\Administrator\AppData\Local\Temp\*`

No delete, move, cleanup, archive, config, or process action was performed against those target-system paths.

### PAOS Control-Plane Write-Back

The following write-back actions did occur and are intentional:

- `PAOS` report creation/update
- `Current-Task.md` task-state updates
- `Reports-Active.md` and `reports.index.md` registry updates
- `progress.md` continuity updates

This task should therefore be described as:

- target-system read-only
- `PAOS` control-plane write-back enabled

## 3. Decision Goal

- Convert the prior evidence into a concrete cleanup sequence.
- Avoid continued analysis drift.
- Separate immediate low-risk cleanup targets from live-runtime surfaces and policy-sensitive data.

## 4. Key Evidence Used

| Path | Approx Size | Last Write | Decision Signal |
| --- | --- | --- | --- |
| `C:\Users\Administrator\.codex\tmp\app-patched.asar` | `152.16 MB` | `2026-07-10` | likely patch residue |
| `C:\Users\Administrator\.codex\tmp\asar-extract-002` | `151.89 MB` | `2026-07-10` | likely patch residue |
| `C:\Users\Administrator\.codex\tmp\app.asar.backup-20260710-145845` | `142.63 MB` | `2026-06-11` | likely historical backup residue |
| `C:\Users\Administrator\.codex\backup\logs_2.sqlite` | `1224.95 MB` | `2026-07-13` | very large, but policy-sensitive backup/log retention surface |
| `C:\Users\Administrator\.codex\logs_2.sqlite` | `482.58 MB` | today | live operational database |
| `C:\Users\Administrator\.codex\sessions\2026\07` | `1106.11 MB` | today | active session history growth |
| `C:\Users\Administrator\.codex\archived_sessions` | `41.43 MB` | today | intentional archived history |
| `C:\Users\Administrator\.codex\plugins` | `442.31 MB` | `2026-07-13` | installed/runtime payload, not a cleanup-first target |
| `C:\Users\Administrator\.codex\.tmp` | `182.16 MB` | `2026-07-10` | staging residue candidate, but lower priority than `tmp` top three |

## 5. Cleanup Decision

### Decision Class A - Clean First

These are the best first-wave cleanup candidates.

| Path | Why It Is In Scope | Estimated Recovery | Risk |
| --- | --- | --- | --- |
| `C:\Users\Administrator\.codex\tmp\app-patched.asar` | patch artifact, not current live database or session history | `152.16 MB` | low |
| `C:\Users\Administrator\.codex\tmp\asar-extract-002` | extracted patch workspace residue | `151.89 MB` | low |
| `C:\Users\Administrator\.codex\tmp\app.asar.backup-20260710-145845` | old backup artifact with timestamped name | `142.63 MB` | low |

Decision:

- These three targets should be the first cleanup wave.
- Combined expected recovery is approximately `446.68 MB`.
- They are the clearest non-runtime residues identified so far.

### Decision Class B - Clean Second After Narrow Confirmation

These are meaningful candidates, but they should not be deleted in the same blind pass as Class A.

| Path | Why Deferred | Estimated Recovery | Risk |
| --- | --- | --- | --- |
| `C:\Users\Administrator\.codex\backup\logs_2.sqlite` | large and likely redundant backup, but still a named backup/log surface | `1224.95 MB` | medium |
| `C:\Users\Administrator\.codex\.tmp` | staging residue is plausible, but content class is less explicit than the three named `tmp` artifacts | `182.16 MB` | medium-low |

Decision:

- `backup\logs_2.sqlite` should be treated as the highest-value second-wave candidate if disk pressure remains after Class A cleanup.
- Before acting on it, confirm whether this backup is intentionally retained for rollback/forensics or is merely leftover residue.
- `.tmp` can be considered after the named `tmp` artifacts, but it should be pruned selectively or with a clearly bounded rule.

### Decision Class C - Do Not Clean In The First Remediation Pass

These should be preserved in the first cleanup decision.

| Path | Why Not A First-Pass Cleanup Target |
| --- | --- |
| `C:\Users\Administrator\.codex\logs_2.sqlite` | live operational database with current writes |
| `C:\Users\Administrator\.codex\sessions\2026\07` | current session history, still actively growing |
| `C:\Users\Administrator\.codex\archived_sessions` | intentionally retained archived conversation state |
| `C:\Users\Administrator\.codex\plugins` | installed/runtime payload |
| `C:\Users\Administrator\AppData\Local\OpenAI\Codex` | installation/runtime tree, not main daily growth source |

Decision:

- These paths are non-targets for the first cleanup pass.
- They may require retention-policy changes, product behavior changes, or migration strategy later, but not ad hoc deletion.

## 6. Recommended Execution Order

1. Remove the three explicit `.codex\tmp` ASAR patch/extract residues.
2. Re-measure `C:\Users\Administrator\.codex` and free space on `C:`.
3. If pressure remains meaningful, evaluate `backup\logs_2.sqlite` as the second-wave candidate.
4. Only after that, consider bounded cleanup of `.codex\.tmp` if it still materially contributes.
5. Keep live `logs_2.sqlite` and `sessions` untouched in the near-term remediation pass.

## 7. Practical Decision

The next remediation task should be:

- a narrowly scoped cleanup task
- limited to the three explicit `.codex\tmp` artifacts listed in Decision Class A
- with post-cleanup measurement and no broader deletion in the same turn

If the user wants a single conservative action set, this is the best current answer.

## 8. Non-Goals

- no cleanup of active session history in this pass
- no cleanup of live SQLite state in this pass
- no config or retention-policy redesign in this pass
- no broader `Temp` cleanup based on mixed-system evidence

## 9. Verdict

- Further open-ended analysis is not needed for the first cleanup decision.
- The first actionable cleanup wave should target the three explicit `.codex\tmp` ASAR patch/extract residues.
- `backup\logs_2.sqlite` is the strongest second-wave candidate if more recovery is needed after the first pass.
