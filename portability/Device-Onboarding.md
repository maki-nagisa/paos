# Device Onboarding

This runbook restores `PAOS` on a new Windows device from the private GitHub repository.

## Prerequisites

1. install Git
2. install GitHub CLI
3. install Codex
4. authenticate GitHub CLI

## PowerShell Commands

```powershell
$ErrorActionPreference = 'Stop'
gh auth login
New-Item -ItemType Directory -Force -Path 'D:\codex' | Out-Null
Set-Location 'D:\codex'
gh repo clone maki-nagisa/paos paos
Set-Location '.\paos'
Copy-Item '.\config\machine.example.yaml' '.\config\machine.local.yaml'
```

## Local Configuration

Edit `config/machine.local.yaml` and replace the example values with the new device paths.

Recommended keys:

- `workspace_root`
- `projects_root`
- `archive_root`
- `backup_root`
- `device.id`
- `device.role`

## First Bootstrap Check

1. read `README.md`
2. read `Bootstrap.md`
3. read `OperatingRules.md`
4. read `CurrentContext.md`
5. read `bootstrap/README.md`
6. verify `state/current/Status.md`
7. verify `state/current/Current-Task.md`
8. confirm `state/current/Active-Writer.yaml` is `idle` or explicitly assigned to this device before write work

## Start Work

```powershell
$ErrorActionPreference = 'Stop'
git pull --ff-only
git status
```

Begin in read-only mode unless this device has acquired the active writer role for the task.
