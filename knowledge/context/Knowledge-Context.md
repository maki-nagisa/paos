# Knowledge Context Module

## Purpose
- Define how PAOS assembles, constrains, and compresses context for AI-assisted work.
- Keep context loadable as small, authoritative modules instead of long conversational history.

## Scope
- Personal context architecture for `ChatGPT`, `Codex`, local workspace, and AI agents.
- Covers context sources, context layers, assembly order, and context control rules.
- Does not store raw chat transcripts, verbose execution logs, or duplicate knowledge already owned by another module.

## Inputs
- Active state from `state`
- Durable knowledge from `knowledge`
- Stable system rules from `core`
- Bounded reports only when the task requires them

## Outputs
- Canonical context model for PAOS
- Context assembly rules for future modules and agents
- Low-context loading guidance for long-term personal use

## Dependencies
- `core/PAOS-Architecture.md`
- `core/PAOS-Directory.md`
- `core/ontology/terms.md`
- `knowledge/Knowledge-Module.md`
- `knowledge/memory/Knowledge-Memory.md`
- `knowledge/storage/Knowledge-Storage.md`
- `state/state.index.md`

## Canonical Files
- `knowledge/context/Knowledge-Context.md`
- `knowledge/context/Context-Layers.md`
- `knowledge/context/Context-Assembly.md`
- `knowledge/context/Context-Rules.md`

## Update Rule
- Update only when context architecture, assembly order, or context control rules change.
- Task-specific prompt text or one-off operating notes should stay in `state`, `reports`, or external working files unless they become reusable context knowledge.

## Context Role

Context in PAOS is not chat replay.
Context is the minimum authoritative bundle an AI needs to act correctly without re-reading history.

Context must satisfy all of the following:
- load current truth before historical trace
- prefer canonical modules over session residue
- remain small enough to reduce token cost and drift
- be composable from stable modules instead of monolithic documents

Context must not become a second memory system, a second archive, or a default dump for notes.

## Context Objective

The context objective is simple:
- load less, but load the right files
- preserve authority ordering
- keep future sessions resumable without replaying the full path

When context is correct, AI work starts from state and knowledge, not from transcript archaeology.
