# Backup Strategy

`PAOS` backup stays file-based and local-first.

## Primary Backup

- root: `E:\codex\paos-backups`
- format: `paos-pre-git-YYYYMMDD-HHMMSS`
- method: file copy preserving data and timestamps
- manifest: `BACKUP-MANIFEST.md`

## Recovery Rule

Before restoring, compare the backup against the current working tree so later valid edits are not overwritten by mistake.

## Recovery Command

```powershell
$ErrorActionPreference = 'Stop'
robocopy 'E:\codex\paos-backups\<backup-folder>' 'E:\codex\paos' /E /COPY:DAT /DCOPY:T /R:1 /W:1 /XJ
```
