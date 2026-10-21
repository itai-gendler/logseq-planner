---
appliesTo:
- type: entity
  id: node
  facts:
  - Choices
- type: entity
  id: planner-state
  facts:
  - Done values
- type: entity
  id: task
  facts:
  - Status
references:
- kind: code
  role: implementation
  target: src/core/nodes.ts#isDone
- kind: code
  role: implementation
  target: src/core/nodes.ts#isNodeDone
- kind: code
  role: implementation
  target: src/core/layout-common.ts#taskState
- kind: spec
  role: intent
  target: REQUIREMENTS.md
---

# Explicit Done when selections override node completion defaults

A node is done if any of its eligible choices is done. Without an override, built-in values use Done/Canceled flags and user values named Done, Completed, Canceled, Cancelled or Closed are done, ignoring case and surrounding spaces. An explicit empty list makes none of that property’s values done. Linked tasks use built-in Task Status flags independently of node overrides.
