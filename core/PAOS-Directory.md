# PAOS Directory

## Purpose

Define the canonical directory structure for `Personal AI Operating System (PAOS)`.
This file is the structural reference for folder layout, entry files, and module placement.

## Canonical Tree

```text
paos/
  README.md
  core/
    PAOS-Architecture.md
    PAOS-Directory.md
    Core-Module.md
    ontology/
      terms.md
    conventions/
      naming.md
      references.md
      dependency-rules.md
    manifest/
      manifest.root.json
      manifest.schema.md
  state/
    State-Module.md
    state.index.md
    current/
      Status.md
      Current-Task.md
    decisions/
      Decision-Index.md
    active-projects/
      Active-Projects.md
    manifest.manifest.json
  knowledge/
    Knowledge-Module.md
    domains/
      Knowledge-Domains.md
    context/
      Knowledge-Context.md
      Context-Layers.md
      Context-Assembly.md
      Context-Rules.md
    memory/
      Knowledge-Memory.md
      Memory-Taxonomy.md
      Memory-Rules.md
      Memory-Retrieval.md
    storage/
      Knowledge-Storage.md
      Storage-Layers.md
      Storage-Rules.md
      Storage-Lifecycle.md
    systems/
      Knowledge-Systems.md
    workflows/
      Knowledge-Workflows.md
      Workflow-Automation.md
      Automation-Lifecycle.md
      Automation-Acceptance.md
    patterns/
      Knowledge-Patterns.md
    solutions/
      Knowledge-Solutions.md
    manifest.manifest.json
  templates/
    Templates-Module.md
    manifests/
      Templates-Manifests.md
      manifest-template.md
    modules/
      Templates-Modules.md
      module-template.md
    reports/
      Templates-Reports.md
      report-template.md
    roadmap/
      Templates-Roadmap.md
      roadmap-template.md
    manifest.manifest.json
  reports/
    Reports-Module.md
    indexes/
      reports.index.md
    active/
      Reports-Active.md
    snapshots/
      Reports-Snapshots.md
    manifest.manifest.json
  roadmap/
    Roadmap-Module.md
    roadmap.index.md
    horizons/
      Roadmap-Horizons.md
    initiatives/
      Roadmap-Initiatives.md
    manifest.manifest.json
  archive/
    Archive-Module.md
    knowledge/
      Archive-Knowledge.md
    reports/
      Archive-Reports.md
    roadmap/
      Archive-Roadmap.md
    manifest.manifest.json
```

## Placement Rules

- `core/` stores system rules, architecture, ontology, and machine-readable registry files.
- `state/` stores the current active truth that should be preferred over history.
- `knowledge/` stores durable reusable knowledge modules.
- `templates/` stores output contracts and generation skeletons.
- `reports/` stores bounded synthesized artifacts and snapshots.
- `roadmap/` stores future-facing structural evolution items.
- `archive/` stores inactive material that must stay out of default context.

## Entry Rules

- System architecture entry: `core/PAOS-Architecture.md`
- System directory entry: `core/PAOS-Directory.md`
- Machine entry: `core/manifest/manifest.root.json`
- Active state entry: `state/state.index.md`

## Change Control

- Top-level modules are fixed unless architecture approval explicitly changes them.
- New folders should be added inside an existing module before proposing a new module.
- New canonical files must be registered through the relevant manifest path.
