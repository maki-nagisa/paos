# Migration Runbook

This runbook describes the bounded Git migration model for `PAOS`.

## Steps

1. create a pre-migration backup under `E:\codex\paos-backups`
2. audit portable files, local configuration, and sensitive content
3. create `config/machine.example.yaml`
4. keep `config/machine.local.yaml` ignored
5. initialize or reuse the Git repository rooted at `E:\codex\paos`
6. stage only portable `PAOS` files
7. create a private GitHub repository
8. push and verify remote visibility
9. validate a fresh clone in a disposable directory

## Non-Goals

- no force push
- no history rewrite during normal setup
- no repository root outside `E:\codex\paos`
- no secret upload
