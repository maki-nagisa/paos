# Dependency Rules

Allowed direction:

```text
core -> state
core -> templates
core -> roadmap
state -> knowledge
knowledge -> reports
templates -> reports
any -> archive (retire only)
```

Constraints:
- `core` is the highest-authority layer
- `state` holds current truth and must stay lighter than `knowledge`
- `knowledge` stores stable reusable modules, not session residue
- `reports` are outputs, not system foundations
- `archive` is never a default input layer
