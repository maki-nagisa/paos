# Automation Acceptance

## Purpose
- Define how a `PAOS` automation is checked before it can be treated as reusable knowledge.
- Keep correctness anchored to explicit acceptance rather than inferred from one successful run.

## Dependencies
- `knowledge/workflows/Workflow-Automation.md`
- `knowledge/workflows/Automation-Lifecycle.md`
- `templates/reports/report-template.md`

## Acceptance Model

Every automation must have an explicit acceptance rule before it can become `stable`.

Acceptance covers four dimensions:

| Dimension | Question |
| --- | --- |
| `contract` | is the automation objective, trigger, and boundary explicit? |
| `state` | are required state inputs and outputs named correctly? |
| `behavior` | does the automation behave as intended under its bounded scenario? |
| `verification` | is there a repeatable way to confirm success or failure? |

## Required Acceptance Checks

Before an automation contract becomes `stable`, it must satisfy all of the following:

1. its owner file is registered in the relevant manifest
2. its trigger, inputs, outputs, and failure policy are explicit
3. its dependency on `state`, `knowledge`, `reports`, or `archive` does not violate architecture rules
4. at least one bounded validation path is defined
5. the validation result can be summarized without replaying the full execution history

## Automation Check Sequence

Recommended validation order:

1. architecture check: confirm module placement and references
2. contract check: confirm the automation unit fields are complete
3. bounded run check: confirm the intended flow on a scoped scenario
4. output check: confirm expected state or report outputs exist
5. regression check: confirm the automation does not invalidate an already stable contract

## Stable Rule Protection

If an upstream section is marked `Stable`, later automation chapters must not weaken it during acceptance work.

Protection rules:
- acceptance may verify a stable section
- acceptance may not silently reinterpret a stable section
- any required change to a stable section must be made in the owning canonical file first

## Acceptance Evidence Rule

Acceptance evidence should be compressed into a bounded report or audit surface.

Evidence rules:
- keep only the minimum evidence needed to prove acceptance
- prefer structured summaries over raw logs
- store long traces outside default context and reference them only when necessary
- once acceptance is summarized, treat the summary as the reusable surface

## Stable Sections

The following sections are now treated as `Stable` for the current architecture phase:
- `Acceptance Model`
- `Required Acceptance Checks`
- `Automation Check Sequence`
- `Stable Rule Protection`
- `Acceptance Evidence Rule`

Current status for this file: `Stable`
