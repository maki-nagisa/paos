# Templates Modules

## Purpose
- Define the template surface for canonical `PAOS` module documents.

## Scope
- Register the template rules for canonical module-level documents inside the fixed `PAOS` module map.
- Keep architecture-facing files structurally aligned without repeating full architecture rules.
- Do not store filled module content examples as if they were templates.

## Dependencies
- `templates/Templates-Module.md`
- `templates/modules/module-template.md`

## Inputs
- Module header rules
- Canonical module structure rules

## Outputs
- Module template registry
- Module creation anchor

## References
- `templates/modules/module-template.md`
- `core/conventions/naming.md`
- `core/conventions/references.md`

## Module Template Role

Module templates exist to keep canonical module files structurally comparable.
They solve the recurring problem of every chapter inventing a slightly different shape for purpose, scope, dependencies, outputs, and update policy.

## Registry Rule

- use `module-template.md` when creating or normalizing any canonical module contract
- keep global rules in `core` and module-specific structure here; do not duplicate the same rule blocks across generated files
- expand this registry only when a recurring module-structure need appears across more than one stable file

## Canonical Template

- `templates/modules/module-template.md`
