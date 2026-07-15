# Storage Rules

## Purpose
- Define the operating rules that keep PAOS storage coherent and maintainable.

## Dependencies
- `knowledge/storage/Knowledge-Storage.md`
- `knowledge/storage/Storage-Layers.md`

## Inputs
- Candidate files
- Canonical modules
- Existing manifests

## Outputs
- Consistent file placement
- Reduced duplication and storage drift

## References
- `core/PAOS-Directory.md`
- `knowledge/storage/Storage-Lifecycle.md`

## Placement Rules

- store by authority, not by where the file was first created
- keep one canonical file per durable contract, rule, or knowledge unit
- place files inside an existing approved module before proposing new structure
- register canonical files in the relevant manifest before treating them as active truth
- prefer narrow subfolders over broad dumping grounds

## Separation Rules

- separate current state from durable knowledge
- separate reusable knowledge from bounded reports
- separate active modules from historical retention
- separate templates from instances
- separate architecture rules from project-specific content

## Manifest Rules

- every canonical active file must be reachable from the relevant manifest
- module manifests should list entry files before detail files
- storage changes that alter canonical placement must update both structure docs and machine-readable manifests
- unregistered files may exist as drafts, but they are not canonical storage until registered

## Duplication Rules

- do not keep parallel copies of the same canonical content in multiple folders
- if a summary is needed, store a pointer to the canonical file instead of repeating the full text
- if historical comparison matters, move the replaced version to `archive` instead of co-locating active variants

## Low-Context Rules

- design folders so retrieval can stop early
- prefer small canonical files over long omnibus documents
- keep file names stable so references remain cheap
- avoid placing unrelated concepts into one file just because they were produced in one work cycle

## Storage Quality Gate

Before a file becomes canonical, confirm all of the following:
1. the file has one clear authority layer
2. the file reduces future reconstruction cost
3. the file does not duplicate an existing canonical file
4. the file has a stable name and placement
5. the file is registered in the correct manifest path
