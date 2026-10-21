---
appliesTo:
- type: entity
  id: node
  facts:
  - Progress
- type: entity
  id: task
  facts:
  - Status
references:
- kind: code
  role: implementation
  target: src/core/nodes.ts#rollup
- kind: code
  role: implementation
  target: src/core/layout-common.ts#nestItems
- kind: spec
  role: intent
  target: REQUIREMENTS.md
---

# Progress excludes canceled linked work from its denominator

Progress is done divided by all minus canceled. Unknown or absent task status is open. Nested Timeline and Agenda parents add their child nodes and their linked tasks that are not themselves selected nodes, each block once; canceled children also leave the denominator.
