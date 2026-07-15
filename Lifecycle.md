# Lifecycle

This file defines the lifecycle states used by the `PAOS` bootstrap layer and modules.

## Lifecycle Flow

```text
Planning
  -> Executing
  -> Review
  -> Stable
  -> Maintenance
  -> Archive
```

## State Meanings

- `Planning`: the work is defined but not yet being applied to canonical surfaces
- `Executing`: the work is actively changing the owned surfaces
- `Review`: the work is under consistency, reference, and rule validation
- `Stable`: the contract is accepted as canonical and should not drift casually
- `Maintenance`: the contract remains stable and only incremental corrections or approved updates should occur
- `Archive`: the material is inactive, replaced, or no longer part of default context

## Usage Rules

- bootstrap-layer files may use lifecycle state to describe current operating posture
- module work should move through lifecycle states intentionally rather than implicitly
- `stable` is not the end of work; stable content may enter `maintenance`
- archived material must not return to default load without explicit need

## State Control Rule

- use lifecycle state to decide whether to create, update, review, maintain, or retire a surface
- keep the lifecycle small and explicit so Codex does not need to infer module posture from scattered prose
