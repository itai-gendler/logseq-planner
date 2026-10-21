---
appliesTo:
- type: entity
  id: node
  facts:
  - Tags
- type: entity
  id: planner-state
  facts:
  - Selected tags
  - Date mappings
references:
- kind: code
  role: implementation
  target: src/core/normalize.ts#viewTagOf
- kind: spec
  role: intent
  target: REQUIREMENTS.md
---

# Each node belongs to its first matching selected tag

The node union contains each graph item once. Direct tags and included descendants match in selection order; the first match supplies its date mappings, Tag filter membership and Tag grouping.
