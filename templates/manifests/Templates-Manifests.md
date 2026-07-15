# Templates Manifests

## Purpose
- Define the template surface for all `PAOS` manifest artifacts.

## Scope
- Register the template rules for module manifests and registry manifests used by `PAOS`.
- Keep manifest generation compact, machine-readable, and structurally consistent.
- Do not become a second manifest schema specification or a history of past manifest variants.

## Dependencies
- `templates/Templates-Module.md`
- `templates/manifests/manifest-template.md`

## Inputs
- Manifest structure rules
- Required manifest metadata

## Outputs
- Manifest template registry
- Manifest creation anchor

## References
- `templates/manifests/manifest-template.md`
- `core/manifest/manifest.schema.md`
- `core/manifest/manifest.root.json`

## Manifest Template Role

Manifest templates exist to keep machine-readable registration surfaces consistent.
They solve the recurring problem of modules drifting in field shape, naming, and load metadata.

## Registry Rule

- use `manifest-template.md` when creating or normalizing any manifest-like `PAOS` file
- keep the manifest template smaller than the manifests it governs
- add fields here only when they materially improve module registration or loading behavior

## Canonical Template

- `templates/manifests/manifest-template.md`
