# Git Recovery Runbook

Use this runbook when sync or device handoff fails.

## Safe Recovery Order

1. inspect `git status`
2. inspect `git remote -v`
3. inspect `git log --oneline -5`
4. inspect `state/current/Active-Writer.yaml`
5. inspect the latest backup manifest
6. restore from backup only after diffing the current tree against the backup

## PowerShell Checks

```powershell
$ErrorActionPreference = 'Stop'
git status
git remote -v
git log --oneline -5
Get-Content '.\state\current\Active-Writer.yaml' -Encoding UTF8
```

## Escalation Boundary

Do not use `git push --force`, `git reset --hard`, or destructive cleanup as a first recovery action.
