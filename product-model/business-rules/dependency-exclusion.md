---
appliesTo:
- type: entity
  id: task
  facts:
  - References
- type: entity
  id: node
  facts:
  - References
  - Progress
references:
- kind: code
  role: implementation
  target: src/core/normalize.ts#buildTasks
- kind: code
  role: implementation
  target: src/core/layout-common.ts#viewItems
- kind: spec
  role: intent
  target: REQUIREMENTS.md
---

# A dependent is not a linked task of its dependency

Only the chosen dependency-property values on the task itself exclude references. Other references still link it. None restores ordinary reference linking. A task selected as a node is not repeated as another node’s task row, while ordinary rollups still count it.
