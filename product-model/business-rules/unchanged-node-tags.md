---
appliesTo:
- type: entity
  id: node
  effect: changes
  facts:
  - Tags
references:
- kind: code
  role: implementation
  target: src/core/kanban.ts#moveDescriptor
- kind: spec
  role: intent
  target: REQUIREMENTS.md
permits: []
---

# Planning moves never change a node’s tags

Tag swimlanes identify existing membership. A move across Tag lanes is refused, and column moves within that lane retain the tag.
