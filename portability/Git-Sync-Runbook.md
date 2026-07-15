# Git Sync Runbook

Use this runbook for routine single-user multi-device sync.

## Rules

1. pull before editing
2. only one device writes current state at a time
3. commit bounded changes with review evidence
4. push when the task state is coherent
5. switch devices only after releasing the writer state

## PowerShell Commands

```powershell
$ErrorActionPreference = 'Stop'
git pull --ff-only
git status
git add .
git commit -m "Update PAOS state"
git push
```
