# Manifest Schema Design

## Root Manifest

Required fields:
- `systemId`
- `systemName`
- `version`
- `defaultEntry`
- `loadOrder`
- `modules`
- `referenceRules`
- `namingRules`
- `statusPolicy`
- `archivePolicy`

## Module Manifest

Required fields:
- `moduleId`
- `title`
- `purpose`
- `scope`
- `dependsOn`
- `defaultLoad`
- `status`

Optional fields:
- `inputs`
- `outputs`
- `freshnessRule`
- `canonicalFiles`
- `replacementOf`

## Report Manifest

Required fields:
- `reportId`
- `reportType`
- `title`
- `scope`
- `sourceModules`
- `generatedFrom`
- `freshness`
- `status`

## Archive Manifest

Required fields:
- `archiveId`
- `sourcePath`
- `replacementPath`
- `reason`
- `archivedAt`

Design rules:
- schema is descriptive and compact
- field names stay stable across modules
- manifests describe current structured truth only
