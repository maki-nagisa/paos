# PAOS Codex C Drive Growth - Read-Only Analysis Report

## 1. Executive Summary

- This first-pass task completed as a read-only analysis with no delete, move, cleanup, or configuration change.
- The strongest Codex-related `C:` growth surface is `C:\Users\Administrator\.codex` at approximately `4.73 GB`.
- The main ongoing growth contributors inside `.codex` are `backup/logs_2.sqlite`, `logs_2.sqlite`, `sessions/`, and `tmp/`.
- The installation tree under `C:\Users\Administrator\AppData\Local\OpenAI\Codex` is materially smaller at approximately `696 MB`; it is not the primary driver of daily growth.
- `C:\Users\Administrator\AppData\Local\Temp` is larger overall at approximately `13.34 GB`, but it contains mixed-system content and only some Codex-related entries, so it is a secondary rather than primary Codex-specific conclusion.

## 2. Task Definition

- Task goal: inspect whether daily Codex operation is causing `C:` usage growth, identify the most plausible path-level sources, and provide evidence-backed next-step recommendations.
- Owning module: `reports`.
- Source modules: `state`, `reports`.
- Risk posture: read-only only.

## 3. Scope and Constraints

- Allowed: path existence checks, directory sizing, recent-write inspection, large-file inspection, and bounded report/state write-back.
- Prohibited: delete, move, archive, cleanup, migration, config edit, service restart, process restart, registry change, task-scheduler change, or speculative repair.

## 4. Evidence Summary

### 4.1 Top examined Codex-related storage surfaces

| Path | Approx Size | Interpretation |
| --- | --- | --- |
| `C:\Users\Administrator\.codex` | `4.73 GB` | primary Codex-specific storage surface and strongest growth candidate |
| `C:\Users\Administrator\AppData\Local\OpenAI\Codex` | `696 MB` | installation/runtime payload, not the primary daily growth source |
| `C:\Users\Administrator\AppData\Roaming\Codex` | `325 MB` | secondary web/runtime state surface |
| `C:\Users\Administrator\AppData\Local\Temp` | `13.34 GB` | very large overall, but mixed-system temp, only partially Codex-related |

### 4.2 Breakdown inside `C:\Users\Administrator\.codex`

| Path | Approx Size | Notes |
| --- | --- | --- |
| `backup` | `1.28 GB` | dominated by `backup/logs_2.sqlite` |
| `sessions` | `1.21 GB` | ongoing rollout/session capture history |
| `logs_2.sqlite` | `505 MB` | active operational database/log surface |
| `tmp` | `471 MB` | includes large one-off patch artifacts |
| `plugins` | `464 MB` | plugin/runtime payload, some recent writes |
| `.sandbox-bin` | `344 MB` | bundled executable/runtime support |
| `.tmp` | `191 MB` | bundled marketplace/plugin staging residue |
| `generated_images` | `152 MB` | bounded but not currently growing in the last 7 days |

### 4.3 Strongest recent-growth signals in the last 7 days

| Path | Recent Bytes | Signal |
| --- | --- | --- |
| `C:\Users\Administrator\.codex\backup` | `1.28 GB` | strongest recent Codex-local growth; entirely explained by backup copy of `logs_2.sqlite` |
| `C:\Users\Administrator\.codex\logs_2.sqlite` | `505 MB` | active database/log file still growing |
| `C:\Users\Administrator\.codex\plugins` | `404 MB` | many recent file writes, likely plugin/runtime refresh activity |
| `C:\Users\Administrator\.codex\sessions` | `314 MB` | recent session history growth consistent with daily use |
| `C:\Users\Administrator\.codex\tmp` | `306 MB` | recent temp/staging growth, partly from patch-related artifacts |
| `C:\Users\Administrator\.codex\archived_sessions` | `33 MB` | smaller but active archival accumulation |

### 4.4 Evidence of session-history accumulation

- `C:\Users\Administrator\.codex\sessions\2026` is approximately `1.15 GB`.
- July daily subfolders show continued accumulation across active dates, including larger daily buckets such as:
  - `07\02` about `491.80 MB`
  - `07\01` about `221.37 MB`
  - `07\13` about `50.18 MB`
  - `07\14` about `21.48 MB`
  - `07\15` about `28.46 MB`

Interpretation:

- Session storage is a real ongoing growth source that scales with usage volume.
- It appears structurally normal rather than corrupted, but it materially contributes to daily `C:` growth.

### 4.5 Evidence of large operational database growth

- `C:\Users\Administrator\.codex\logs_2.sqlite` is approximately `505 MB` and was written today.
- `C:\Users\Administrator\.codex\backup\logs_2.sqlite` is approximately `1.22 GB` and was written recently.
- `logs_2.sqlite-wal` is active at about `5.65 MB`.

Interpretation:

- Operational logging/database state is one of the strongest Codex-local storage consumers.
- The backup copy is larger than the live file and likely reflects retained historical state rather than current runtime necessity, but this round does not modify it.

### 4.6 Evidence of temp/staging residue

Inside `C:\Users\Administrator\.codex\tmp`:

- `app-patched.asar` about `152.16 MB`
- `asar-extract-002` about `151.89 MB`
- `app.asar.backup-20260710-145845` about `142.63 MB`

Interpretation:

- These are consistent with one-off patch/extract activity rather than ordinary daily conversational growth.
- They are large enough to matter, but they look more like residue from earlier intervention work than the primary steady-state daily growth mechanism.

### 4.7 Installation tree and roaming state

- `C:\Users\Administrator\AppData\Local\OpenAI\Codex\bin` is about `390 MB`.
- `C:\Users\Administrator\AppData\Local\OpenAI\Codex\runtimes` is about `274 MB`.
- `C:\Users\Administrator\AppData\Roaming\Codex\web` is about `310 MB`.

Interpretation:

- These paths are substantial, but they do not explain the majority of current Codex-related `C:` usage.
- They look more like installed/runtime footprint than the main daily incremental growth source.

### 4.8 `Temp` observations with Codex-related traces

- Global `C:\Users\Administrator\AppData\Local\Temp` is extremely large overall.
- Recent large files include both unrelated package artifacts and clearly Codex-related temp objects such as `codex-review-objects-*` directories.

Interpretation:

- `Temp` may contribute some incremental Codex growth during review/object processing.
- However, this round cannot attribute the bulk of `Temp` growth to Codex alone.

## 5. Findings

### Informational

- The main Codex-specific `C:` footprint is under `C:\Users\Administrator\.codex`, not the installed app directory.
- Session history and operational SQLite storage are normal-looking but materially large.
- Some large temp artifacts look like historical intervention residue rather than normal daily growth.

### Maintenance Finding

- `C:\Users\Administrator\.codex\tmp` contains large patch/extract artifacts whose naming suggests earlier manual repair work.
- This is worth follow-up if disk pressure matters, but it is not by itself evidence of a runtime defect.

## 6. Current Conclusion

- Most likely steady-state Codex daily growth drivers:
  1. `C:\Users\Administrator\.codex\sessions`
  2. `C:\Users\Administrator\.codex\logs_2.sqlite` and related SQLite state
  3. `C:\Users\Administrator\.codex\backup\logs_2.sqlite`
- Likely non-steady-state but still significant residue:
  1. `C:\Users\Administrator\.codex\tmp\app-patched.asar`
  2. `C:\Users\Administrator\.codex\tmp\asar-extract-002`
  3. `C:\Users\Administrator\.codex\tmp\app.asar.backup-20260710-145845`
- Installation footprint exists but is not the main explanation for the current growth pattern.

## 7. Limits

- This round did not compare with historical filesystem snapshots, so it identifies plausible growth surfaces from current size and recent-write evidence rather than exact day-over-day deltas.
- This round did not inspect process-level open handles or SQLite schema semantics.
- This round did not delete or consolidate anything, so all conclusions remain observational.

## 8. Recommended Next Steps

1. Run a second read-focused pass on `C:\Users\Administrator\.codex\logs_2.sqlite`, `backup\logs_2.sqlite`, and `sessions\2026\07` to quantify table/file composition and growth cadence.
2. Separate steady-state growth from cleanup candidates by classifying `.codex\tmp` and `.codex\backup` contents into runtime-required versus historical residue.
3. If the user wants remediation after review, design a narrowly scoped non-destructive cleanup plan for historical residue first, before touching live session or SQLite state.
4. If exact attribution is required, capture a 24-hour or 72-hour size baseline for `.codex`, `Temp`, and the largest subpaths.

## 9. Verdict

- First-round read-only analysis: complete.
- Strongest evidence-backed answer: Codex-related `C:` growth is primarily driven by `.codex` session/log/backup storage, with additional but more episodic contribution from temp patch/staging residue.
