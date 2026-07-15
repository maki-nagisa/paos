# Device Offboarding

Use this runbook before retiring or pausing a device that has worked on `PAOS`.

## Required Steps

1. finish or explicitly hand off the current task
2. commit and push all approved `PAOS` changes
3. release `state/current/Active-Writer.yaml` back to `idle`
4. keep `config/machine.local.yaml` local to the device
5. remove any copied secrets or credentials that were installed outside Git

## PowerShell Commands

```powershell
$ErrorActionPreference = 'Stop'
git status
git add .
git commit -m "Hand off PAOS device state"
git push
```

After push, set the active writer state to `idle` or assign it to the next device before new edits start elsewhere.
